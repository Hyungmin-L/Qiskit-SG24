# Week 7 — Section B: 기출 문제

> syllabus 토픽: **Retrieve and analyze the results of quantum circuits**
> Advocate가 만든 practice exam 4종에서 이 토픽에 해당하는 문항만 추린 것. 총 **16문항**.

출처별 문항 수: algovista 2, clausia 5, MarcoBarroca 5, Q-Bees 4

풀이 방법 — 정답은 접혀 있으니 **먼저 풀고** 펼칠 것. 틀린 문항은 번호를 아래 오답 목록에
적고, 이유를 한 줄로 남긴다. 문제 자체보다 그 한 줄이 시험 직전에 쓸모 있다.

---


### 1. [algovista #18](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

Which code snippet correctly retrieves a historical list of jobs submitted to an IBM backend named 'ibm_brisbane' under a specific session ID?

A. `service.jobs(backend_name='ibm_brisbane', session_id=my_session_id)`

B. `backend.jobs(session_id=my_session_id)`

C. `Session.from_id(my_session_id).get_all_jobs()`

D. `service.get_backend('ibm_brisbane').history(my_session_id)`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [algovista #18](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 2. [algovista #22](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

Which function provides a straightforward way to dynamically track and print updates on a job's status while it is processing in the IBM Quantum hardware runtime queue?

A. `job.status()`

B. `job.wait_for_final_state()`

C. `job.result(stream=True)`

D. `runtime.monitor(job)`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [algovista #22](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 3. [clausia #43](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Filter jobs by session*

Which one-liner returns **all runtime jobs that belong to a given session** whose ID is stored in the variable `sid`?

a) `service.jobs(session_id=sid)`  
b) `service.job(sid)`  
c) `service.jobs(filter_session=sid)`  
d) `service.jobs().filter(session=sid)`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #43](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 4. [clausia #44](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Meaning of a final status*

If `job.status()` returns `JobStatus.DONE`, what does this indicate?

a) The job is still queued.  
b) The job has run successfully, and results can be retrieved.  
c) The job was cancelled by the user.  
d) The job failed with an error.

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [clausia #44](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 5. [clausia #45](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Blocking a call that returns results*

Which RuntimeJob method **blocks until the job finishes and then returns the result object**?

a) `job.result()`  
b) `job.queue_position()`  
c) `job.metrics()`  
d) `job.backend()`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #45](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 6. [clausia #46](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Convert a quasi-distribution to a proper probability distribution*

After a `Sampler` run, you have

```python
qpd = result.quasi_dists[0]  # a QuasiDistribution
```

Which call converts `qpd` to the *nearest* valid probability distribution?

a) `qpd.nearest_probability_distribution()`  
b) `qpd.to_counts()`  
c) `qpd.binary_probabilities()`  
d) `qpd.normalize()`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #46](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 7. [clausia #47](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Persist results to JSON for later analysis*

According to the IBM guide, which import pair should you use with Python’s `json` module when writing a Runtime result to disk?

