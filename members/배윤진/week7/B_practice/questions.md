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

`QiskitRuntimeService.jobs()`의 필터는 **전부 키워드 인자**다 (qiskit-ibm-runtime 0.49.0 시그니처):

```python
service.jobs(limit=10, skip=0, backend_name=None, pending=None, program_id=None,
             instance=None, job_tags=None, session_id=None,
             created_after=None, created_before=None, descending=True)
```

`backend_name=`과 `session_id=`를 같이 주면 둘 다 만족하는 job만 온다. D_exercises 1번 [18]의
`service.jobs(created_after=...)`가 같은 패턴.

| 보기 | 왜 틀림 |
| --- | --- |
| B) `backend.jobs(...)` | `IBMBackend`에 `jobs` 메서드 **없음** (`hasattr` → False). job 조회는 항상 `service`에서 |
| C) `Session.from_id(...).get_all_jobs()` | `Session.from_id()`는 **있지만** `get_all_jobs()`는 **없음**. 절반만 맞는 함정 |
| D) `.history(...)` | `IBMBackend`에 `history` **없음** |

주의: `limit` 기본값이 **10**. "historical list 전부"가 필요하면 `limit=None`을 같이 줘야 한다.

출처: [algovista #18](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

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

`RuntimeJobV2.wait_for_final_state(timeout=None, poll_interval=None) -> None` —
최종 상태(`DONE`/`ERROR`/`CANCELLED`)가 될 때까지 API를 **주기적으로 polling**한다.
`timeout` 초 안에 안 끝나면 `RuntimeJobTimeoutError`. 기본 poll 간격은 일반 job 0.5초, session job 0.1초.
**반환값은 없다** — 결과는 따로 `job.result()`로.

**클라우드 `RuntimeJobV2`에만 있고 로컬 `PrimitiveJob`에는 없다.** D_exercises 1번이 전부 로컬이라
이 함수가 안 보인 것. 1번 [23]의 `while not job.in_final_state(): ... time.sleep(0.1)` 루프가 이걸
손으로 짠 버전이다.

| 보기 | 왜 틀림 |
| --- | --- |
| A) `job.status()` | 지금 상태를 **한 번** 알려줄 뿐. 추적하려면 직접 루프를 돌려야 함 |
| C) `job.result(stream=True)` | `stream` 인자 **없음**. 실제 시그니처는 `result(timeout, decoder, poll_interval)` |
| D) `runtime.monitor(job)` | **존재하지 않음.** Qiskit 1.x 이전 `job_monitor()`를 떠올리게 하는 함정 |

문제 문구의 "print updates"는 과장 — `wait_for_final_state()`는 기다리기만 하고 출력은 안 한다.

출처: [algovista #22](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

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

#1과 같은 함수. `service.jobs(session_id=sid)` — 필터는 키워드 인자.

| 보기 | 왜 틀림 |
| --- | --- |
| B) `service.job(sid)` | `job` (**단수**)는 `job(self, job_id: str) -> RuntimeJobV2` — job ID 하나로 job **하나**. session ID를 넣으면 그런 job 없다고 에러. D_exercises 1번 [20]의 `service.job(job_id)`가 이 용법 |
| C) `filter_session=` | **존재하지 않는 인자** → `TypeError` |
| D) `.filter(session=sid)` | `jobs()`는 **일반 Python list** 반환. list에 `.filter()` 없음 → `AttributeError`. pandas/ORM 스타일 함정 |

역시 `limit=10` 기본값 주의. session에 job이 10개 넘으면 `limit=None` 필요.

출처: [clausia #43](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

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

enum 값 자체가 답이다:

```
QUEUED     'job is queued'
RUNNING    'job is actively running'
CANCELLED  'job has been cancelled'
DONE       'job has successfully run'   ←
ERROR      'job incurred error'
```

종료 상태 셋(`DONE`/`ERROR`/`CANCELLED`) 중 **유일한 성공**이 `DONE`. 이 상태에서만 `job.result()`가
예외 없이 결과를 돌려준다. D_exercises 1번 [23]의 `if job.done():`이 정확히 `status() == DONE`과 같은 뜻.

| 보기 | 왜 틀림 |
| --- | --- |
| A) 아직 대기 중 | 그건 `QUEUED` |
| C) 사용자가 취소 | 그건 `CANCELLED` (2026-09-05에 cancel한 유령 job 9개가 지금 이 상태) |
| D) 에러로 실패 | 그건 `ERROR`. 이때 `result()`는 예외를 던지고 원인은 `error_message()`로 |

"끝남"과 "성공"을 구분하라는 게 요점 — D_exercises 1번 연습문제 2(`done()` vs `in_final_state()`)와 짝.
참고: 클라우드 `RuntimeJobV2.status()`는 enum이 아니라 **문자열 `"DONE"`**을 돌려준다. 뜻은 같다.

