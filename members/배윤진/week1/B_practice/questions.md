# Week 1 — Section B: 기출 문제

> syllabus 토픽: **Perform quantum operations**
> Advocate가 만든 practice exam 4종에서 이 토픽에 해당하는 문항만 추린 것. 총 **25문항**.

출처별 문항 수: algovista 3, clausia 8, MarcoBarroca 11, Q-Bees 3

풀이 방법 — 정답은 접혀 있으니 **먼저 풀고** 펼칠 것. 틀린 문항은 번호를 아래 오답 목록에
적고, 이유를 한 줄로 남긴다. 문제 자체보다 그 한 줄이 시험 직전에 쓸모 있다.

---


### 1. [algovista #1](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

Which two operations will result in a SparsePauliOp that represents exactly the operator $-iY$?

A. 
```python
from qiskit.quantum_info import Pauli
p = Pauli('X') @ Pauli('Z')
```

B. 
```python
from qiskit.quantum_info import SparsePauliOp
SparsePauliOp.from_list([("Y", -1j)])
```

C. 
```python
from qiskit.quantum_info import Pauli
p = Pauli('Z') @ Pauli('X')
```

D. 
```python
from qiskit import QuantumCircuit
from qiskit.quantum_info import Pauli
qc = QuantumCircuit(1)
qc.y(0)
Pauli(qc)
```

<details>
<summary>정답</summary>

**A,B**

해설은 출처 원문 참고: [algovista #1](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

- A: `@`는 그대로 곱함. $X \cdot Z = -i Y$.
- B: -1j를 곱한것.
- D: question: 이거 출력 뭐로 나오지?

</details>

---

### 2. [algovista #2](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

What is the correct representation of the operator created by the following line of code under Qiskit's little-endian ordering convention?

```python
from qiskit.quantum_info import SparsePauliOp
SparsePauliOp.from_sparse_list([("XYZ", (1, 3, 4), 2.0)], num_qubits=6)
```

A. `SparsePauliOp(['ZXIYII'], coeffs=[2.+0.j])`

B. `SparsePauliOp(['IZYIXI'], coeffs=[2.+0.j])`

C. `SparsePauliOp(['IXIYZE'], coeffs=[2.+0.j])`

D. `SparsePauliOp(['IIXYZI'], coeffs=[2.+0.j])`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [algovista #2](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

- qiskit 순서: 뒤에서부터 0

</details>

---

### 3. [algovista #3](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

Given the code block below, what is the exact analytical probability of observing the state $|1>$ upon running an ideal computational basis measurement?

```python
from qiskit import QuantumCircuit
import numpy as np

qc = QuantumCircuit(1)
qc.ry(np.pi / 3, 0)
qc.rz(np.pi / 2, 0)
```

A. 0.25

B. 0.75

C. 0.5

D. 0.125

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [algovista #3](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

$$ Rn^​(θ)=cos2θ​I−isin2θ​(n^⋅σ)$$

$$R_X(\theta) = \begin{pmatrix}\cos\frac\theta2 & -i\sin\frac\theta2\  \\ -i\sin\frac\theta2 & \cos\frac\theta2\end{pmatrix}$$
$$R_Y(\theta) = \begin{pmatrix}\cos\frac\theta2 & -\sin\frac\theta2\ \\ \sin\frac\theta2 & \cos\frac\theta2\end{pmatrix}$$

$$R_Z(\theta) = \begin{pmatrix}e^{-i\theta/2} & 0\ \\ 0 & e^{i\theta/2}\end{pmatrix}$$
- RY(pi/3) = {{}}

</details>

---

### 4. [clausia #1](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Labeling Pauli operators*

Which code fragment constructs the Pauli operator $Z\otimes X$ (-Z on qubit 1, X on qubit 0) for a two-qubit system?

a) `p = Pauli('ZX')`  
b) `p = Pauli('XZ')`  
c) `p = Pauli('IZ')`  
d) `p = Pauli('XI')`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #1](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

- OK

</details>

---

### 5. [clausia #2](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Square-root-of-X twice*

A qubit is initialised in $|0\rangle$. The following Qiskit program is run:

```python
qc = QuantumCircuit(1)
qc.sx(0)
qc.sx(0)
qc.measure_all()
```

Which final *computational* state does this sequence prepare (ignoring global phase)?

