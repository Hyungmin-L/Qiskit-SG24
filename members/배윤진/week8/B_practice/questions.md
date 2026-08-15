# Week 8 — Section B: 기출 문제

> syllabus 토픽: **Operate with OpenQASM**
> Advocate가 만든 practice exam 4종에서 이 토픽에 해당하는 문항만 추린 것. 총 **11문항**.

출처별 문항 수: algovista 2, clausia 2, MarcoBarroca 3, Q-Bees 4

풀이 방법 — 정답은 접혀 있으니 **먼저 풀고** 펼칠 것. 틀린 문항은 번호를 아래 오답 목록에
적고, 이유를 한 줄로 남긴다. 문제 자체보다 그 한 줄이 시험 직전에 쓸모 있다.

---


### 1. [algovista #19](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

Which line of OpenQASM 3 code correctly declares a fixed-size array of 8 multi-bit registers, where each register is a 4-bit unsigned integer?

A. `uint[4][8] my_array;`

B. `array[uint[4], 8] my_array;`

C. `uint my_array[4][8];`

D. `register uint[4] my_array[8];`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [algovista #19](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 2. [algovista #25](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

Which OpenQASM 3 feature allows you to change the execution path of a circuit dynamically based on the outcome of a mid-circuit measurement?

A. Dynamic circuit switch-case or conditional if statements evaluating classical bits.

B. The compiletime verification macro system.

C. The reset instruction.

D. The deferred execution pipeline filter.

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [algovista #25](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 3. [clausia #48](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Declaring an 8-bit classical register in OpenQASM 3*

Which line is **valid** syntax?

a) `bit[8] c;`  
b) `creg c[8];`  
c) `bit c[8];`  
d) `uint8 c;`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #48](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 4. [clausia #49](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Exporting a `QuantumCircuit` to an OpenQASM 3 string*

Which function does Qiskit 2.x provide for this task?

a) `QuantumCircuit.qasm()`  
b) `qiskit.qasm3.dumps()`  
c) `qiskit.qasm3.export_string()`  
d) `qiskit.qasm2.dumps()`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [clausia #49](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 5. [MarcoBarroca #24](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

What does this OpenQASM 3 declaration create?

```qasm
uint[16] counter;
```

- **A.** It declares a unsigned 16-bit integer.
- **B.** It indexes the eighth element of an array.
- **C.** It assigns the value inside brackets to the identifier.
- **D.** It declares a Python integer and exports it to Qiskit.

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #24](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 6. [MarcoBarroca #37](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which expression returns an OpenQASM 3 string for a circuit object named `circuit`?

- **A.** `qiskit.qasm3.to_qasm(circuit)`
- **B.** `qiskit.qasm3.export(circuit)`
- **C.** `qiskit.qasm3.write_string(circuit)`
- **D.** `qiskit.qasm3.dumps(circuit)`

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #37](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 7. [MarcoBarroca #50](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which Qiskit fragment implements the same operations and classical-bit mapping as this OpenQASM 3 program?

```qasm
OPENQASM 3.0;
include "stdgates.inc";
bit[3] c;
qubit[3] q;
h q[1];
cx q[1], q[2];
c[2] = measure q[1];
c[0] = measure q[2];
```

- **A.** 

    ```python
    qc = QuantumCircuit(3, 3)
    qc.h(1)
    qc.cx(1, 2)
    qc.measure([1, 2], [0, 2])
    ```
- **B.** 

    ```python
    qc = QuantumCircuit(2, 2)
    qc.h(0)
    qc.cx(0, 1)
    qc.measure([0, 1], [0, 1])
    ```
- **C.** 

    ```python
    qc = QuantumCircuit(3, 3)
    qc.h(1)
    qc.cx(1, 2)
    qc.measure([1, 2], [2, 0])
    ```
- **D.** 

    ```python
    qc = QuantumCircuit(3, 3)
    qc.h(2)
    qc.cx(2, 1)
    qc.measure([1, 2], [2, 0])
    ```

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [MarcoBarroca #50](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 8. [Q-Bees #12](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You are designing a parameterized circuit using Qiskit and want to express it in OpenQASM 3 syntax, including classical control based on measurement outcomes. Which Qiskit component most directly helps generate OpenQASM 3 code from your circuit?

- A
qiskit.qasm3 exporter to convert a QuantumCircuit with classical control into OpenQASM 3

- B
qiskit.qasm2 exporter to produce OpenQASM 2 code, then manually edit it to OpenQASM 3

- C
Only the QuantumCircuit.draw() method, which can output OpenQASM 3 when using the 'qasm3' style

- D
Qiskit does not yet provide any support for OpenQASM 3 export

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [Q-Bees #12](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 9. [Q-Bees #13](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

Consider the following OpenQASM 3 fragment:
```python
bit[1] c;
qubit[1] q;
reset q[0];
rx(1.5708) q[0];
measure q[0] -> c[0];
if (c[0] == 1) {
    z q[0];
}
```
What behavior should a corresponding Qiskit circuit reproduce?

- A
Reset the qubit, apply $R_x(π/2)$, measure, and conditionally apply $Z$ gate only when the outcome is 1

- B
Apply $R_x(π/2)$ measure, and then conditionally reset based on the classical bit

- C
Apply an $R_x(π/2)$ rotation, always apply a $Z$ gate, then measure into a classical bit

- D
Prepare $|1⟩$, measure, then always apply $Z$ gate after measurement

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [Q-Bees #13](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 10. [Q-Bees #18](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You are using Qiskit’s qasm3 exporter on a circuit that includes mid-circuit measurements and classical conditions. How does this relate to the notion of dynamic circuits in Qiskit and OpenQASM 3?

- A
OpenQASM 3 only supports static circuits without measurements

- B
Dynamic circuits are not supported in OpenQASM 3, so the exporter will fail

- C
The exporter can express many dynamic-circuit features, such as mid-circuit measurement and classical branching, as OpenQASM 3 control constructs

- D
Dynamic circuits in Qiskit are fundamentally incompatible with any text-based representation

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [Q-Bees #18](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 11. [Q-Bees #20](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You are translating a simple Qiskit circuit into OpenQASM 3 by hand and want to ensure that it matches Qiskit's qubit and classical bit indexing conventions. Which principle should you follow?

- A
Always reverse the qubit order in OpenQASM 3 because Qiskit uses the opposite convention

- B
Ensure that qubits and bits are declared in OpenQASM 3 arrays with consistent indexing starting at 0, and map Qiskit’s register and bit ordering directly to these indices

- C
Ignore indexing details because simulators automatically correct ordering mismatches

- D
Use 1-based indexing in OpenQASM 3 for both qubits and bits

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [Q-Bees #20](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---


---

## 오답 정리

| 문항 | 내가 고른 답 | 정답 | 왜 틀렸나 |
| --- | --- | --- | --- |
| | | | |

## 이 토픽에서 반복해서 틀리는 것

- [ ]
