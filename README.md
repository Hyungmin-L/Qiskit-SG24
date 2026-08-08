# Qiskit-SG24

Study group **SG24** working toward the [IBM Certified Associate Developer — Quantum Computation using Qiskit v2.X](https://www.ibm.com/training/certification/ibm-certified-quantum-computation-using-qiskit-v2x-developer-associate-C9008400) certification, run as part of the Qiskit Advocate Program.

This repository is our shared workspace: meeting agendas and notes, coding-session notebooks, practice-exam attempts, and curated study resources.

---

## Table of contents

- [Goals](#goals)
- [Meeting format](#meeting-format)
- [12-week study plan](#12-week-study-plan)
- [Repository structure](#repository-structure)
- [Getting started](#getting-started)
- [Resources](#resources)
- [Contributing](#contributing)

---

## Goals

- Every member passes the Qiskit v2.X Developer Certification exam by the end of the program.
- Build a working, hands-on command of Qiskit 2.X — not just exam recall.
- Leave behind a reusable set of notes and notebooks for future study groups.

> **TODO:** Add group-specific goals agreed on in the first meeting (see [`SG_first_meeting_Qs.md`](resources/SG_first_meeting_Qs.md)).

---

## Meeting format

One **90-minute** meeting per week, with self-study ("homework") in between.

| Time   | Segment                       | What we do                                                                 |
| ------ | ----------------------------- | -------------------------------------------------------------------------- |
| 10 min | Homework review               | Common mistakes, concepts that didn't click                                  |
| 20 min | Concept lesson                | Key theory of the week's topic on a shared whiteboard                        |
| 30 min | Hands-on coding               | Work through examples, break things, write our own                           |
| 20 min | Practice questions            | Certification-style questions on the week's topic                            |
| 10 min | Wrap-up                       | Takeaways, homework, resources, confirm next meeting                         |

**Logistics**

| | |
| --- | --- |
| Cadence | *TBD — weekly* |
| Day & time | *TBD* |
| Platform | *TBD (Discord / Zoom / …)* |
| Meeting notes | [`meetings/`](meetings/) |

**Rotating roles** (proposed — decide in meeting 1):

- **Facilitator** — runs the agenda, keeps time
- **Note-taker** — writes the meeting log into `meetings/`
- **Topic lead** — prepares the concept lesson for the week
- **Question wrangler** — picks practice questions for the topic

---

## 12-week study plan

Adapted from the Qiskit Advocate example structure. Topics follow the [official exam syllabus](https://github.com/qiskit-advocate/qiskit-advocate-library/blob/main/advocate-resources/qiskit-cert-study-resources/QAP_Qiskit_exam_syllabus.pdf).

| Week | Topic | Session focus | Homework |
| ---- | ----- | ------------- | -------- |
| 1  | Kickoff & level-setting | Introductions, [first-meeting questions](resources/SG_first_meeting_Qs.md), assess prior Qiskit/QC experience, agree on cadence and plan, install Qiskit, build a first circuit | Finish install, refresh Python basics, review *perform quantum operations* resources |
| 2  | Defining & applying quantum operations | Pauli operators, Bloch sphere intuition, X/Y/Z/H/S/T, RX/RY/RZ, two-qubit gates (CX, CZ, SWAP); coding + practice questions | Review *visualize circuits, measurements, and states* resources |
| 3  | Visualizing circuits, measurements & states | Circuit drawing, state and measurement visualization; coding + practice questions | Review *create quantum circuits* resources |
| 4  | Creating quantum circuits | Circuit construction, registers, parameterized circuits, composition; coding + practice questions | Review *run quantum circuits* resources |
| 5  | Running quantum circuits | Execution modes (job / session / batch), running on real hardware, transpilation basics; coding + practice questions | Review *use the Sampler primitive* resources |
| 6  | The Sampler primitive | SamplerV2 usage, PUBs, error mitigation options, resilience levels; coding + practice questions | Review *use the Estimator primitive* resources |
| 7  | The Estimator primitive | EstimatorV2 usage, observables, expectation values, mitigation options; coding + practice questions | Review *retrieve and analyze results* resources |
| 8  | Retrieving & analyzing results | Job monitoring, result objects, `BitArray` handling, post-processing; coding + practice questions | Review OpenQASM resources |
| 9  | OpenQASM | OpenQASM 3 semantics and structure, interop with Qiskit; coding + practice questions | Review Qiskit IBM Runtime REST API resources |
| 10 | Qiskit IBM Runtime REST API | Endpoints, auth, submitting and querying jobs; practice questions | **Full-length mock exam under timed conditions** — log weak areas |
| 11 | Mock exam review | Walk through solutions together, compare approaches to hard questions | Targeted review of weak areas |
| 12 | Final review & readiness | Lightning review of all topics, exam strategy, confidence check | Submit study group finalization form, sit (or schedule) the exam |

> This is a starting point, not a contract. If the group wants to slow down on primitives and compress OpenQASM, we change it — see [Contributing](#contributing).

---

## Repository structure

Shared material lives at the top level. Each member gets their own folder under `members/` for personal code, notes, and practice attempts.

```
Qiskit-SG24/
├── README.md
├── meetings/              # Shared — one file per week: agenda, notes, action items
│   └── week-01.md
├── shared/                # Shared — code we write together in coding sessions
│   └── week-01/
├── resources/             # Shared — syllabus, links, reference material
│   ├── advocate_created_practice_exams.md
│   └── SG_first_meeting_Qs.md
└── members/               # Personal — one folder per member
    ├── <member-1>/
    │   ├── README.md      # Optional: goals, background, progress log
    │   ├── notebooks/     # week-NN/ subfolders or flat, your call
    │   └── practice/      # Practice-exam attempts and worked answers
    ├── <member-2>/
    ├── <member-3>/
    └── <member-4>/
```

> **TODO:** Replace `<member-N>` with each member's GitHub handle (recommended — it matches the commit author) or Discord username. Pick one convention and stick to it.

**Naming conventions**

- Meeting notes: `meetings/week-NN.md`
- Shared session code: `shared/week-NN/topic-name.ipynb`
- Personal notebooks: `members/<handle>/notebooks/week-NN-topic.ipynb`
- Practice attempts: `members/<handle>/practice/week-NN-<exam-name>.md`

**Who edits what**

- Your own folder is yours. Push directly to `main`, no review needed, organize it however you like.
- `meetings/`, `shared/`, `resources/`, and this README are group-owned — changes go through a PR.
- Don't edit someone else's folder. If you spot a mistake in their work, open an issue or bring it up in the meeting.

Setting up your folder:

```bash
mkdir -p members/<your-handle>/{notebooks,practice}
touch members/<your-handle>/README.md
git add members/<your-handle>
git commit -m "Add <your-handle> member folder"
git push
```

---

## Getting started

```bash
git clone https://github.com/<org-or-user>/Qiskit-SG24.git
cd Qiskit-SG24

python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

pip install qiskit qiskit-ibm-runtime qiskit-aer
pip install "qiskit[visualization]" jupyter
```

Verify the install:

```python
import qiskit
print(qiskit.__version__)        # expect 2.x

from qiskit import QuantumCircuit
qc = QuantumCircuit(2)
qc.h(0)
qc.cx(0, 1)
print(qc.draw())
```

To run on real hardware, create an [IBM Quantum Platform](https://quantum.cloud.ibm.com/) account and save your credentials locally:

```python
from qiskit_ibm_runtime import QiskitRuntimeService
QiskitRuntimeService.save_account(channel="ibm_quantum_platform", token="<YOUR_TOKEN>")
```

> Never commit API tokens. `.env` and credential files should stay in `.gitignore`.

---

## Resources

**Official**

- [Certification page & exam objectives](https://www.ibm.com/training/certification/ibm-certified-quantum-computation-using-qiskit-v2x-developer-associate-C9008400)
- [Exam syllabus guide (Qiskit Advocate Library)](https://github.com/qiskit-advocate/qiskit-advocate-library/blob/main/advocate-resources/qiskit-cert-study-resources/QAP_Qiskit_exam_syllabus.pdf)
- [Qiskit documentation](https://quantum.cloud.ibm.com/docs)
- [IBM Quantum Learning](https://quantum.cloud.ibm.com/learning)

**Study group materials**

- [Study group kickoff recording](https://event.on24.com/wcc/r/5435181/4F5ADC5B7BE8DBAD0C75B927C51A83F0)
- [First meeting discussion questions](resources/SG_first_meeting_Qs.md)
- [Example 12-week study plan](https://github.com/qiskit-advocate/qiskit-advocate-library/blob/main/advocate-resources/qiskit-cert-study-resources/)

**Practice exams**

A full list of advocate-created practice exams lives in [`resources/advocate_created_practice_exams.md`](resources/advocate_created_practice_exams.md). A few starting points:

| Practice exam | Creator |
| --- | --- |
| [clausia/qiskit-v2.x-cert-practice-exam](https://github.com/clausia/qiskit-v2.x-cert-practice-exam/blob/main/practice-exam-1.md) | clausia |
| [Seattle QC Meetup sample exam (PDF)](https://github.com/SeattleQuantumComputingMeetup/qiskit_developer_certification/blob/main/Sample_Exam_Qiskit2.0_Developer_Certification_2025.pdf) | nhawkins_seattle |
| [quantum-tokyo/qiskit-certification-prep](https://github.com/quantum-tokyo/qiskit-certification-prep) | dmurata |
| [MarcoBarroca/qiskit-v2-mock-exam](https://github.com/MarcoBarroca/qiskit-v2-mock-exam) | MarcoBarroca |
| [Q-Bees practice questions (notebook)](https://github.com/Q-Bees/Qiskit-v2.X-Certification-Practice-Questions/blob/main/Qiskit-Practice-Exam.ipynb) | maja |
| [QubitQuiz newsletter](https://qubitquiz.substack.com/) | itsazombi |

Huge thanks to the advocates who built and shared these.

---

## Contributing

**Your own folder** (`members/<your-handle>/`) — commit straight to `main`. Pull first to avoid conflicts:

```bash
git pull --rebase
git add members/<your-handle>
git commit -m "week-03: Sampler practice"
git push
```

**Shared folders** (`meetings/`, `shared/`, `resources/`, `README.md`) — use a branch and a PR:

```bash
git checkout -b week-03-notes
# ...make changes...
git push -u origin week-03-notes
```

Then open a PR and tag whoever facilitated that week. Small fixes — a typo, a broken link — can go straight to `main`. Anything that changes the study plan gets discussed in a meeting first.

**Ground rules**

- Clear notebook outputs before committing (`jupyter nbconvert --clear-output --inplace <file>.ipynb`) unless the output is the point.
- No API tokens, ever.
- Wrong answers are useful. Commit them with the reasoning, not just the correction.
