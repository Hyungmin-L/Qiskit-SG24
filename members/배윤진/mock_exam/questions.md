# Qiskit v2.X Developer Certification — Mock Exam (yoonjin)

Original practice questions for the IBM Certified Associate Developer — Quantum Computation
using Qiskit v2.X exam. Every "what does this print?" answer was fixed by running the code with
`qiskit` 2.5.2, `qiskit-aer` 0.17.2 and `qiskit-ibm-runtime` 0.49.0. Every conceptual answer quotes
the official IBM Quantum documentation.

Answers are hidden in `<details>` — try the question first.

## Topic coverage (target: 20 questions)

| # | Syllabus topic | Target | Done |
| - | --- | :-: | :-: |
| 1 | Perform quantum operations | 2 | 1 |
| 2 | Visualize circuits, measurements, and states | 2 | 1 |
| 3 | Create quantum circuits (basic / dynamic / parameterized / transpile) | 4 | 3 |
| 4 | Run quantum circuits | 2 | 1 |
| 5 | Use the Sampler primitive | 3 | 1 |
| 6 | Use the Estimator primitive | 2 | 1 |
| 7 | Retrieve and analyze results | 2 | 1 |
| 8 | Operate with OpenQASM (incl. Runtime REST API) | 3 | 1 |
| | **Total** | **20** | **10** |

---

### Q1. Perform quantum operations — Pauli products

What does the following code print?

```python
from qiskit.quantum_info import Pauli

print(Pauli("X").compose(Pauli("Y")), Pauli("X") @ Pauli("Y"))
```

A. `iZ iZ`
B. `-iZ -iZ`
C. `-iZ iZ`
D. `iZ -iZ`

<details>
<summary>Answer</summary>

**C**

`A.compose(B)` applies `A` first, then `B`, so its matrix is `B·A = Y·X = -iZ`.
For `Pauli`, the `@` operator is matrix multiplication in the written order, `X·Y = iZ`
(the same as `A.dot(B)`).

</details>

---

### Q2. Visualize quantum states — `Statevector.draw`

Which `output` value raises an error when passed to `Statevector.draw()`?

A. `"latex"`
B. `"city"`
C. `"bloch"`
D. `"mpl"`

<details>
<summary>Answer</summary>

**D**

`"mpl"` is an option for `QuantumCircuit.draw()`, not for `Statevector.draw()`. Running it gives:

```
ValueError: 'mpl' is not a valid option for drawing Statevector objects. Please choose from:
'text', 'latex', 'latex_source', 'qsphere', 'hinton', 'bloch', 'city' or 'paulivec'.
```

</details>

---

### Q3. Create quantum circuits — parameter ordering

```python
from qiskit import QuantumCircuit
from qiskit.circuit import Parameter

theta = Parameter("theta")
alpha = Parameter("alpha")

qc = QuantumCircuit(1)
qc.rx(theta, 0)
qc.ry(alpha, 0)

bound = qc.assign_parameters([0.1, 0.2])
```

Which angles end up in `bound`?

A. `rx(0.1)`, `ry(0.2)`
B. `rx(0.2)`, `ry(0.1)`
C. Both gates get `0.1`
D. `TypeError`: a list cannot be passed; a dict is required

<details>
<summary>Answer</summary>

**B**

A list is bound in the order of `qc.parameters`, which is sorted by name, not by the order the
parameters were added: `ParameterView([Parameter(alpha), Parameter(theta)])`. So `alpha = 0.1`
and `theta = 0.2`. Pass a dict (`{theta: 0.1, alpha: 0.2}`) to avoid this trap.

</details>

---

### Q4. Create quantum circuits — dynamic circuits

```python
from qiskit import QuantumCircuit, QuantumRegister, ClassicalRegister
from qiskit_aer import AerSimulator

qr = QuantumRegister(2)
cr = ClassicalRegister(2, "c")
qc = QuantumCircuit(qr, cr)

qc.x(0)
qc.measure(0, 0)
with qc.if_test((cr[0], 0)) as else_:
    qc.x(1)
with else_:
    qc.h(1)
    qc.h(1)
qc.measure(1, 1)

print(AerSimulator().run(qc, shots=100).result().get_counts())
```

What is printed?

A. `{'11': 100}`
B. `{'01': 100}`
C. `{'10': 100}`
D. `{'01': 50, '11': 50}`

<details>
<summary>Answer</summary>

**B**

Qubit 0 is flipped and measured, so `c[0] = 1`. The condition `c[0] == 0` is false, so the
`else` block runs: `H·H = I`, and qubit 1 stays `|0⟩`. Bit strings are little-endian
(`c[1] c[0]`), giving `'01'`.

</details>

---

### Q5. Create quantum circuits — transpiler optimization levels

```python
from qiskit import QuantumCircuit, transpile

qc = QuantumCircuit(2)
qc.h(0)
qc.h(0)
qc.cx(0, 1)
qc.cx(0, 1)
qc.x(1)

t = transpile(qc, basis_gates=["rz", "sx", "x", "cx"], optimization_level=1)
print(dict(t.count_ops()))
```

What is printed?