a) `from qiskit_ibm_runtime import RuntimeEncoder, RuntimeDecoder`  
b) `from qiskit_ibm_runtime import ResultEncoder, ResultDecoder`  
c) `from qiskit.result import ResultEncoder, ResultDecoder`  
d) `import pickle as RuntimeEncoder`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [clausia #47](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 8. [MarcoBarroca #21](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

The circuit below stores samples in a two-bit classical register. Which count dictionary has the correct key width for this workload?

```python
q = QuantumRegister(2, 'q')
c = ClassicalRegister(2, 'c')
qc = QuantumCircuit(q, c)
qc.h(0)
qc.measure(0, 0)
with qc.while_loop((c[0], 1)):
    qc.x(1)
    qc.measure(1, 1)
    qc.measure(0, 0)
```

- **A.** `{'000': 1024}`
- **B.** `{'0': 512, '1': 512}`
- **C.** `NameError: name 'while_loop' is not defined`
- **D.** `{'00': 430, '10': 594}`

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [MarcoBarroca #21](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 9. [MarcoBarroca #39](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A submitted Runtime job failed. Which call retrieves the failure text from the job object?

- **A.** `job.exception_text()`
- **B.** `job.error_message()`
- **C.** `job.get_error()`
- **D.** `job.retrieve_error()`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [MarcoBarroca #39](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 10. [MarcoBarroca #47](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

Which use of `QiskitRuntimeService` is intended for listing previously submitted Runtime jobs?

- **A.** `service.backend().jobs()` only for a backend named `ibm_foo`
- **B.** `service.jobs()` with optional filters such as backend, status, or time
- **C.** `service.jobs()` only after every possible filter is supplied
- **D.** `service.jobs()` only for the hard-coded last 30 days

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [MarcoBarroca #47](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 11. [MarcoBarroca #52](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A notebook process exits after submitting a Runtime job. Later, the user still has the job ID and account access. What is the expected retrieval model?

- **A.** The job record can be looked up later through Runtime job/service APIs, subject to access and retention limits.
- **B.** The result is lost unless the original notebook called `job.save()` before exiting.
- **C.** The result can be read only from the Python object that originally submitted the job.
- **D.** The SDK cannot retrieve stored results; only direct REST calls can.

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #52](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 12. [MarcoBarroca #55](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A Runtime job is still active and should be stopped. Which line requests that action?

- **A.** `job.in_final_state()`
- **B.** `job.cancel()`
- **C.** `job.complete()`
- **D.** `job.done()`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [MarcoBarroca #55](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---

### 13. [Q-Bees #11](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You submit multiple jobs to a runtime session to run parameter sweeps using the Sampler primitive. You want to track all jobs and handle failures. Which Qiskit pattern best supports job management in this context?

- A
Avoid tracking jobs because runtime guarantees completion for all submitted tasks

- B
Use a runtime Session with Sampler, collecting the returned job handles, and periodically query their statuses via job.status()

- C
Use only blocking calls like result = sampler.run(...).result() and ignore job handles

- D
Use backend.run for all tasks and manually store job IDs in a list for later inspection

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [Q-Bees #11](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 14. [Q-Bees #22](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

After submitting a circuit to run on a hardware backend in Qiskit you receive a job object. Which method or approach best allows you to monitor the job’s progress until completion?

- A
Resubmit the same job repeatedly until results appear

- B
Ignore the job object and wait for an email notification from the provider

- C
Directly access the backend’s internal scheduler logs

- D
Use job status methods or a job monitor utility to poll the job’s state

<details>
<summary>정답</summary>

**D**

해설은 출처 원문 참고: [Q-Bees #22](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 15. [Q-Bees #23](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

You submitted a long-running experiment to a hardware backend in Qiskit but then realize a bug in your circuit. How can you responsibly stop the experiment to avoid wasting hardware time?

- A
Manually power down the backend if you have access

- B
Submit an empty job to overwrite the old one

- C
Use the job object’s cancel method (or equivalent) to request job cancellation

- D
Close your Python session and hope the job stops automatically

<details>
<summary>정답</summary>

**C**

해설은 출처 원문 참고: [Q-Bees #23](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---

### 16. [Q-Bees #24](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

In Qiskit which practice is most appropriate for saving a job so that you can retrieve its results later, even from a different session or machine?

- A
Store the job’s unique job ID or use built-in job history mechanisms provided by the account or provider

- B
Copy the circuit’s source code; the provider will automatically find the matching job

- C
Screenshot the output of the run call and reconstruct results manually

- D
Memorize the job’s status message, which is enough to reload it later

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [Q-Bees #24](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---


---

## 오답 정리

| 문항 | 내가 고른 답 | 정답 | 왜 틀렸나 |
| --- | --- | --- | --- |
| | | | |

## 이 토픽에서 반복해서 틀리는 것

- [ ]
