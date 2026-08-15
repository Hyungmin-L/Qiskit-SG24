# Week 6 — Section B: 기출 문제

> syllabus 토픽: **Use the Estimator primitive**
> Advocate가 만든 practice exam 4종에서 이 토픽에 해당하는 문항만 추린 것. 총 **28문항**.

출처별 문항 수: algovista 3, clausia 7, MarcoBarroca 18

풀이 방법 — 정답은 접혀 있으니 **먼저 풀고** 펼칠 것. 틀린 문항은 번호를 아래 오답 목록에
적고, 이유를 한 줄로 남긴다. 문제 자체보다 그 한 줄이 시험 직전에 쓸모 있다.

---


### 1. [algovista #13](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

Which represents the standard structural layout sequence for executing an experimental workflow with the V2 Estimator primitive?

A. Circuit design -> Primitive instantiation -> Hardware selection -> Execution

B. Backend selection -> Circuit design -> Observable mapping -> Transpilation -> Layout application to observables -> Primitive configuration -> Execution

C. Primitive configuration -> Execution -> Local compilation -> Topology selection

D. Observable mapping -> Execution -> Local transpilation -> Backend selection

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [algovista #13](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 2. [algovista #15](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

When defining an execution block for `EstimatorV2.run()`, what is the correct structure for a single Primitive Unified Block (PUB) tuple?

A. `(circuit, observables)`

B. `(circuit, observables, parameter_values, precision)`

C. `(circuit, observables, shots)`

D. `(circuit, parameter_values)`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [algovista #15](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 3. [algovista #16](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

According to the broadcasting rules used by Qiskit Runtime Primitive Unified Blocks (PUBs), what happens if a circuit uses a parameter array of size 5 and an observable array of size 1?

A. The execution fails immediately due to a dimension mismatch error.

B. The single observable is automatically broadcast to match all 5 parameter sets, resulting in 5 expectation values.

C. The execution defaults to a size of 1, discarding the remaining parameter values.

D. The system pads the missing observable slots with identity operators.

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [algovista #16](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 4. [clausia #32](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*To change the built-in error-mitigation strategy for every circuit an `Estimator` runs, which option should you set?*

a) `options.dynamical_decoupling`  
b) `options.resilience_level`  
c) `options.meas_level`  
d) `options.optimization_level`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [clausia #32](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 5. [clausia #37](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Choosing a built-in error-mitigation profile*

Which `EstimatorOptions` field lets you pick one of Qiskit’s preset error-mitigation bundles (level 0, 1 or 2)?

a) `dynamical_decoupling`  
b) `default_precision`  
c) `resilience_level`  
d) `seed_estimator`

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [clausia #37](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 6. [clausia #38](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Effect of setting `default_shots`*

When you set `estimator.options.default_shots`, what *immediate* consequence does the documentation state?

a) It ignores `resilience_level`  
b) It overrides any `default_precision` value  
c) It disables Pauli-twirling  
d) It forces precision to 1 / √shots

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [clausia #38](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 7. [clausia #39](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Precision-precedence hierarchy*

For any Estimator PUB, which source of precision has the **highest** precedence if all four are supplied?

a) `estimator.options.default_precision`  
b) A `precision` keyword in `run()`  
c) The product `num_randomizations × shots_per_randomization` from twirling  
d) A precision value embedded directly in the PUB

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [clausia #39](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 8. [clausia #40](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Valid broadcasting shapes*

The Estimator broadcasts observables and parameter sets like NumPy. Which pair below *will* broadcast? (O = observables shape, P = parameter\_values shape.)

a) O (3 × 1), P (100 × 2)  
b) O (3 × 1), P (1 × 100 × 2)  
c) O (5), P (3)  
d) O (2 × 1), P (6 × 5 × 4)

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [clausia #40](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 9. [clausia #41](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Allowed keyword arguments to `Estimator.run()`*

Which call is **valid** for Estimator V2 according to the interface?

a) `estimator.run(pubs, precision=0.02)`  
b) `estimator.run(pubs, shots=4096)`  
c) `estimator.run(pubs, mode="priority")`  
d) `estimator.run(pubs, max_execution_time=60)`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #41](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 10. [clausia #42](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Accessing expectation values*

