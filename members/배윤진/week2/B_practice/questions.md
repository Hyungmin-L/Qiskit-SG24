# Week 2 — Section B: 기출 문제

> syllabus 토픽: **Visualize quantum circuits, measurements, and states**
> Advocate가 만든 practice exam 4종에서 이 토픽에 해당하는 문항만 추린 것. 총 **17문항**.

출처별 문항 수: algovista 2, clausia 6, MarcoBarroca 5, Q-Bees 4

풀이 방법 — 정답은 접혀 있으니 **먼저 풀고** 펼칠 것. 틀린 문항은 번호를 아래 오답 목록에
적고, 이유를 한 줄로 남긴다. 문제 자체보다 그 한 줄이 시험 직전에 쓸모 있다.

---


### 1. [algovista #4](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

Which visualization method should be chosen to visualize a multi-qubit quantum state specifically when you need to highlight continuous phase values by color mapping across computational basis state projections without displaying a full density matrix?

A. `plot_state_city`

B. `plot_state_qsphere`

C. `plot_state_hinton`

D. `plot_bloch_multivector`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [algovista #4](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 2. [algovista #5](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

What visualization is produced by executing the following snippet on a multi-qubit state, tracking Qiskit's right-to-left string indexing rule?

```python
from qiskit.quantum_info import Statevector
from qiskit.visualization import plot_bloch_multivector

sv = Statevector.from_label('r-')
plot_bloch_multivector(sv)
```

A. Qubit 0 vector points along $+Y$; Qubit 1 vector points along $-Z$

B. Qubit 0 vector points along $-X$; Qubit 1 vector points along $+Y$

C. Qubit 0 vector points along $+X$; Qubit 1 vector points along $-Y$

D. Qubit 0 vector points along $-Z$; Qubit 1 vector points along $+X$

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [algovista #5](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 3. [clausia #9](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Draw a circuit with Matplotlib*

Which call renders a `QuantumCircuit` named `qc` using Matplotlib?

a) `qc.draw(output="mpl")`  
b) `qc.plot("mpl")`  
c) `plot_circuit(qc, backend="mpl")`  
d) `qc.draw_mpl()`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #9](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 4. [clausia #10](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Save a circuit diagram as a PNG*

Which snippet correctly saves a Matplotlib circuit diagram to `circuit.png`?

a) `from qiskit.visualization import circuit_drawer; circuit_drawer(qc, output="mpl", filename="circuit.png")`  
b) `qc.draw(filename="circuit.png")`  
c) `qc.save(output="mpl", file="circuit.png")`  
d) `from qiskit.visualization import plot_histogram; plot_histogram(qc, filename="circuit.png")`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #10](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 5. [clausia #11](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Visualize measurement outcomes*

Given `counts = {"00": 520, "01": 504}`, which function produces a bar chart of these results?

a) `plot_state_city(counts)`  
b) `plot_histogram(counts)`  
c) `plot_bloch_multivector(counts)`  
d) `plot_state_qsphere(counts)`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [clausia #11](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 6. [clausia #12](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Overlay two histograms*

You have `counts_a` and `counts_b` from two circuits. Which call overlays them in one figure with a legend?

a) `plot_histogram(counts_a, counts_b, legend=["A","B"])`  
b) `plot_histogram([counts_a, counts_b], legend=["A","B"])`  
c) `plot_state_city([counts_a, counts_b], labels=["A","B"])`  
d) `plot_bloch_multivector([counts_a, counts_b], legend=["A","B"])`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [clausia #12](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 7. [clausia #13](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Visualize a single-qubit pure state on the Bloch sphere*

You computed `state = Statevector.from_label("0")`. Which call plots the state on a Bloch sphere?

a) `plot_state_qsphere(state)`  
b) `plot_state_city(state)`  
c) `plot_bloch_multivector(state)`  
d) `plot_histogram(state)`

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [clausia #13](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 8. [clausia #14](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Qsphere for equal superposition of two qubits*

Which code produces a Qsphere with **four equally sized points of the same color** (equal amplitudes, zero relative phase)?

a)

```python
qc = QuantumCircuit(2); qc.h(0); qc.h(1)
state = Statevector.from_instruction(qc)
plot_state_qsphere(state)
```

b)

```python
qc = QuantumCircuit(2); qc.h(0); qc.z(0); qc.h(1)
state = Statevector.from_instruction(qc)
plot_state_qsphere(state)
```

c)

```python
qc = QuantumCircuit(2); qc.h(0); qc.h(1); qc.z(1)
state = Statevector.from_instruction(qc)
plot_state_qsphere(state)
```

d)

```python
qc = QuantumCircuit(2); qc.x(0); qc.x(1); qc.h(0); qc.h(1)
state = Statevector.from_instruction(qc)
plot_state_qsphere(state)
```

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #14](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 9. [MarcoBarroca #6](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A qubit is initialized with amplitudes `[sqrt(3)/2, 1/2]`. Which Bloch-vector panel represents the state?

