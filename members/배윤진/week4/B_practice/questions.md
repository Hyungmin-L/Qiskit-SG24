# Week 4 — Section B: 기출 문제

> syllabus 토픽: **Run quantum circuits**
> Advocate가 만든 practice exam 4종에서 이 토픽에 해당하는 문항만 추린 것. 총 **21문항**.

출처별 문항 수: algovista 4, clausia 6, MarcoBarroca 8, Q-Bees 3

풀이 방법 — 정답은 접혀 있으니 **먼저 풀고** 펼칠 것. 틀린 문항은 번호를 아래 오답 목록에
적고, 이유를 한 줄로 남긴다. 문제 자체보다 그 한 줄이 시험 직전에 쓸모 있다.

---


### 1. [algovista #10](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

Which two approaches are incorrect when managing job contexts using execution modes in Qiskit Runtime V2 primitives?

A. 
```python
with Session(backend=backend) as session:
    sampler = SamplerV2(mode=backend)
```

B. 
```python
session = Session(backend=backend)
sampler = SamplerV2(mode=session)
```

C. 
```python
with Batch(backend=backend) as batch:
    estimator = EstimatorV2(mode=batch)
```

D. 
```python
sampler = SamplerV2(mode="Batch")
```

<details>
<summary>정답</summary>

**A,D**

해설은 출처 원문 참고: [algovista #10](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 2. [algovista #11](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

What occurs when the `.close()` method is called on an active Qiskit Runtime `Session` or `Batch` object instance?

A. The session immediately stops accepting new jobs, and all currently queued or running jobs within that context are forced to cancel.

B. The session stops accepting new job submissions, but any jobs already submitted within the context are allowed to run to completion.

C. The session remains open indefinitely until the maximum system wall clock limit forces a hard server-side termination.

D. The session context is deleted along with its entire historical job record from the cloud dashboard service database.

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [algovista #11](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 3. [algovista #12](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

How does usage time accumulation differ between Batch mode and Session mode on real IBM Quantum backends?

A. Batch mode limits your usage footprint to active QPU processing time, whereas Session mode tracks the total wall clock time from context opening to closure (including processing pauses).

B. Session mode calculates usage based only on pure gate counts, while Batch mode uses real hardware clock duration metrics.

C. There is no difference; both execution modes charge exclusively for full wall clock time from start to finish.

D. Batch mode charges for the compilation time of circuits, whereas Session mode does not.

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [algovista #12](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 4. [algovista #23](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

What happens if you attempt to submit an untranspiled `QuantumCircuit` directly to an IBM Qiskit Runtime V2 primitive execution method?

A. The primitive automatically transpiles the circuit using default optimization settings.

B. The job fails because V2 primitives require circuits to be pre-transpiled to match the backend's native basis gates and physical layout.

C. The primitive routes the circuit to a local simulator instead of the real hardware.

D. The circuit runs normally, but the hardware uses slower fallback emulation pulses.

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [algovista #23](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 5. [clausia #24](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Identify a valid execution mode*

Which option is an official job-execution mode in Qiskit Runtime?

a) *stream*  
b) *batch*  
c) *parallel*  
d) *single-shot*

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [clausia #24](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 6. [clausia #25](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Opening a dedicated session*

Choose the call that opens a **dedicated** session on a backend stored in `backend`:

a)

```python
from qiskit_ibm_runtime import Session
session = Session(backend=backend)
```

b)

```python
session = Session(backend, mode="dedicated")
```

c)

```python
session = Session(backend); session.mode = "dedicated"
```

d)

```python
with Session(backend, dedicated=True) as session:
    ...
```

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #25](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 7. [clausia #26](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Limiting how long a **Batch** session stays open*

When you construct a `Batch` to run jobs in batch mode, which **keyword argument** lets you set the maximum time before the batch is forcibly closed?

a. `timeout`  
b. `max_time`  
c. `session_time`  
d. `runtime_limit`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [clausia #26](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 8. [clausia #27](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Batch-mode behaviour*

In *batch* mode, how are jobs queued?

a) Each job executes immediately in arrival order.  
b) Jobs wait and execute **only after you close the session or it times out**.  
c) Jobs are distributed across multiple backends simultaneously.  
d) Jobs execute one-by-one but with elevated priority.

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [clausia #27](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 9. [clausia #28](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Running a circuit with the Sampler primitive in a session*

Which snippet correctly runs a list `circuits` on real hardware using **Sampler** inside an existing session `session`?

a)

```python
from qiskit_ibm_runtime import Sampler
sampler = Sampler(session=session)
job = sampler.run(circuits)
```

b)

```python
sampler = Sampler()
job = session.run(sampler, circuits)
```

c)

```python
job = Sampler.run(session, circuits)
```

d)

```python
job = session.sampler(circuits)
```

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #28](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 10. [clausia #30](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Closing a session*

What is the recommended way to end a session so that *batch* jobs are released to the queue?