After the job completes, you write

```python
pub_result = job.result()[0]      # Estimator V2
```

Which attribute gives the array of expectation-value estimates?

a) `pub_result.evs`  
b) `pub_result.values`  
c) `pub_result.data.evs`  
d) `pub_result.data.values`

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [clausia #42](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 11. [MarcoBarroca #11](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which construction line puts `EstimatorV2` in a valid execution context?

- **A.** `estimator = EstimatorV2(mode=sampler)`
- **B.** `estimator = EstimatorV2(mode=backend)`
- **C.** `estimator = EstimatorV2(mode=observable)`
- **D.** `estimator = EstimatorV2(mode=circuit)`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [MarcoBarroca #11](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 12. [MarcoBarroca #13](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A ZNE configuration is being reviewed. Which assignment uses the expected value type for noise amplification factors?

- **A.** `estimator.options.resilience.zne.noise_factors = 'linear'`
- **B.** `estimator.options.resilience.zne.noise_factors = (-1, 1, 3)`
- **C.** `estimator.options.resilience.zne.noise_factors = {'low': 1, 'high': 3}`
- **D.** `estimator.options.resilience.zne.noise_factors = (1, 2, 4)`

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #13](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 13. [MarcoBarroca #14](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A workload should use the preset mitigation behavior that includes ZNE. Which assignment selects that resilience level?

- **A.** `estimator.options.resilience_level = 0`
- **B.** `estimator.options.resilience_level = -1`
- **C.** `estimator.options.resilience_level = 2`
- **D.** `estimator.options.resilience_level = 1`

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [MarcoBarroca #14](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 14. [MarcoBarroca #17](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

For Estimator, which tuple has the shape of a primitive unified bloc rather than a local plotting or serialization object?

- **A.** `(counts, legend, title)`
- **B.** `(qasm_source, filename)`
- **C.** `(backend_name, api_token)`
- **D.** `(isa_circuit, isa_observables, parameter_values)`

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #17](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 15. [MarcoBarroca #22](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A hardware workload shows coherent over-rotation effects. Which option names the noise class that Pauli twirling is designed to reshape statistically?

- **A.** HTTP retry noise
- **B.** Classical register overflow
- **C.** Coherent gate noise
- **D.** Finite-shot sampling noise

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [MarcoBarroca #22](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 16. [MarcoBarroca #27](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

The diagram below omits the row names. In Qiskit Runtime Estimator broadcasting terminology, what is row B called?

![Question figure](https://raw.githubusercontent.com/MarcoBarroca/qiskit-v2-mock-exam/main/assets/visuals/broadcasting_panels.png)

- **A.** Broadcast single observable
- **B.** Zip
- **C.** Outer/Product
- **D.** Standard n-D generalization

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [MarcoBarroca #27](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 17. [MarcoBarroca #28](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

`pubs` is a list of Estimator PUBs. Which line submits them?

- **A.** `job = estimator.run(pubs)`
- **B.** `job = estimator.compute(pubs)`
- **C.** `job = estimator.execute(pubs)`
- **D.** `job = estimator.evaluate(pubs)`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #28](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 18. [MarcoBarroca #29](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which object shape best represents a Runtime primitive unified bloc?

- **A.** A list of gates appended directly to a circuit
- **B.** A pair containing only an observable and a backend name
- **C.** A REST-only JSON object that the Python SDK never uses
- **D.** A tuple-like workload unit that includes a circuit and data associated with that circuit

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #29](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 19. [MarcoBarroca #30](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Dynamical decoupling is enabled for a scheduled circuit. Which error source is it meant to suppress?

- **A.** REST authentication failures
- **B.** Incorrect Python imports
- **C.** Idle/decoherence effects during gaps
- **D.** Readout assignment errors only

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [MarcoBarroca #30](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 20. [MarcoBarroca #31](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A mitigation setting randomizes circuit-level operations so coherent errors are converted into easier-to-average stochastic behavior. Which workload element is being randomized?

- **A.** The local Python module cache
- **B.** Gates or measurements in the submitted circuits
- **C.** Runtime job tags
- **D.** Session IDs

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [MarcoBarroca #31](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 21. [MarcoBarroca #34](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A `StatevectorEstimator` PUB contains a two-parameter circuit, one observable, and three parameter rows:

```python
alpha = Parameter('alpha')
beta = Parameter('beta')
qc = QuantumCircuit(1)
qc.ry(alpha, 0)
qc.rz(beta, 0)
observable = SparsePauliOp('X')
values = np.array([[0.0, 0.0], [np.pi / 3, np.pi / 5], [np.pi / 2, np.pi / 7]])
job = StatevectorEstimator().run([(qc, observable, values)])
```

- **A.** The job fails because Estimator PUBs cannot contain parameter arrays.
- **B.** The primitive transpiles the circuit but does not evaluate the observable.
- **C.** The result contains one expectation-value estimate for each supplied parameter row.
- **D.** Only the first parameter row is evaluated.

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [MarcoBarroca #34](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 22. [MarcoBarroca #42](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which option path controls the number of randomized circuits/samples used by twirling?

- **A.** `estimator.options.twirling.default_shots`
- **B.** `estimator.options.twirling.enable_gates`
- **C.** `estimator.options.twirling.num_randomizations`
- **D.** `estimator.options.twirling.strategy`

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [MarcoBarroca #42](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 23. [MarcoBarroca #43](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

After transpilation, `isa_circuit.layout` is available. Which line maps observables to the same layout before Estimator execution?

- **A.** `isa_observables = [isa_circuit.set_layout(op) for op in observables]`
- **B.** `isa_observables = [op.apply_layout(isa_circuit.layout) for op in observables]`
- **C.** `isa_observables = [isa_circuit.layout(op) for op in observables]`
- **D.** `isa_observables = [op(isa_circuit.layout) for op in observables]`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [MarcoBarroca #43](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 24. [MarcoBarroca #44](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which pair of PUB array shapes is broadcast-compatible under the primitive input rules?

- **A.** `(2, 1, 3)` and `(1, 5, 1)`
- **B.** `(2, 3)` and `(4, 3)`
- **C.** `(5,)` and `(4,)`
- **D.** `(2, 0)` and `(2, 3)`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #44](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 25. [MarcoBarroca #45](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

**Select 3.**

A parameterized Estimator workload is packaged as one PUB. Which items can be part of that PUB?

- [ ] **A.** The user's API token
- [ ] **B.** The backend queue position
- [ ] **C.** A histogram legend
- [ ] **D.** The quantum circuit
- [ ] **E.** The observable or observable array
- [ ] **F.** The parameter-value array

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #45](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 26. [MarcoBarroca #51](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

An Estimator PUB uses parameter values with shape `(3, 1, 2)` and observables with shape `(1, 4, 1)`. What shape should the expectation-value array have?

- **A.** `(12, 2)`
- **B.** `(3, 4, 2)`
- **C.** `(4, 3, 2)`
- **D.** `(3, 1, 1)`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [MarcoBarroca #51](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 27. [MarcoBarroca #59](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Why is broadcasting useful when building Estimator PUBs?

- **A.** It creates a new Runtime session for each parameter value.
- **B.** It combines compatible observable and parameter arrays without manually writing every pair.
- **C.** It decomposes two-qubit gates into the backend basis.
- **D.** It increases the number of shots automatically.

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [MarcoBarroca #59](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 28. [MarcoBarroca #66](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

**Order the options.**

Put these Estimator workflow steps in the correct order for a hardware-oriented run.

- **A.** Create the Estimator primitive in the selected execution mode.
- **B.** Submit the PUBs with estimator.run(...) and retrieve the result.
- **C.** Define the quantum circuit and observable operator.
- **D.** Transpile the circuit to the target ISA and apply the layout to the observables.

<details>
<summary>정답</summary>

**C,D,A,B**

해설은 출처 원문 참고: [MarcoBarroca #66](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---


---

## 오답 정리

| 문항 | 내가 고른 답 | 정답 | 왜 틀렸나 |
| --- | --- | --- | --- |
| | | | |

## 이 토픽에서 반복해서 틀리는 것

- [ ]
