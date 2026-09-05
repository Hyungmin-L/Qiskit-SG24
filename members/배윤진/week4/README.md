# Week 4 — Run quantum circuits

> **4주차 숙제.** 이 내용은 **5주차 미팅**에서 다룸.
> syllabus 토픽: *Run quantum circuits*

## A. 공식 문서 ([`A_docs/`](A_docs/))

IBM [Qiskit 공식 가이드](https://github.com/Qiskit/documentation/tree/main/docs/guides) 원본.
직접 실행하며 공부하고, **원본 셀은 수정하지 않고 새 markdown 셀로만** 메모를 붙인다.

```markdown
> **📝 내 메모** — 여기에 적기
```

커널은 `Python (qiskit-sg24)` 선택.

| 파일 | 형식 | 읽음 | 실행 |
| --- | --- | :--: | :--: |
| [`choose-execution-mode.mdx`](A_docs/choose-execution-mode.mdx) | 읽기 자료 | [ ] | — |
| [`execution-modes-faq.mdx`](A_docs/execution-modes-faq.mdx) | 읽기 자료 | [ ] | — |
| [`execution-modes.mdx`](A_docs/execution-modes.mdx) | 읽기 자료 | [ ] | — |
| [`get-started-with-estimator.ipynb`](A_docs/get-started-with-estimator.ipynb) | notebook | [ ] | [ ] |
| [`get-started-with-sampler.ipynb`](A_docs/get-started-with-sampler.ipynb) | notebook | [ ] | [ ] |
| [`primitives.ipynb`](A_docs/primitives.ipynb) | notebook | [ ] | [ ] |

## B. 기출 문제 ([`B_practice/`](B_practice/))

Advocate practice exam 4종에서 이 토픽 문항만 추린 것 — [**21문항**](B_practice/questions.md) (algovista 4, clausia 6, MarcoBarroca 8, Q-Bees 3).
풀고 **틀린 것과 그 이유**를 기록한다. 출처 링크와 원본 문제 번호를 남길 것.

- [ ] 풀이 완료
- [ ] 오답 정리 → 아래 "약점"에 반영

## C. 퀴즈 ([`C_quiz/`](C_quiz/))

Claude가 만든 문제. 정답은 `<details>`로 접혀 있으니 먼저 풀고 펼칠 것.
출력 맞히기 문제의 정답은 실제 실행으로 확정된 값이다.

- [ ] 풀이 완료

## D. 스터디 공용 실습 노트북 ([`D_exercises/`](D_exercises/))

그룹의 다른 멤버들(천가희·임형민·김정환)이 올린 노트북과 **같은 출처**:
[kibrahim757/qiskit_2x_certification_exam_tutorial](https://github.com/kibrahim757/qiskit_2x_certification_exam_tutorial)
→ `Section_4_Run_Quantum_Circuits/`. 원본 2개는 **셀을 하나도 수정하지 않았고**, 커널만
`qiskit-sg24`로 바꾼 뒤 맨 위에 메모 셀 + 자격증명 로딩 셀만 추가함.
`_aer` 사본 2개는 로컬 시뮬레이터로 돌도록 고친 것 (아래 표 참고).

| 파일 | 내용 | 실행 |
| --- | --- | :--: |
| [`1_Demonstrate_Execution_Modes.ipynb`](D_exercises/1_Demonstrate_Execution_Modes.ipynb) | Task 4.1 — job / session / batch, batch 실행·모니터링 | 실기기 |
| [`2_Demonstrate_Circuit_Running_RealHW.ipynb`](D_exercises/2_Demonstrate_Circuit_Running_RealHW.ipynb) | Task 4.2 — 실제 하드웨어 실행, primitive 입출력·broadcasting, session | 실기기 |
| [`1_..._aer.ipynb`](D_exercises/1_Demonstrate_Execution_Modes_aer.ipynb) | 위 사본, 로컬 시뮬레이터 | ✅ 14.5초 |
| [`2_..._aer.ipynb`](D_exercises/2_Demonstrate_Circuit_Running_RealHW_aer.ipynb) | 위 사본, 로컬 시뮬레이터 | ✅ 30.4초 |

### Aer 사본 (발표용) ← 이걸 쓴다

`_aer` 사본은 **끝까지 실행해서 출력을 박아뒀다.** IBM 계정·토큰·네트워크가 전혀 필요 없고
큐 대기도 없다. 바뀐 셀에는 전부 `[Aer 사본]` 주석이 달려 있다.

원본 대비 바뀐 것:

| 위치 | 원본 | 사본 |
| --- | --- | --- |
| 백엔드 | `service.least_busy(operational=True, simulator=False)` | `AerSimulator()` |
| transpile 타겟 | 실기기 (120~156 qubit) | Aer — **이게 핵심**. 실기기 타겟이면 2-qubit 회로가 120-qubit으로 부풀어 시뮬레이션 불가 (2^120) |
| nb1 셀 20 | `SparsePauliOp("Z"*133)` | `SparsePauliOp("ZZ")` — 원본은 133-qubit 기기 기준 하드코딩이라 다른 기기에선 터짐 |
| nb1 셀 32 | `details['id']` | 로컬에선 `details()`가 `None` → 분기 처리 |
| nb1 셀 35 | `random_circuit(3, 3)` | `measure=True` 추가 — 원본은 측정이 없어 결과가 빈 `DataBin()` |
| 크레딧 경고 | "10~15초 소모" | 로컬이라 크레딧 안 씀 |

**nb1 셀 27은 일부러 에러가 난다** (닫힌 batch에 job 제출 → `IBMRuntimeError: The session is closed.`).
로컬 모드에서도 이 검증은 그대로 작동하므로 시연 포인트로 쓸 수 있다.

각 노트북 끝에 `## Practice Questions` 섹션이 있음.

### 자격증명 (원본 2개에만 해당 — `_aer` 사본은 불필요)

원본은 `QiskitRuntimeService()` + `least_busy(operational=True, simulator=False)`로
**실제 백엔드**를 잡는다. 토큰은 repo 루트 [`.env`](../../../.env)(gitignored)에 있고,
각 노트북 3번째 셀이 그걸 `os.environ`으로 올린다. `qiskit-ibm-runtime`은 저장된 계정
(`~/.qiskit/`)보다 환경변수를 **먼저** 보므로 원본 셀은 그대로 둬도 된다.

> 🚫 **2026-09-05 기준 실기기 실행 불가.** 두 인스턴스 모두 `usage_allocation_seconds = 0`
> (한도는 28일당 60초). 그래서 job이 큐에 들어가도 QPU에 올라가지 않는다. 2026-08-06 이후
> 제출한 job은 **하나도 실행된 적이 없고** 전부 `QUEUED`로 방치됐다 (2026-03월 job들은 정상
> 실행됨). 백엔드 자체는 `operational=True`라 겉보기엔 멀쩡하니 `pending_jobs`만 보고
> 판단하면 안 된다 — `service.usage()`를 확인할 것.
>
> 유령 job 9개는 2026-09-05에 cancel 완료. 할당량은 SNU 인스턴스 관리자 문의 사항.

```
QISKIT_IBM_CHANNEL=ibm_quantum_platform
QISKIT_IBM_TOKEN=<토큰>
QISKIT_IBM_INSTANCE=auto
```

- 인스턴스: `0_2025_SNU`, `0_2025_SNU-eu` (premium)
- 노트북을 열기 전에 `.env`가 있는지 확인. 없으면 로딩 셀이 `FileNotFoundError`를 낸다.
- ⚠️ **`.env`는 절대 커밋 금지.** 노출됐으면 IBM Quantum Platform에서 토큰 rotate.
- 실기기가 막히거나 큐가 길면 `backend`를 `AerSimulator()` / `GenericBackendV2`로 바꿀 것.
  단 session/batch 셀 상당수는 실기기 전용이라 시뮬레이터로는 시연이 반쪽이 된다.

## 약점

이번 주에 계속 헷갈린 것. 지워지 말고 남겨둘 것 — 시험 직전에 이 줄들만 다시 봄.

- [ ]

## 미팅에서 물어볼 것

- [ ]