출처: [clausia #44](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

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

`job.result()`는 job이 최종 상태가 될 때까지 **실행을 막고(block)** 기다렸다가 `PrimitiveResult`를 돌려준다.
D_exercises 1번 [24] 표에 "**Blocks execution** until the job is in a final state"라고 명시.
시그니처는 `result(timeout=None, decoder=None, poll_interval=None)` — `timeout`을 주면
`RuntimeJobMaxTimeoutError`로 끊을 수 있다 (week4 때 17분 멈춘 셀이 바로 이 timeout 없는 `result()`).

| 보기 | 왜 틀림 |
| --- | --- |
| B) `queue_position()` | **0.49.0에는 존재하지 않음** (`dir(RuntimeJobV2)`에 없음, 호출 시 `AttributeError` 확인). D_exercises 1번 [24] 표에 "cloud-only"로 적혀 있지만 그건 구버전 기준 — 원본 노트북의 오류 |
| C) `metrics()` | 존재함. 하지만 타임스탬프·사용량 등 **지표 dict**를 돌려주지 결과가 아니고, block도 안 함 |
| D) `backend()` | 존재함. **backend 객체**를 돌려줌. 결과와 무관 |

`wait_for_final_state()`(#2)도 block하지만 **반환값이 없다**. "block + 결과 반환"은 `result()`뿐.

출처: [clausia #45](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

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

**이건 V1 Sampler 문제다.** `result.quasi_dists`는 V1 `SamplerResult`의 속성이고, V2 `PrimitiveResult`에는
**없다** (`hasattr(PrimitiveResult, "quasi_dists")` → False). V2는 `result[0].data.meas.get_counts()`로 간다.
시험이 v2.X 기준이라 나올 가능성은 낮지만, `QuasiDistribution` 클래스 자체는 `qiskit.result`에 아직 있다.

`nearest_probability_distribution()`: quasi-distribution은 error mitigation 때문에 **음수 확률**이나
합이 1이 아닌 값을 가질 수 있다. 이 메서드는 L2 거리 기준 가장 가까운 유효 확률분포로 사영한다. 실측:

```python
QuasiDistribution({0: 1.2, 3: -0.2}).nearest_probability_distribution()  → {0: 1.0}
```

| 보기 | 왜 틀림 |
| --- | --- |
| B) `to_counts()` | **존재하지 않음** |
| C) `binary_probabilities()` | **존재하지만** 하는 일이 다름 — int 키를 이진 문자열 키로 바꿀 뿐 (`{0: 1.2, 3: -0.2}` → `{'00': 1.2, '11': -0.2}`). 음수 그대로, 합도 그대로. 유효 분포로 만들지 않는다 |
| D) `normalize()` | **존재하지 않음** |

출처: [clausia #46](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

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

D_exercises 1번 [14][16]이 정확히 이 코드:

```python
from qiskit_ibm_runtime import RuntimeEncoder, RuntimeDecoder
json.dump(result, f, cls=RuntimeEncoder)
loaded = json.load(f, cls=RuntimeDecoder)
```

일반 `json`은 `BitArray`·`ndarray`·`PrimitiveResult`를 직렬화 못 한다. `RuntimeEncoder`는 이들을
`{"__type__": ..., "__value__": ...}` 형태로 바꾸고 (`sampler_result.json` 열어보면 보임), `RuntimeDecoder`가 복원한다.

| 보기 | 왜 틀림 |
| --- | --- |
| B) `ResultEncoder` from `qiskit_ibm_runtime` | **존재하지 않음** (`hasattr` → False). 이름만 그럴듯 |
| C) `ResultEncoder` from `qiskit.result` | **존재하지 않음**. `qiskit.result`에는 `Result`, `Counts`, `QuasiDistribution` 등만 있음 |
| D) `pickle as RuntimeEncoder` | `pickle`은 `json.dump(cls=...)`에 못 넣음 — `cls`는 `JSONEncoder` 서브클래스여야 함. 애초에 문제가 "with Python's `json` module"이라고 못박음 |

출처: [clausia #47](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

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

**D** — 단, **키 폭 기준으로만** 정답.

문제의 요점: counts 딕셔너리의 **키 길이 = `ClassicalRegister` 비트 수**. 여기선 `ClassicalRegister(2, 'c')`이므로
키는 무조건 2글자. 보기 중 2글자 키는 D뿐이다.

| 보기 | 왜 틀림 |
| --- | --- |
| A) `{'000': 1024}` | 3글자 — 레지스터가 2비트인데 3비트 키는 나올 수 없음 |
| B) `{'0': 512, '1': 512}` | 1글자 — 같은 이유 |
| C) `NameError` | `while_loop`는 `QuantumCircuit`의 **메서드**(`qc.while_loop(...)`)라 이름 조회 자체가 안 일어남. 문법도 맞음 |

