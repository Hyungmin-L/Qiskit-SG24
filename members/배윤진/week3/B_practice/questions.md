# Week 3 — Section B: 기출 문제

> syllabus 토픽: **Create quantum circuits**
> Advocate가 만든 practice exam 4종에서 이 토픽에 해당하는 문항만 추린 것. 총 **33문항**.

출처별 문항 수: algovista 6, clausia 9, MarcoBarroca 12, Q-Bees 6

풀이 방법 — 정답은 접혀 있으니 **먼저 풀고** 펼칠 것. 틀린 문항은 번호를 아래 오답 목록에
적고, 이유를 한 줄로 남긴다. 문제 자체보다 그 한 줄이 시험 직전에 쓸모 있다.

---


### 1. [algovista #6](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

You want to dynamically append measurements to all qubits in your circuit. You have already declared a classical register and want the measurement outcomes to route directly into it without creating an additional, new classical register. Which routine fits this requirement precisely?

A. `qc.measure_all()`

B. `qc.measure_all(add_bits=False)`

C. `qc.measure_active()`

D. `qc.measure()`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [algovista #6](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 2. [algovista #7](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

When configuring a compilation strategy utilizing the modern pass management framework via `generate_preset_pass_manager`, which parameter option dictates the depth and heuristic computational effort spent optimizing target hardware layouts?

A. `optimization_level`

B. `routing_method`

C. `initial_layout`

D. `approximation_degree`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [algovista #7](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 3. [algovista #8](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

A user compiles a circuit for an IBM backend using `optimization_level=3`. What structural optimization will they notice regarding consecutive single-qubit gates?

A. All virtual Z gates are transformed into physical RZ microwave pulses.

B. Adjacent single-qubit gates are aggressively combined and parameterized into single target basis gates to minimize errors.

C. The transpiler wraps all operations into un-optimized opaque black-box structures.

D. Every CX gate is systematically replaced with an ECR gate regardless of backend specifications.

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [algovista #8](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 4. [algovista #9](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

Which code snippet correctly implements a parameterized hardware-level control flow loop inside a `QuantumCircuit` instance using standard Qiskit v2.x context-manager syntax?

A. 
```python
with qc.for_loop(range(3)) as i:
    qc.rx(i * theta, i)
```

B. 
```python
for i in range(3):
    qc.rx(i * theta, i)
```

C. 
```python
qc.add_loop(range(3), lambda i: qc.rx(i * theta, i))
```

D. 
```python
with qc.loop(3) as i:
    qc.rx(theta, i)
```

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [algovista #9](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 5. [algovista #21](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

What is the native gate configuration behavior when transpiling a circuit for a target backend that natively supports Cross-Resonance (`ECR`) instead of Controlled-NOT (`CX`)?

A. The transpiler will reject the circuit unless you manually replace all CX gates first.

B. Each CX gate is unrolled into an ECR gate combined with local single-qubit rotations.

C. The transpiler converts all operations into software-simulated swap networks.

D. The circuit is executed on the hardware using virtualized CX emulation layers.

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [algovista #21](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 6. [algovista #24](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

When using `generate_preset_pass_manager` to target a specific backend, what is the primary benefit of passing the real `backend` object instance instead of just providing a raw list of basis gates?

A. It enables the pass manager to optimize the circuit using real-time dynamic calibration metrics, gate error rates, and the physical coupling map of the device.

B. It automatically authenticates your runtime cloud session with the cloud infrastructure service.

C. It bypasses local compilation and uploads the raw Python code directly to the hardware.

D. It reduces the physical gate execution times on the quantum device.

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [algovista #24](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 7. [clausia #15](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Classical-control "if"*

Which fragment applies an X gate on qubit 0 *only* when classical bit `c0` equals 1?

a)

```python
with qc.if_test((c0, 1)):
    qc.x(0)
```

b)

```python
qc.x(0).c_if(c0, 1)
```

c)

```python
if c0 == 1:
    qc.x(0)
```

d)

```python
qc.if_else(c0 == 1, qc.x(0))
```

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #15](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 8. [clausia #16](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Creating a 3-parameter vector*

How do you create three independent symbolic parameters all named θ?

a) `theta = Parameter('theta', 3)`  
b) `theta = ParameterVector('theta', 3)`  
c) `theta = ParameterVector(3, 'theta')`  
d) `theta = ParameterExpression('theta', 3)`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [clausia #16](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 9. [clausia #17](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Binding a single value to a parameter*

Given `theta = Parameter('θ')` and a circuit `qc` containing `rx(theta, 0)`, which call returns a **new** circuit with θ = π/4?

a) `qc.assign_parameters({theta: np.pi/4}, inplace=False)`  
b) `qc.bind_parameters({theta: np.pi/4})`  
c) `qc.assign(theta, np.pi/4)`  
d) `theta.bind(qc, np.pi/4)`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #17](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 10. [clausia #18](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Repeating a block five times*

