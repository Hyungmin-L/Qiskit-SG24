# Week 7 — Retrieve and analyze the results of quantum circuits

> **7주차 숙제.** 이 내용은 **8주차 미팅**에서 다룸.
> syllabus 토픽: *Retrieve and analyze the results of quantum circuits*

## A. 공식 문서 ([`A_docs/`](A_docs/))

IBM [Qiskit 공식 가이드](https://github.com/Qiskit/documentation/tree/main/docs/guides) 원본.
직접 실행하며 공부하고, **원본 셀은 수정하지 않고 새 markdown 셀로만** 메모를 붙인다.

```markdown
> **📝 내 메모** — 여기에 적기
```

커널은 `Python (qiskit-sg24)` 선택.

| 파일 | 형식 | 읽음 | 실행 |
| --- | --- | :--: | :--: |
| [`monitor-job.ipynb`](A_docs/monitor-job.ipynb) | notebook | [ ] | [ ] |
| [`save-circuits.ipynb`](A_docs/save-circuits.ipynb) | notebook | [ ] | [ ] |
| [`save-jobs.ipynb`](A_docs/save-jobs.ipynb) | notebook | [ ] | [ ] |

## B. 기출 문제 ([`B_practice/`](B_practice/))

Advocate practice exam 4종에서 이 토픽 문항만 추린 것 — [**16문항**](B_practice/questions.md) (algovista 2, clausia 5, MarcoBarroca 5, Q-Bees 4).
풀고 **틀린 것과 그 이유**를 기록한다. 출처 링크와 원본 문제 번호를 남길 것.

- [ ] 풀이 완료
- [ ] 오답 정리 → 아래 "약점"에 반영

## C. 퀴즈 ([`C_quiz/`](C_quiz/))

Claude가 만든 문제. 정답은 `<details>`로 접혀 있으니 먼저 풀고 펼칠 것.
출력 맞히기 문제의 정답은 실제 실행으로 확정된 값이다.

- [ ] 풀이 완료

## D. 스터디 공용 실습 노트북 ([`D_exercises/`](D_exercises/))

출처: [kibrahim757/qiskit_2x_certification_exam_tutorial](https://github.com/kibrahim757/qiskit_2x_certification_exam_tutorial)
→ `Section_7_Retrieve_Analyze_Results/`. 원본 셀은 수정하지 않았고, 커널만 `qiskit-sg24`로 바꾼 뒤
맨 위에 메모 셀 + `.env` 로더 셀만 추가함. **끝까지 실행해서 출력을 박아뒀다** (에러 0).

| 파일 | 내용 | 실행 |
| --- | --- | :--: |
| [`1_Retrieve_Experiment_Results.ipynb`](D_exercises/1_Retrieve_Experiment_Results.ipynb) | Task 7.1 — `PubResult`/`DataBin`/`BitArray`, 결과 JSON 저장·복원, job 조회, job 상태 폴링 | ✅ 75초 |
| [`2_Monitor_Jobs.ipynb`](D_exercises/2_Monitor_Jobs.ipynb) | Task 7.2 — `Provider`/`BackendV2`/`Job` 직접 구현, `Target`, `JobStatus` 열거형 | ✅ 13초 |
| [`1_..._ko.ipynb`](D_exercises/1_Retrieve_Experiment_Results_ko.ipynb) | 위 한글 번역본 + **오답 해설** | ✅ 71초 |
| [`2_..._ko.ipynb`](D_exercises/2_Monitor_Jobs_ko.ipynb) | 위 한글 번역본 + **오답 해설** | ✅ 10초 |
| `sampler_result.json` | 1번 셀 14가 생성하는 파일 (업스트림에도 있음) | — |

`_ko` 번역본은 천가희 방식 — 코드는 동일, 주석·출력 문자열·설명만 번역, Qiskit 용어는 영어 유지.
연습문제 정답 `<details>` 안에 보기별 오답 해설을 넣었고, 근거는 전부 노트북 셀 번호나 `dir()` 실측으로 달았다.
1번 원본에 직접 추가한 셀 [4](결과 계층 정리)와 [34] 메모는 번역본에도 살려뒀다.

week4와 달리 **Aer 사본이 필요 없다.** 1번은 `AerSimulator` + `BackendSamplerV2`, 2번은 전부 로컬 클래스라
실기기를 안 쓴다. 1번의 클라우드 셀 [17][19]는 `try/except`로 감싸져 있고, 완료된 옛날 job을 *조회*만 하므로
QPU 할당량 0이어도 동작한다 (2026-03 job 조회 성공). 75초 중 대부분은 [19]가 job 100개 status를 하나씩 묻는 시간.

주의할 것:
- 1번 [22] `EfficientSU2(...)` 클래스는 **Qiskit 2.1에서 deprecated** (3.0 제거 예정) — `efficient_su2()` 함수를 쓰라는 경고가 뜬다. 시험 포인트.
- 2번은 `JobV1`, `Result.from_dict`, `Options` 등 V1 API를 쓴다. 시험이 V2 중심이라 "이런 게 있었다" 수준으로만.

## 약점

이번 주에 계속 헷갈린 것. 지워지 말고 남겨둘 것 — 시험 직전에 이 줄들만 다시 봄.

- [ ]

## 미팅에서 물어볼 것

- [ ]