a) `session.stop()`  
b) Exiting the `with Session(...):` context block  
c) `session.end_batch()`  
d) You do not need to do anything; sessions close automatically after 24 h

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [clausia #30](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 11. [MarcoBarroca #3](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

**Select 3.**

A usage report is being interpreted for Runtime work. Which statements are accurate?

- [ ] **A.** Batch usage is local Python CPU time.
- [ ] **B.** `batch.usage_time()` is the documented SDK call.
- [ ] **C.** The API token changes how usage time is computed.
- [ ] **D.** Single-job usage is quantum time charged for processing that job.
- [ ] **E.** Session usage is tied to the active session workload window under Runtime accounting.
- [ ] **F.** Reported details data can include a `usage_time` field.

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #3](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 12. [MarcoBarroca #10](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A Runtime session is being opened for hardware work. Which value belongs in the session setup rather than in circuit construction or authentication?

- **A.** The account password in plain text
- **B.** An infinite maximum lifetime
- **C.** The backend or execution mode
- **D.** The circuit's qubit count

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [MarcoBarroca #10](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 13. [MarcoBarroca #19](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which object category can be passed as `mode` when constructing a `SamplerV2` primitive?

- **A.** A raw Pauli string such as `'ZZ'`
- **B.** A backend, session, or batch execution context
- **C.** A `QuantumCircuit` to be sampled
- **D.** A `SparsePauliOp` observable

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [MarcoBarroca #19](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 14. [MarcoBarroca #41](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A session object has been created but no workload has started yet. Which lifecycle statement is accurate?

- **A.** The session has an unlimited active lifetime.
- **B.** The session can run only Sampler jobs or only Estimator jobs, never both.
- **C.** The session always closes exactly 10 minutes after construction.
- **D.** The session starts when its first job starts.

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #41](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 15. [MarcoBarroca #56](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A Runtime workload has classical orchestration plus QPU execution. Which processing statement is accurate?

- **A.** Some classical job processing can overlap, while QPU execution is still governed by hardware scheduling.
- **B.** Runtime jobs skip classical processing entirely.
- **C.** A QPU executes independent jobs simultaneously by putting jobs in superposition.
- **D.** Putting every circuit into one huge job is always the fastest strategy.

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #56](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 16. [MarcoBarroca #63](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Several Runtime jobs appear in a dashboard with the same `session_id`. What does that ID indicate?

- **A.** Those jobs are automatically first in the backend queue.
- **B.** Those jobs are associated with the same Runtime session.
- **C.** Those jobs must have used the same physical qubit layout.
- **D.** Those jobs share the user's API token.

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [MarcoBarroca #63](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 17. [MarcoBarroca #65](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which line retrieves a backend object from a `QiskitRuntimeService` named `service`?

- **A.** `backend = service.fetch_backend("ibm_test_backend")`
- **B.** `backend = service.get("ibm_test_backend")`
- **C.** `backend = "ibm_test_backend"`
- **D.** `backend = service.backend("ibm_test_backend")`

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #65](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 18. [MarcoBarroca #67](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which setting category is used to bound how much Runtime quantum execution time a workload can consume?

- **A.** Only default transpiler settings
- **B.** Execution-time limits where supported
- **C.** More shots and more iterations
- **D.** Long sleeps between submitted jobs

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [MarcoBarroca #67](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 19. [Q-Bees #16](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You are using the IBM Quantum runtime to run an iterative algorithm with many calls to Estimator. What is the main advantage of using a single long-lived Session for these calls instead of creating a new session each time?

- A
Multiple sessions are always faster because they parallelize across different backends

- B
A single session guarantees zero queue time for all jobs

- C
Sessions only affect billing, not technical behavior

- D
A single session groups related jobs, reduces overhead, and can provide priority handling compared to many short sessions

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [Q-Bees #16](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 20. [Q-Bees #19](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You are building an intermediate-level Qiskit application and want to structure your workflow using primitives and the runtime. Which of the following is a recommended design pattern?

- A
Use primitives like Sampler and Estimator inside a runtime Session to implement algorithm-specific logic on the client side

- B
Use backend.run for everything and ignore primitives, since they add unnecessary complexity

- C
Implement your entire algorithm as a monolithic runtime program to avoid client-side iteration

- D
Avoid sessions and submit each primitive call as an isolated job to maximize flexibility

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [Q-Bees #19](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 21. [Q-Bees #21](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

In Qiskit which description best characterizes an "execution mode" for running circuits on backends?

- A
It is a hardware parameter describing qubit coherence time

- B
It refers to how jobs are scheduled and run, such as synchronous versus asynchronous interactions with the backend

- C
It is a setting that adjusts optimization level during transpilation

- D
It defines the measurement basis used for all qubits in a circuit

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [Q-Bees #21](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---


---

## 오답 정리

| 문항 | 내가 고른 답 | 정답 | 왜 틀렸나 |
| --- | --- | --- | --- |
| | | | |

## 이 토픽에서 반복해서 틀리는 것

- [ ]