A. `{'rz': 4, 'sx': 2, 'cx': 2, 'x': 1}`
B. `{'cx': 2, 'x': 1}`
C. `{'x': 1}`
D. `{}`

<details>
<summary>Answer</summary>

**C**

At level 1 the adjacent self-inverse pairs `H·H` and `CX·CX` cancel, leaving only `x`.
Option A is what `optimization_level=0` produces: each `H` is only translated to `rz, sx, rz`.

</details>

---

### Q6. Run quantum circuits — execution modes

You need to run 50 independent circuits, all known in advance, with no classical processing
between them. You are on the Open Plan. Which execution mode should you use?

A. Session
B. Batch
C. Session, because only sessions keep the QPU reserved between jobs
D. None — the Open Plan only supports single jobs

<details>
<summary>Answer</summary>

**B**

From [Execution modes](https://quantum.cloud.ibm.com/docs/guides/execution-modes):

> Batch mode — A multi-job manager for efficiently running experiments comprising multi-job
> workloads. These workloads are made up of independently executable jobs that have no
> conditional relationship with each other.

> Open Plan users cannot submit session jobs.

And from [Choose the right execution mode](https://quantum.cloud.ibm.com/docs/guides/choose-execution-mode):

> Generally, use batch mode unless you have workloads that don't have all inputs ready at the outset.

</details>

---

### Q7. Use the Sampler primitive — reading results

```python
from qiskit import QuantumCircuit
from qiskit.primitives import StatevectorSampler

qc = QuantumCircuit(2, 2)
qc.h(0)
qc.cx(0, 1)
qc.measure([0, 1], [0, 1])

result = StatevectorSampler().run([qc], shots=100).result()
```

Which expression returns the counts dictionary?

A. `result.get_counts()`
B. `result[0].data.meas.get_counts()`
C. `result[0].data.c.get_counts()`
D. `result[0].get_counts()`

<details>
<summary>Answer</summary>

**C**

The `DataBin` fields are named after the circuit's classical registers. `QuantumCircuit(2, 2)`
creates a register named `c`, so `list(result[0].data.keys())` is `['c']`. The name `meas`
only exists when the circuit was measured with `measure_all()`.

</details>

---

### Q8. Use the Estimator primitive — PUB broadcasting

```python
import numpy as np
from qiskit import QuantumCircuit
from qiskit.circuit import Parameter
from qiskit.quantum_info import SparsePauliOp
from qiskit.primitives import StatevectorEstimator

th = Parameter("th")
qc = QuantumCircuit(1)
qc.ry(th, 0)

obs = [[SparsePauliOp("Z")], [SparsePauliOp("X")]]   # shape (2, 1)
vals = np.linspace(0, np.pi, 3)                      # 3 parameter sets

result = StatevectorEstimator().run([(qc, obs, vals)]).result()
print(result[0].data.evs.shape)
```

What is printed?

A. `(3,)`
B. `(2,)`
C. `(2, 3)`
D. `ValueError`: shapes `(2, 1)` and `(3,)` cannot be broadcast

<details>
<summary>Answer</summary>

**C**

The parameter values have shape `(3,)` and the observables `(2, 1)`. NumPy broadcasting gives
`(2, 3)`: one row per observable, one column per parameter set. The values are
`[[1, 0, -1], [0, 1, 0]]` (⟨Z⟩ = cos θ, ⟨X⟩ = sin θ for θ = 0, π/2, π).

</details>

---

### Q9. Retrieve and analyze results — retrieving a past job

You submitted a job yesterday and saved its ID in `job_id`. Which call retrieves it?

A. `QiskitRuntimeService().job(job_id)`
B. `QiskitRuntimeService().retrieve_job(job_id)`
C. `QiskitRuntimeService().get_job(job_id)`
D. `SamplerV2(backend).result(job_id)`

<details>
<summary>Answer</summary>

**A**

From [Save and retrieve jobs](https://quantum.cloud.ibm.com/docs/guides/save-jobs):
`retrieved_job = service.job(job_id)`.
`retrieve_job` and `get_job` do not exist on `QiskitRuntimeService` (checked with `hasattr`
on qiskit-ibm-runtime 0.49.0).

</details>

---

### Q10. Operate with OpenQASM — importing OpenQASM 3

```python
from qiskit import qasm3

prog = """
OPENQASM 3.0;
include "stdgates.inc";
qubit[3] q;
bit[2] c;
h q[0];
cx q[0], q[1];
c[0] = measure q[0];
c[1] = measure q[1];
"""
qc = qasm3.loads(prog)
print(qc.num_qubits, qc.num_clbits)
```

What is printed?

A. `2 2`
B. `3 2`
C. `3 3`
D. `SyntaxError`: OpenQASM 3 requires `creg`/`qreg`

<details>
<summary>Answer</summary>

**B**

`qubit[3] q;` declares three qubits even though `q[2]` is never used, and `bit[2] c;` declares two
bits. `qreg`/`creg` are OpenQASM 2 syntax; OpenQASM 3 uses `qubit[n]`/`bit[n]`. `qasm3.loads` needs the `qiskit_qasm3_import` package.

</details>