**⚠️ 이 문제는 실제로 돌리면 무한 루프다.** 2026-09-19에 Aer로 실행 → 60초 타임아웃. 이유:
`h(0); measure(0,0)`에서 `c[0]==1`이 나오면 q0는 이미 |1⟩로 붕괴됐고, 루프 안에서 q0에 아무 gate 없이
`measure(0,0)`만 다시 하니 영원히 1 → `while_loop((c[0], 1))` 탈출 불가. 게다가 D의 `'10'`(c1=1, c0=0)은
c0가 1→0으로 바뀌어야 나오는데 그럴 경로가 없다. 출제자가 안 돌려본 문제. **시험에선 키 폭만 보고 D를 고르면 되고,
숫자는 신경 쓰지 말 것.**

출처: [MarcoBarroca #21](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

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

`RuntimeJobV2.error_message()` — 실패한 job의 에러 텍스트. **클라우드 전용**이며 로컬 `PrimitiveJob`에는 없다
(로컬은 `result()` 호출 시 예외가 바로 터지므로 나중에 조회할 필요가 없음). 짝인 `job.errored()`는 실패 여부 bool.
D_exercises 1번 연습문제 3이 같은 내용.

| 보기 | 왜 틀림 |
| --- | --- |
| A) `exception_text()` | **존재하지 않음** |
| C) `get_error()` | **존재하지 않음** |
| D) `retrieve_error()` | **존재하지 않음** |

`dir(RuntimeJobV2)`에 있는 에러 관련 이름은 `ERROR`(상태 상수), `errored`, `error_message` 셋뿐.

출처: [MarcoBarroca #39](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

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

`service.jobs()`는 **인자 없이도** 동작하고(최근 10개, `descending=True`), 필요하면 `backend_name=`, `pending=`,
`created_after=`/`created_before=`, `session_id=`, `job_tags=`, `program_id=` 등을 **선택적으로** 얹는다.
#1 #3의 시그니처 참고. D_exercises 1번 [18]에서 `created_after=`만 주고 호출한 것이 예.

| 보기 | 왜 틀림 |
| --- | --- |
| A) `service.backend().jobs()` | `IBMBackend`에 `jobs()` **없음**. 그리고 `service.backend()`는 이름 인자가 필수라 `()`로 못 부름 |
| C) 모든 필터를 다 줘야만 | 전부 `None` 기본값 — **하나도 안 줘도 됨** |
| D) 하드코딩된 30일 | 기간 제한은 `created_after`/`created_before`로 **호출자가** 정함. 기본은 기간 무제한, 개수만 `limit=10` |

주의: 문제 보기 B의 "status" 필터는 정확히는 `pending=True/False` (대기·실행 중 vs 종료)다. 상태 이름으로 필터하는 인자는 없다.

출처: [MarcoBarroca #47](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

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

job은 제출되는 순간 **IBM 서버에 기록**되고, 결과도 서버에 저장된다. 로컬 Python 객체는 그 기록을 가리키는
handle일 뿐이다. 그래서 프로세스가 죽어도 **job ID + 계정**만 있으면 어디서든 다시 꺼낼 수 있다:

```python
service = QiskitRuntimeService()
job = service.job("d6tp2maf84ks73ddff4g")   # 2026-03에 돌린 job
result = job.result()
```

D_exercises 1번 [20]이 정확히 이 시연 — 6개월 전 job을 ID로 다시 가져온다. 단 "retention limits"가 붙는 이유:
서버 보관 기간이 있고, 다른 인스턴스의 job은 안 보인다 (week4 때 EU/US 인스턴스 나눠 조회했던 것).

| 보기 | 왜 틀림 |
| --- | --- |
| B) `job.save()` 필요 | **`save()` 메서드 없음** (`hasattr` → False). 저장은 제출 시 서버가 자동으로 함 |
| C) 원래 Python 객체로만 | 정반대. handle은 `service.job(id)`로 얼마든지 다시 만들 수 있음 |
| D) REST만 가능 | `service.job()` / `service.jobs()`가 SDK 안에서 REST를 대신 호출해 줌. week9 REST API 토픽과 헷갈리게 하는 함정 |

출처: [MarcoBarroca #52](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

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

`RuntimeJobV2.cancel() -> None` — 서버에 취소 요청. 성공하면 상태가 `CANCELLED`. 취소 불가능한 상태(이미 끝남 등)면
`RuntimeInvalidStateError`, 그 외 실패면 `IBMRuntimeError`. 2026-09-05에 큐에 갇힌 job 9개를 이걸로 정리했다.

| 보기 | 왜 틀림 |
| --- | --- |
| A) `in_final_state()` | **조회**. 끝났는지 물어볼 뿐 아무것도 안 바꿈 |
| C) `complete()` | **존재하지 않음** |
| D) `done()` | **조회**. 성공했는지 물어볼 뿐 |