a) $|+\rangle$  
b) $i\,|1\rangle$  
c) $|1\rangle$  
d) $|0\rangle$

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [clausia #2](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

- OK

</details>

---

### 6. [clausia #3](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Phase from an **S** gate*

Applying `SGate` (`qc.s(0)`) to a qubit in state $|1\rangle$ introduces which global phase?

a) $+\frac{\pi}{2}$  
b) $-\frac{\pi}{2}$  
c) $+\pi$  
d) $-\pi$

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #3](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

- OK

</details>

---

### 7. [clausia #4](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Hadamard followed by Z*

Consider

```python
qc = QuantumCircuit(1)
qc.h(0)
qc.z(0)
qc.measure_all()
```

What is the probability of measuring the classical bit `1`?

a) 0.25  
b) 0.50  
c) 0.75  
d) 1.00

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [clausia #4](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

- |1> ->  |0>-|1> -> |0>+|1> -> (b)

</details>

---

### 8. [clausia #5](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Probabilities after an $R_x$ rotation*

```python
qc = QuantumCircuit(1)
qc.rx(np.pi/3, 0)
qc.measure_all()
```

Approximately what is the probability of obtaining outcome `1`?

a) 0.25  
b) 0.50  
c) 0.75  
d) 0.866

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #5](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

- cos 3/pi 에 제곱

</details>

---

### 9. [clausia #6](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Generating a Bell state*

Which of the following code fragments prepares the Bell state $|\Phi^{+}\rangle = (|00\rangle+|11\rangle)/\sqrt{2}$?

a) `qc.h(0); qc.cx(0,1)`  
b) `qc.h(1); qc.cx(1,0)`  
c) `qc.x(0); qc.h(1); qc.cx(1,0)`  
d) `qc.h(0); qc.cz(0,1)`

<details>
<summary>정답</summary>

**A,B**

