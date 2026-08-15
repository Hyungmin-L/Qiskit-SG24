# Week 9 — Section B: 기출 문제

> syllabus 토픽: **Qiskit IBM Runtime REST API**
> Advocate가 만든 practice exam 4종에서 이 토픽에 해당하는 문항만 추린 것. 총 **3문항**.

출처별 문항 수: algovista 1, clausia 1, MarcoBarroca 1

풀이 방법 — 정답은 접혀 있으니 **먼저 풀고** 펼칠 것. 틀린 문항은 번호를 아래 오답 목록에
적고, 이유를 한 줄로 남긴다. 문제 자체보다 그 한 줄이 시험 직전에 쓸모 있다.

---


### 1. [algovista #20](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

When interacting directly with the IBM Quantum cloud infrastructure via its REST API, which header field must be included to authenticate your requests securely?

A. `Authorization: Bearer <API_TOKEN>`

B. `X-IAM-Key: <KEY>`

C. `Content-Type: application/qasm`

D. `Service-CRN: <CRN_ID>`

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [algovista #20](https://github.com/algovista-collab/qiskit_v2_study_materials/blob/main/25_Practice_Questions.md)

</details>

---

### 2. [clausia #50](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

*Qiskit IBM Runtime REST API – running a job*

According to the official REST spec, which HTTP verb and endpoint starts a new Runtime job?

a) `GET /v1/jobs`  
b) `POST /v1/jobs`  
c) `PUT /v1/job/run`  
d) `PATCH /v1/jobs/{id}`

<details>
<summary>정답</summary>

**B**

해설은 출처 원문 참고: [clausia #50](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md)

</details>

---

### 3. [MarcoBarroca #48](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

A direct Runtime REST request is made outside the Python SDK. Where should the API token be placed?

- **A.** In the HTTP `Authorization` header as a Bearer token
- **B.** In the URL query string
- **C.** In the JSON body under `token`
- **D.** In an HTTP `CONNECT` header

<details>
<summary>정답</summary>

**A**

해설은 출처 원문 참고: [MarcoBarroca #48](https://github.com/MarcoBarroca/qiskit-v2-mock-exam/blob/main/notebooks/qiskit_v2_mock_exam.ipynb)

</details>

---


---

## 오답 정리

| 문항 | 내가 고른 답 | 정답 | 왜 틀렸나 |
| --- | --- | --- | --- |
| | | | |

## 이 토픽에서 반복해서 틀리는 것

- [ ]