요점: 상태를 **바꾸는** 메서드는 `cancel()` 하나. 나머지 `status/done/running/cancelled/in_final_state`는 전부 읽기 전용.

출처: [MarcoBarroca #55](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

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

정석 패턴 — session 안에서 여러 job을 던지고, **반환된 job handle을 모아두고**, `status()`로 주기적으로 확인하며
실패한 것은 `errored()` / `error_message()`로 처리:

```python
with Session(backend=backend) as session:
    sampler = Sampler(mode=session)
    jobs = [sampler.run([(isa, p)]) for p in param_sets]   # handle 수집
for j in jobs:
    if j.errored(): print(j.job_id(), j.error_message())
```

| 보기 | 왜 틀림 |
| --- | --- |
| A) 추적 안 함 | runtime은 완료를 **보장하지 않음**. `ERROR`/`CANCELLED`가 종료 상태로 있는 이유. 2026-09 사건처럼 큐에서 영영 안 나오기도 함 |
| C) `run(...).result()`만 | handle을 버리면 **어느 job이 실패했는지 모르고**, 하나가 막히면 뒤가 다 멈춤 (`result()`는 block, #5). session의 이점(job들을 병렬로 던져두기)도 사라짐 |
| D) `backend.run()` | **구식**. v2.X는 primitive(`Sampler`/`Estimator`)로 실행. `backend.run()`은 IBM Runtime에서 지원 종료됨 |

출처: [Q-Bees #11](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

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

job 객체의 상태 메서드로 polling — `status()`, `in_final_state()`, `done()`, 또는 클라우드에서 `wait_for_final_state()`(#2).
D_exercises 1번 [23]의 `while not job.in_final_state(): ... time.sleep(0.1)`이 이 패턴.

| 보기 | 왜 틀림 |
| --- | --- |
| A) 재제출 반복 | 큐에 같은 job이 쌓이고 크레딧만 낭비. 원래 job은 그대로 돌아감 |
| B) 이메일 대기 | 그런 알림 없음. job 객체가 있는데 무시할 이유가 없음 |
| C) 백엔드 내부 로그 | 접근 불가. `job.logs()`는 있지만 그건 job 자체의 로그지 스케줄러가 아님 |

문제의 "job monitor utility"는 옛 `qiskit.tools.job_monitor` — **v2.X에는 없다.** 지금은 상태 메서드로 직접 하거나 `wait_for_final_state()`.

출처: [Q-Bees #22](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

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

`job.cancel()` (#12). 큐에 있든 실행 중이든 서버에 중단을 요청하는 유일한 정식 경로. 실행 중이던 job은 QPU 시간을
더 안 쓰게 되고, 큐에 있던 job은 빠진다.

| 보기 | 왜 틀림 |
| --- | --- |
| A) 백엔드 전원 차단 | 공용 QPU. 사용자에게 그런 권한 없음 |
| B) 빈 job 제출 | job은 서로 **독립**. 새 job이 기존 job을 덮어쓰지 않고 그냥 큐 뒤에 하나 더 붙음 |
| D) Python 세션 종료 | #11의 정반대 — job은 **서버에** 있으므로 로컬 프로세스가 죽어도 계속 돈다. 2026-09-05에 발견한 유령 job들이 정확히 이 경우 (한 달 전 노트북은 닫혔는데 job은 `QUEUED`로 남아 있었음) |

출처: [Q-Bees #23](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

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

두 가지 방법이 다 정답에 들어 있다:
1. **job ID 보관** → `service.job(job_id)` (D_exercises 1번 [20])
2. **job history** → `service.jobs(...)` 로 필터 조회 (#1 #3 #10, D_exercises 1번 [18])

결과 자체를 파일로 남기고 싶으면 `RuntimeEncoder`로 JSON 저장(#7, D_exercises 1번 [14])이 세 번째 방법.

| 보기 | 왜 틀림 |
| --- | --- |
| B) 회로 소스 복사 | 서버는 회로 내용으로 job을 찾아주지 않음. 같은 회로를 100번 던지면 job 100개 |
| C) 스크린샷 | 데이터가 아님 |
| D) 상태 메시지 암기 | `"DONE"`은 수천 개 job이 공유하는 값. 식별자가 아님 |

식별자는 **job ID 하나뿐**. 나머지(회로·상태·backend 이름)는 전부 여러 job이 공유할 수 있다.

출처: [Q-Bees #24](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb)

</details>

---


---

## 오답 정리

| 문항 | 내가 고른 답 | 정답 | 왜 틀렸나 |
| --- | --- | --- | --- |
| | | | |

## 이 토픽에서 반복해서 틀리는 것

- [ ]