해설은 출처 원문 참고: [clausia #6](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

- OK

</details>

---

### 10. [clausia #7](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Commutation of Pauli gates*

Which pair of single-qubit Pauli operations **commute** with each other?

a) X and Z  
b) Y and Z  
c) X and X  
d) X and Y

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [clausia #7](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

- OK

</details>

---

### 11. [clausia #8](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Applying a Pauli-Y gate in Qiskit*

Which code fragment applies a Pauli-Y operation to qubit 0 of an existing circuit `qc`?

a) `qc.sx(0)`  
b) `qc.y(0)`  
c) `qc.t(0)`  
d) `qc.rz(np.pi, 0)`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [clausia #8](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

- OK

</details>

---

### 12. [MarcoBarroca #4](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Using Qiskit's displayed state-label ordering, what final basis state is prepared by this circuit?

```python
from qiskit import QuantumCircuit

qc = QuantumCircuit(3)
qc.x(2)
qc.cx(2, 0)
qc.x(1)
qc.cx(1, 2)
```

- **A.** `|011>`
- **B.** `|110>`
- **C.** `|101>`
- **D.** `|111>`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #4](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

- 000 -> 100 -> 101 -> 111 -> 011

</details>

---

### 13. [MarcoBarroca #18](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

The following one-qubit circuit is sampled many times. What is the expected probability of bit value 0?

```python
from qiskit import QuantumCircuit
import numpy as np

qc = QuantumCircuit(1)
qc.reset(0)
qc.ry(2 * np.pi / 3, 0)
qc.measure_all()
```

- **A.** `0.50`
- **B.** `1.00`
- **C.** `0.25`
- **D.** `0.75`

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [MarcoBarroca #18](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 14. [MarcoBarroca #20](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Ignoring global phase, which Pauli operator matches the one-qubit unitary below?

```python
qc = QuantumCircuit(1)
qc.z(0)
qc.x(0)
qc.z(0)
```

- **A.** `Pauli('X')`
- **B.** `Pauli('Z')`
- **C.** `Pauli('Y')`
- **D.** No valid Pauli operator

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #20](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 15. [MarcoBarroca #25](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which code fragment is valid and creates a one-qubit Pauli Z operator?

- **A.** `p = Pauli('2Z')`
- **B.** `p = Pauli(QuantumCircuit(1).z(0))`
- **C.** `p = Pauli('ZY') @ Pauli('Y')`
- **D.** `p = Pauli('Z')`

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #25](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 16. [MarcoBarroca #33](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which two-operation sequence prepares `|1>` even if the qubit's previous state is unknown?

- **A.** `z` followed by `measure`
- **B.** `reset` followed by `h`
- **C.** A nonexistent `set_state(1)` instruction
- **D.** `reset` followed by `x`

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #33](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 17. [MarcoBarroca #36](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A state has amplitude only on `|1>`. What relative phase does `TdgGate` apply to that component?

- **A.** `exp(-i*pi/4)`
- **B.** `exp(i*pi/4)`
- **C.** `exp(i*pi/2)`
- **D.** `-1`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #36](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 18. [MarcoBarroca #38](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which line creates a two-qubit Pauli with Z on qubit 1 and X on qubit 0, using Qiskit's Pauli-label ordering?

- **A.** `p = Pauli('ZI')`
- **B.** `p = Pauli('IX')`
- **C.** `p = Pauli('ZX')`
- **D.** `p = Pauli('XZ')`

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [MarcoBarroca #38](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 19. [MarcoBarroca #40](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which array is returned by this Pauli object?

```python
from qiskit.quantum_info import Pauli

print(Pauli('Y').to_matrix())
```

- **A.** 

    ```text
    [[0.+0.j 0.-1.j]
     [0.+1.j 0.+0.j]]
    ```
- **B.** 

    ```text
    [[0.+0.j 1.+0.j]
     [1.+0.j 0.+0.j]]
    ```
- **C.** 

    ```text
    [[ 1.+0.j  0.+0.j]
     [ 0.+0.j -1.+0.j]]
    ```
- **D.** A sampled counts dictionary

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #40](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 20. [MarcoBarroca #53](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which line creates a four-qubit Pauli operator with `Y` on qubit 0 and identity on qubits 1, 2, and 3?

- **A.** `p = Pauli('YIII')`
- **B.** `p = Pauli('IIYI')`
- **C.** `p = Pauli('Y')`
- **D.** `p = Pauli('IIIY')`

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #53](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 21. [MarcoBarroca #60](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

After this one-qubit circuit is built, which state has been prepared?

```python
from qiskit import QuantumCircuit

qc = QuantumCircuit(1)
qc.reset(0)
qc.x(0)
qc.h(0)
```

- **A.** |->
- **B.** |0>
- **C.** |1>
- **D.** |+>

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #60](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 22. [MarcoBarroca #61](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

What is the approximate probability of measuring bit value 1 after this circuit?

```python
from qiskit import QuantumCircuit
import numpy as np

qc = QuantumCircuit(1)
qc.reset(0)
qc.rx(2 * np.pi / 3, 0)
qc.measure_all()
```

- **A.** `0.25`
- **B.** `0.50`
- **C.** `1.00`
- **D.** `0.75`

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #61](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 23. [Q-Bees #5](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You want to compare two Qiskit circuits to check if they implement the same unitary (up to global phase). Which workflow is most appropriate?

- A
Compare their text diagrams produced by qc.draw("text")

- B
Check that they have the same number of gates and qubits

- C
Convert both to Operator objects and compare the matrices

- D
Run both on a simulator for a few random input states and compare outputs

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [Q-Bees #5](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 24. [Q-Bees #6](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

Which best describes the relationship between QuantumCircuit and Operator in Qiskit?

- A
Operators can only be created from measurement results, not from circuits

- B
QuantumCircuit and Operator are unrelated; they live in different namespaces

- C
QuantumCircuit is a subclass of Operator

- D
Operator provides a mathematical representation of the linear map implemented by a circuit

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [Q-Bees #6](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 25. [Q-Bees #7](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You are working with Qiskit operators and want to represent the Hamiltonian $H=0.5Z_0Z_1$+$X_1$ for use with primitives. What is the most appropriate Qiskit class to represent this operator compactly?

- A
DensityMatrix from qiskit.quantum_info

- B
Operator from qiskit.quantum_info with a full 4×4 matrix

- C
PauliList from qiskit.quantum_info without coefficients

- D
SparsePauliOp from qiskit.quantum_info built from Pauli strings and coefficients

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [Q-Bees #7](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---


---

## 오답 정리

| 문항 | 내가 고른 답 | 정답 | 왜 틀렸나 |
| --- | --- | --- | --- |
| | | | |

## 이 토픽에서 반복해서 틀리는 것

- [ ]