Which construct correctly repeats the enclosed operations five times in a dynamic circuit?

a)

```python
with qc.for_loop(range(5)):
    qc.cx(0, 1)
```

b)

```python
for _ in range(5):
    qc.cx(0, 1)
```

c)

```python
qc.repeat(5):
    qc.cx(0, 1)
```

d)

```python
qc.loop(5).cx(0, 1)
```

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #18](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 11. [clausia #19](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Quick high-level transpilation*

What single-line call compiles `qc` for a backend `backend` using the **highest built-in optimisation** level?

a) `transpile(qc, backend, optimization_level=3)`  
b) `qc.transpile(backend, 3)`  
c) `run_transpile(qc, backend, level='max')`  
d) `generate_preset_pass_manager(level=3).run(qc)`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #19](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 12. [clausia #20](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Preset pass manager creation*

Which function directly returns a pass manager equivalent to transpiler optimisation level 2 for a target backend?

a) `generate_preset_pass_manager(optimization_level=2, target=backend.target)`  
b) `PassManager.preset(backend, level=2)`  
c) `PresetPassManager(backend, 2)`  
d) `transpile(qc, backend, opt_level=2, return_passmanager=True)`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #20](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 13. [clausia #21](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Controlling qubit layout manually*

While building a circuit for a five-qubit device with coupling map `coupling`, which `transpile` argument lets you **fix physical qubit placement**?

a) `layout_method='trivial'`  
b) `initial_layout=[0,1,2,3,4]`  
c) `routing_method='sabre'`  
d) `backend_properties=coupling`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [clausia #21](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 14. [clausia #22](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Creating a dynamic while-loop*

Which snippet repeats the `foo` sub-circuit until the classical bit `flag` equals 1?

a)

```python
qc.while_loop((flag, 0), foo)
```

b)

```python
while flag == 0:
    qc.append(foo, qc.qubits)
```

c)

```python
with qc.while_loop((flag, 1)):
    qc.append(foo, qc.qubits)
```

d)

```python
qc.do_while(foo, until=(flag,1))
```

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #22](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 15. [clausia #23](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Gate fusion by optimisation*

After executing

```python
tqc = transpile(qc, backend, optimization_level=3)
```

you notice the depth is much smaller because consecutive single-qubit rotations were merged. Which **pass family** is mainly responsible?

