# Week 5 — Section B: 기출 문제

> syllabus 토픽: **Use the Sampler primitive**
> Advocate가 만든 practice exam 4종에서 이 토픽에 해당하는 문항만 추린 것. 총 **14문항**.

출처별 문항 수: algovista 2, clausia 6, MarcoBarroca 5, Q-Bees 1

풀이 방법 — 정답은 접혀 있으니 **먼저 풀고** 펼칠 것. 틀린 문항은 번호를 아래 오답 목록에
적고, 이유를 한 줄로 남긴다. 문제 자체보다 그 한 줄이 시험 직전에 쓸모 있다.

---


### 1. [algovista #14](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

You have a parameterized circuit `qct` with two parameters, `alpha` and `beta`. Which code snippet correctly formats the parameter values for a single Primitive Unified Block (PUB) when calling `SamplerV2.run()`?

A. 
```python
pub = (qct, {alpha: [0.1, 0.2], beta: [0.4, 0.5]})
job = sampler.run([pub])
```

B. 
```python
pub = (qct, [0.1, 0.2, 0.4, 0.5])
job = sampler.run([pub])
```

C. 
```python
pub = (qct, [{alpha: 0.1, beta: 0.4}, {alpha: 0.2, beta: 0.5}])
job = sampler.run([pub])
```

D. 
```python
pub = (qct, alpha, beta, [0.1, 0.4])
job = sampler.run([pub])
```

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [algovista #14](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 2. [algovista #17](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

You execute a parameterized circuit via SamplerV2 with an array of 4 parameter sets. Assuming your classical register is named 'c', how should you retrieve the measurement counts for the third parameter configuration from the job result object?

A. `result.get_counts(2)`

B. `result[0].data.meas.get_counts()[2]`

C. 
```python
pub_result = result[0]
pub_result.data.c.get_counts(2)
```

D. `result.pub_data[2].counts()`

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [algovista #17](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 3. [clausia #29](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Broadcasting parameter values*

`circuits` contains two parameterised circuits. Which `parameter_values` array will **broadcast correctly** under Runtime rules?

a) shape (2, 3)  
b) shape (1, 3)  
c) shape (3, 2)  
d) shape (3, 3)  

*(Assume each circuit has three Parameters.)*

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [clausia #29](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 4. [clausia #31](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*What does the `SamplerOptions` parameter **`options.default_shots`** specify?*

a) The sum of measurement results on every qubit  
b) The number of randomisations applied to the circuit  
c) The number of times the circuit is executed (shots)  
d) The number of dynamical-decoupling sequences

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [clausia #31](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 5. [clausia #33](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Which `Sampler` option lets you enable or configure dynamical-decoupling sequences during execution?*

a) `options.dynamical_decoupling`  
b) `options.resilience_level`  
c) `options.default_shots`  
d) `options.bias_mitigation`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #33](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 6. [clausia #34](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*In Qiskit v2, which of the following is a *valid* call to execute sampling with **`Sampler.run()`**?*

a) `sampler.run([circuit1, circuit2])` — returns a job object  
b) `sampler.run(distribution, circuit1)`  
c) `sampler.run(circuit1, distribution="gauss")`  
d) `sampler.run(shots=1024)`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #34](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 7. [clausia #35](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*If you omit the `shots` argument when calling `Sampler.run()`, how is the shot count chosen?*

a) It falls back to the backend’s default shots  
b) It is auto-determined from circuit depth  
c) It uses the value of `options.default_shots` set on the `Sampler` instance  
d) It is fixed at 1024 shots

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [clausia #35](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 8. [clausia #36](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*What does a `Sampler` job **return** to the user?*

a) A list of expectation values of observables  
b) Raw state-vector amplitudes  
c) A list of quasi-probability distributions over measured bit-strings  
d) Pulse-level schedules for each circuit

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [clausia #36](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 9. [MarcoBarroca #1](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A primitive is needed for sampled measurement data rather than expectation values. What does `SamplerV2` return from measured circuits?

- **A.** Observable expectation values
- **B.** A final statevector
- **C.** A backend configuration document
- **D.** Classical-register bitstring samples/count-access data

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #1](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 10. [MarcoBarroca #5](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

**Select 2.**

Which `SamplerV2` option groups configure suppression or mitigation behavior?

- [ ] **A.** `sampler.options.twirling`
- [ ] **B.** `sampler.options.dynamical_decoupling`
- [ ] **C.** `sampler.options.surface_codes`
- [ ] **D.** `sampler.options.max_execution_time`
- [ ] **E.** `sampler.options.account_token`

<details>
<summary>정답</summary>

**A,B**

해설은 출처 원문 참고: [MarcoBarroca #5](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 11. [MarcoBarroca #9](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A sampler PUB is submitted without its own shot override. The notebook contains this setup:

```python
sampler = SamplerV2(mode=backend)
sampler.options.default_shots = 2048
```

- **A.** The primitive creates 2048 twirled circuits before sampling.
- **B.** Each measured qubit is read 2048 times before circuit execution begins.
- **C.** The backend is reserved for exactly 2048 seconds.
- **D.** The PUB is sampled with 2048 shots unless the PUB supplies a different shot count.

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #9](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 12. [MarcoBarroca #15](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A sampler job was run for a circuit that measured classical register `creg`. Which line can return a counts dictionary from the first PUB result?

- **A.** `job.result().metadata.counts(creg)`
- **B.** `job.result()[0].data.creg.get_counts()`
- **C.** `job.get_counts(creg)`
- **D.** `job.result(creg).to_counts_dict()`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [MarcoBarroca #15](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 13. [MarcoBarroca #57](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A circuit has already been transpiled to ISA form. Which call uses the Sampler v2 input shape?

- **A.** `job = sampler.run(isa_circuit, SparsePauliOp('Z'))`
- **B.** `job = sampler.run(backend, isa_circuit)`
- **C.** `job = sampler.run(circuit=isa_circuit, mode=backend)`
- **D.** `job = sampler.run([isa_circuit])`

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #57](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 14. [Q-Bees #14](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You are using Qiskit’s Sampler primitive to estimate outcome probabilities for a list of circuits. Which statement best describes how the primitive reports these probabilities and how they differ from raw counts?

- A
Sampler returns raw counts per bitstring with no normalization

- B
Sampler returns only expectation values of Pauli observables

- C
Sampler returns quasi-probabilities per bitstring that may not be exactly non-negative or normalized

- D
Sampler returns exact probabilities with infinite precision, independent of the number of shots

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [Q-Bees #14](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---


---

## 오답 정리

| 문항 | 내가 고른 답 | 정답 | 왜 틀렸나 |
| --- | --- | --- | --- |
| | | | |

## 이 토픽에서 반복해서 틀리는 것

- [ ]