![Question figure](https://raw.githubusercontent.com/MarcoBarroca/qiskit-v2-mock-exam/main/assets/visuals/bloch_panels.png)

- **A.** Panel A
- **B.** Panel B
- **C.** Panel C
- **D.** Panel D

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [MarcoBarroca #6](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 10. [MarcoBarroca #32](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

**Select 2.**

Which Python objects are valid inputs for `plot_distribution`?

- [ ] **A.** `{0: [500, 250], 1: [500, 750]}`
- [ ] **B.** `[(0, 500), (3, 500)]`
- [ ] **C.** `[0, 1, 2], [500, 250, 250]`
- [ ] **D.** `{0: 500, 3: 500}`
- [ ] **E.** `[{0: 500, 3: 500}, {0: 250, 1: 750}]`

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #32](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 11. [MarcoBarroca #49](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which panel matches the qsphere-style state that would be produced by a Bell-like state with populated `|00>` and `|11>` basis states and a relative phase?

![Question figure](https://raw.githubusercontent.com/MarcoBarroca/qiskit-v2-mock-exam/main/assets/visuals/qsphere_panels.png)

- **A.** Panel A
- **B.** Panel B
- **C.** Panel C
- **D.** Panel D

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #49](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 12. [MarcoBarroca #54](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which panel could be produced by `plot_histogram([ideal_counts, hardware_counts])` when the ideal simulator is mostly `00` and the hardware result has visible counts in both `00` and `11`?

![Question figure](https://raw.githubusercontent.com/MarcoBarroca/qiskit-v2-mock-exam/main/assets/visuals/histogram_panels.png)

- **A.** Panel A
- **B.** Panel B
- **C.** Panel C
- **D.** Panel D

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #54](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 13. [MarcoBarroca #68](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which circuit drawing panel is produced by the code below?

```python
from qiskit import ClassicalRegister, QuantumCircuit, QuantumRegister

q = QuantumRegister(2, 'q')
c = ClassicalRegister(2, 'c')
qc = QuantumCircuit(q, c)
qc.h(q[0])
qc.measure(q[0], c[0])
with qc.switch(c[0]) as case:
    with case(0):
        qc.z(q[1])
    with case(1):
        qc.x(q[1])
qc.measure(q[1], c[1])
qc.draw(output='mpl')
```

![Question figure](https://raw.githubusercontent.com/MarcoBarroca/qiskit-v2-mock-exam/main/assets/visuals/dynamic_switch_panels.png)

- **A.** Panel A
- **B.** Panel B
- **C.** Panel C
- **D.** Panel D

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #68](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 14. [Q-Bees #2](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You have a parameterized circuit and want to visualize how the parameters appear in the diagram. What behavior should you expect from qc.draw("mpl")?

- A
Parameters will be hidden; only gate types will be shown

- B
The diagram will show symbolic parameter names (like $θ_0$, $θ_1$) as labels on the gates

- C
The drawer will fail unless all parameters are numerically bound

- D
All parameters will be treated as 0 during drawing

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [Q-Bees #2](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 15. [Q-Bees #4](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

In Qiskit visualization, what is a typical use of a style dictionary when drawing a circuit with the Matplotlib-based drawer?

- A
To control colors, fonts, and gate shapes in the circuit diagram

- B
To define parameter values for parameterized gates

- C
To specify initial qubit states $|0⟩$ or $|1⟩$

- D
To change backend-specific transpilation settings

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [Q-Bees #4](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 16. [Q-Bees #8](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You create a 3-qubit circuit and want to visualize the statevector after applying some gates using the state_city visualization. Which Qiskit toolchain correctly produces this visualization?

- A
Simulate the circuit with AerSimulator(method='statevector'), get the final statevector, and pass it to plot_state_city

- B
Use Statevector.from_int only, because visualizations are created automatically when constructing the object

- C
Call circuit.draw('mpl') and interpret the diagram as a state-city plot

- D
Use the Sampler primitive and directly pass its quasi-distribution to plot_state_city

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [Q-Bees #8](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 17. [Q-Bees #9](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You need to visualize how the layout and gate structure of a circuit changes after transpilation at a certain optimization level. Which pair of visualizations best helps you compare pre- and post-transpilation circuits on a specific backend?

- A
Use plot_state_city before and after transpilation to compare amplitude distributions

- B
Use plot_histogram on simulated results of both circuits to compare measurement distributions

- C
Use plot_error_map for the backend and plot_histogram of circuit counts

- D
Use circuit.draw('mpl') before and circuit.draw('mpl') after calling transpile, with the same reverse_bits and fold settings

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [Q-Bees #9](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---


---

## 오답 정리

| 문항 | 내가 고른 답 | 정답 | 왜 틀렸나 |
| --- | --- | --- | --- |
| | | | |

## 이 토픽에서 반복해서 틀리는 것

- [ ]