a) **BasisTranslation** passes  
b) **CXCancellation** passes  
c) **Optimize1qGatesDecomposition** passes  
d) **CommutationAnalysis** passes

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [clausia #23](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 16. [MarcoBarroca #2](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which line changes a `ParameterVector` named `theta` from length 2 to length 6?

- **A.** `theta.extend(6)`
- **B.** `theta.adjust(6)`
- **C.** `theta.resize(6)`
- **D.** `theta.length = 6`

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [MarcoBarroca #2](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 17. [MarcoBarroca #7](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

In a `CircuitInstruction`, which object is the operation component?

- **A.** A backend options dictionary
- **B.** A `Gate` or `Instruction` applied to bits
- **C.** A `SamplerV2` primitive object
- **D.** A Runtime session identifier

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [MarcoBarroca #7](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 18. [MarcoBarroca #8](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which code fragment is valid and applies the `Unroll3qOrMore` transpiler pass to a circuit named `qc`?

- **A.** 

    ```python
    from qiskit.transpiler import PassManager
    from qiskit.transpiler.passes import Unroll3qOrMore
    qc = PassManager([Unroll3qOrMore()]).run(qc)
    ```
- **B.** `qc = qc.unroll3qOrMore()`
- **C.** `qc = Unroll3qOrMore().execute(qc)`
- **D.** `qc.apply_pass(Unroll3qOrMore())`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #8](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 19. [MarcoBarroca #12](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Given a pass manager with basis gates `['ecr', 'rz', 'sx', 'x']`, which panel is a plausible transpiled drawing of an H-CX circuit?

![Question figure](https://raw.githubusercontent.com/MarcoBarroca/qiskit-v2-mock-exam/main/assets/visuals/transpiled_panels.png)

- **A.** Panel A
- **B.** Panel B
- **C.** Panel C
- **D.** Panel D

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #12](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 20. [MarcoBarroca #16](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

**Select 2.**

Which fragments create a circuit with 5 qubits and 2 classical bits?

- [ ] **A.** `QuantumCircuit(QuantumRegister(5, 'q'), ClassicalRegister(2, 'c'))`
- [ ] **B.** `QuantumCircuit(2, 5)`
- [ ] **C.** `QuantumCircuit(QuantumRegister(5), QuantumRegister(2))`
- [ ] **D.** `QuantumCircuit(ClassicalRegister(2), QuantumRegister(5))`
- [ ] **E.** `QuantumCircuit(5, 2)`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #16](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 21. [MarcoBarroca #23](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which import path is correct for transpiler passes such as `SabreLayout` and `RemoveFinalReset`?

- **A.** `from qiskit.scheduler import SabreLayout, RemoveFinalReset`
- **B.** `from qiskit.transpiler.passes import SabreLayout, RemoveFinalReset`
- **C.** `from qiskit.circuit.library import SabreLayout, RemoveFinalReset`
- **D.** `from qiskit.providers.models import SabreLayout, RemoveFinalReset`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [MarcoBarroca #23](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 22. [MarcoBarroca #26](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A transpiler fence is needed between two groups of gates. Which circuit call expresses that boundary?

- **A.** `qc.section()`
- **B.** `qc.session()`
- **C.** `qc.barrier()`
- **D.** `qc.partition()`

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [MarcoBarroca #26](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 23. [MarcoBarroca #35](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

The circuit below is still symbolic. Which line returns a circuit with `angle` bound to a numeric value?

```python
from qiskit import QuantumCircuit
from qiskit.circuit import Parameter

angle = Parameter('angle')
qc = QuantumCircuit(1)
qc.rz(angle, 0)
```

- **A.** `bound = qc.parameters.assign({angle: 0.75})`
- **B.** `bound = qc.assign_parameters({angle: 0.75})`
- **C.** `bound = qc.set_parameters({angle: 0.75})`
- **D.** `bound = qc.update_parameters({angle: 0.75})`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [MarcoBarroca #35](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 24. [MarcoBarroca #46](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which code fragment completes the logic: measure qubit 1 into classical bit 1, apply X to qubit 2 if that bit is 1, then measure qubit 2 into classical bit 2?

- **A.** 

    ```python
    qc.measure(1, 1)
    if clbits[1] == 1:
        qc.x(2)
    qc.measure(2, 2)
    ```
- **B.** 

    ```python
    qc.measure(1, 2)
    with qc.if_test((clbits[2], 1)):
        qc.x(1)
    ```
- **C.** 

    ```python
    qc.measure(1, 1)
    with qc.if_test((clbits[1], 1)):
        qc.x(2)
    qc.measure(2, 2)
    ```
- **D.** 

    ```python
    with qc.if_test((clbits[1], 1)):
        qc.x(2)
    qc.measure(1, 1)
    qc.measure(2, 2)
    ```

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [MarcoBarroca #46](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 25. [MarcoBarroca #58](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A circuit must measure `q[0]` into `c[0]`, then apply `X` to `q[1]` only when that measured bit is 1. Which fragment uses Qiskit's dynamic-circuit API correctly?

```python
from qiskit import ClassicalRegister, QuantumCircuit, QuantumRegister

q = QuantumRegister(2, 'q')
c = ClassicalRegister(1, 'c')
```

- **A.** 

    ```python
    qc = QuantumCircuit(q, c)
    qc.h(q[0])
    with qc.if_test((c[0], 1)):
        qc.x(q[1])
    ```
- **B.** 

    ```python
    qc = QuantumCircuit(q, c)
    qc.h(q[0])
    qc.measure(q[0], c[0])
    if c[0] == 1:
        qc.x(q[1])
    ```
- **C.** 

    ```python
    qc = QuantumCircuit(q, c)
    qc.h(q[0])
    qc.measure(q[0], c[0])
    with qc.if_test((c[0], 1)):
        qc.x(q[1])
    ```
- **D.** 

    ```python
    qc = DynamicCircuit(q, c)
    qc.h(q[0])
    qc.measure(q[0], c[0])
    if qc.test((c[0], 1)):
        qc.x(q[1])
    ```

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [MarcoBarroca #58](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 26. [MarcoBarroca #62](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

**Select 2.**

In a circuit-control code review, which two names are actual `QuantumCircuit` control-flow builders?

- [ ] **A.** `QuantumCircuit.repeat_until(...)`
- [ ] **B.** `QuantumCircuit.replace(...)`
- [ ] **C.** `QuantumCircuit.branch(...)`
- [ ] **D.** `QuantumCircuit.while_loop(...)`
- [ ] **E.** `QuantumCircuit.for_loop(...)`

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #62](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 27. [MarcoBarroca #64](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

What does the final line print?

```python
from qiskit.circuit import ParameterVector

weights = ParameterVector('w', 5)
selected = weights[3]
print(weights.index(selected))
```

- **A.** `3`
- **B.** `w[3]`
- **C.** `4`
- **D.** `ParameterVectorElement(3)`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #64](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 28. [Q-Bees #1](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You use a circuit-library state preparation routine that outputs a specific n-qubit state $|ψ⟩$. How is this typically integrated into a larger circuit?

- A
You must manually copy all of its gates into your circuit definition

- B
You can append it as a subcircuit or instruction at the beginning of your main circuit

- C
You must convert it to OpenQASM text and paste it into your code

- D
It can only be used as a standalone circuit and not combined

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [Q-Bees #1](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 29. [Q-Bees #3](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You are building a variational algorithm with layers of parameterized Ry and CNOT gates. Which practice best leverages the circuit library and parameterization features?

- A
Transpile the circuit first and then try to introduce parameters into the transpiled output

- B
Manually code every Ry and CNOT gate for each layer in plain QuantumCircuit

- C
Use a TwoLocal or EfficientSU2-style template from the circuit library with symbolic parameters

- D
Avoid symbolic parameters and bake fixed angles into the circuit

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [Q-Bees #3](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 30. [Q-Bees #10](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You are optimizing a circuit for a specific hardware backend with limited connectivity. Which transpiler pass or configuration most directly addresses qubit routing to satisfy the coupling map?

- A
Increasing optimization_level in transpile to 3

- B
Using layout and routing passes, such as SetLayout and StochasticSwap, in a custom PassManager

- C
Changing the basis_gates to match the backend's native gate set

- D
Using RemoveBarriers to minimize unnecessary barriers

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [Q-Bees #10](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 31. [Q-Bees #15](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You have a QuantumCircuit with custom Gate and Instruction objects and want to run it on a real device that only supports a limited set of basis gates. What is the main role of the transpiler in this context?

- A
It only optimizes the visual layout of the circuit diagram

- B
It decomposes high-level and custom gates into the device's basis gates while respecting connectivity and constraints

- C
It automatically chooses the best quantum algorithm for you

- D
It replaces all two-qubit gates with single-qubit gates to reduce error

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [Q-Bees #15](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 32. [Q-Bees #17](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You are reviewing a transpiled circuit and see many inserted swap gates between certain qubits. What is the primary reason the transpiler added these swap gates?

- A
To change the measurement basis of the final measurements

- B
To increase the circuit depth for benchmarking purposes

- C
To satisfy the device’s coupling map by moving logical qubits so that two-qubit gates act only on connected qubit pairs

- D
To reduce the overall number of two-qubit gates by replacing them with swaps

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [Q-Bees #17](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 33. [Q-Bees #25](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

In a dynamic circuit, what is the best description of classical feedforward?

- A
A measurement result is used to decide later operations.

- B
A gate is automatically decomposed into single-qubit gates.

- C
The transpiler chooses the backend based on the measurement result.

- D
The circuit is converted to a density matrix.

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [Q-Bees #25](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---


---

## 오답 정리

| 문항 | 내가 고른 답 | 정답 | 왜 틀렸나 |
| --- | --- | --- | --- |
| | | | |

## 이 토픽에서 반복해서 틀리는 것

- [ ]
