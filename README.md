# Codex Active Orchestration AGENTS.md

## 한국어

이 저장소는 Codex가 작업을 더 효율적으로 나누어 처리하도록 돕는 `AGENTS.md` 운영지침을 제공합니다.

목표는 간단합니다.

Codex가 모든 일을 한 모델 강도로 직접 처리하지 않고, 부모 세션이 작업을 판단한 뒤 필요한 경우 적절한 강도의 워커에게 실제 작업을 맡기도록 하는 것입니다.

이 방식은 특히 다음 상황에 유용합니다.

- 작업이 여러 파일이나 여러 단계로 나뉘는 경우
- 코드 작성과 검토를 분리하고 싶은 경우
- 단순 확인에는 낮은 추론 강도를 쓰고 싶은 경우
- 보통 구현은 적당한 강도로 처리하고 싶은 경우
- 위험한 판단이나 최종 검토에만 높은 추론 강도를 쓰고 싶은 경우
- 전체 작업을 무조건 가장 비싼 추론 강도로 처리하고 싶지 않은 경우

부모 세션은 `xhigh`일 수도 있고 아닐 수도 있습니다. 이 지침은 특정 부모 강도를 강제하지 않습니다. 핵심은 부모가 어떤 강도이든 작업을 보고 적절히 나누고, 워커 강도를 상황에 맞게 고르는 것입니다.

### 포함 파일

배포 구성은 두 파일입니다.

```text
.
|-- AGENTS.md
`-- README.md
```

- `AGENTS.md`: Codex가 실제로 따를 운영지침
- `README.md`: 사람이 읽는 설명 문서

별도 런처, 스크립트, 스킬 패키지, 외부 의존성은 필요하지 않습니다.

### 설치 방법

사용할 프로젝트 루트에 `AGENTS.md`를 복사합니다.

```text
your-project/
|-- AGENTS.md
|-- src/
`-- ...
```

그 다음 해당 프로젝트에서 Codex를 실행하면 됩니다.

```powershell
cd your-project
codex
```

`README.md`는 GitHub 배포용 설명 문서입니다. 실제 동작에는 `AGENTS.md`만 필요합니다.

### 기본 개념

이 지침은 Codex를 두 역할로 나누어 생각합니다.

#### 부모 세션

부모는 전체 작업을 책임지는 조율자입니다.

부모가 하는 일:

- 작업 의도 파악
- 필요한 파일과 범위 확인
- 작업 분해
- 워커 호출
- 결과 통합
- 최종 리뷰
- 검증
- 결과가 약할 때 재위임 또는 추론 강도 상향

#### 워커

워커는 범위가 정해진 실제 작업자입니다.

워커가 하는 일:

- 코드 작성
- 문서 작성
- 산출물 생성
- 특정 파일 수정
- 특정 범위 조사
- 특정 검증 수행

### 작업 흐름

일반적인 흐름은 다음과 같습니다.

1. Codex가 먼저 `AGENTS.md`를 읽습니다.
2. 부모가 작업 목표와 현재 파일 상태를 간단히 확인합니다.
3. 코드, 문서, 산출물처럼 실제 작성물이 필요한지 판단합니다.
4. 필요한 경우 부모가 직접 구현하지 않고 워커를 부릅니다.
5. 부모는 워커에게 작은 컨텍스트와 명확한 작업 범위를 줍니다.
6. 워커가 실제 파일을 작성하거나 수정합니다.
7. 부모가 결과를 읽고 통합, 리뷰, 검증합니다.
8. 부족하면 부모가 다시 나누거나 더 높은 강도의 워커에게 맡깁니다.

### 사전 승인된 능동 위임

이 지침은 사용자가 능동 위임을 기본적으로 허용한다고 가정합니다.

즉, Codex가 매번 "워커를 불러도 될까요?"라고 묻지 않고, 작업상 필요하다고 판단하면 워커를 부를 수 있습니다.

단, 실행 환경이나 상위 도구 정책이 워커 호출을 막는 경우에는 이를 우회하지 않습니다. 그런 경우 부모는 직접 몰래 대신 구현하지 않고, 워커 호출이 막혔다고 보고해야 합니다.

### 추론 강도 선택 기준

추론 강도는 고정 숫자나 쿼터 계산으로 고르지 않습니다.

기준은 다음 네 가지입니다.

- 작업 위험도
- 불확실성
- 영향 범위
- 실패 비용

권장 기준:

| 강도 | 적합한 작업 |
|---|---|
| `low` | 파일 스캔, 단순 확인, 작은 수정 |
| `medium` | 일반 구현, 문서 작성, 보통 기능 |
| `high` | 원인 분석, 아키텍처 판단, 마이그레이션, flaky 테스트, 보안, 최종 검토 |
| `xhigh` | 실패 비용이 큰 최상위 위험 판단, `high`로 부족한 병목 |

중요한 점은 전체 작업을 한 강도로 밀어붙이지 않는 것입니다.

예를 들어 웹앱을 만든다면:

- 부모: 요구사항 파악, 범위 설정, 리뷰
- `medium` 워커: 실제 구현
- `low` 워커: 단순 파일 확인이나 정적 검사
- `high` 워커: 복잡한 버그나 보안 이슈가 생길 때만 사용

### 토큰 효율성

비용은 추론 강도 이름만으로 결정되지 않습니다.

다음 요소가 비용에 영향을 줍니다.

- 입력 컨텍스트 크기
- 출력 길이
- 숨은 추론 토큰
- 도구 호출 결과
- 재시도 횟수
- 동시에 부르는 워커 수
- 전체 대화 기록을 워커에게 넘기는지 여부

그래서 이 지침은 다음을 권장합니다.

- 워커에게 필요한 내용만 짧게 전달
- 낮은 강도 워커에는 `fork_context=false` 사용
- 스캔 작업은 싸게 처리
- 일반 구현은 `medium` 중심으로 처리
- 고위험 판단에만 `high` 또는 제한적 `xhigh` 사용
- 모든 워커를 한꺼번에 고강도로 올리지 않기

### 예시

#### 예시 1: 작은 정적 웹앱 만들기

사용자 요청:

```text
지뢰찾기 만들어줘. 브라우저에서 바로 열 수 있게.
```

기대 흐름:

1. 부모가 프로젝트가 비어 있는지 확인
2. 부모가 정적 HTML/CSS/JS 앱으로 충분하다고 판단
3. 부모가 `medium` 워커에게 구현을 맡김
4. 워커가 `index.html`, `style.css`, `script.js` 작성
5. 부모가 파일을 읽고 동작을 검토
6. 부모가 문법 검사나 간단한 스모크 테스트 실행
7. 부모가 결과와 확인 내용을 보고

#### 예시 2: 마이그레이션 검토

사용자 요청:

```text
이 데이터 마이그레이션 계획 위험한 부분 검토해줘.
```

기대 흐름:

1. 부모가 영향 범위와 실패 비용을 파악
2. 단순 스캔은 `low` 워커에게 맡김
3. 동시성, 롤백, 데이터 무결성은 `high` 워커에게 맡김
4. 부모가 결과를 통합
5. 최종 위험과 검증 항목을 정리

### 주의할 점

이 지침은 Codex의 행동을 강하게 유도하지만, 모든 실행 환경에서 서브에이전트 호출이 항상 가능한 것은 아닙니다.

다음 경우에는 기대대로 동작하지 않을 수 있습니다.

- 사용하는 Codex 환경이 워커 호출을 지원하지 않는 경우
- 상위 정책이 서브에이전트 사용을 제한하는 경우
- 도구 권한이 부족한 경우
- 실행 중인 클라이언트가 `AGENTS.md`를 읽지 않는 경우

이 경우 Codex는 제한 사항을 보고해야 합니다.

### 요약

이 `AGENTS.md`는 Codex가 다음 방식으로 일하도록 유도합니다.

- 부모가 먼저 읽고 판단한다.
- 부모는 계획과 감독을 맡는다.
- 실제 산출물은 워커가 만든다.
- 작업별로 추론 강도를 다르게 쓴다.
- 불필요한 `xhigh` 사용과 과도한 fanout을 줄인다.
- 부모가 최종 리뷰와 검증을 책임진다.

---

## English

This repository provides a minimal `AGENTS.md` policy for Codex active orchestration.

The goal is simple:

Codex should not handle every task directly with one reasoning level. Instead, the parent session should understand the task, split it when useful, and delegate real work to bounded workers with appropriate effort.

This is useful when:

- a task spans multiple files or phases
- implementation and review should stay separate
- simple checks should use cheaper reasoning
- normal implementation should use balanced reasoning
- high reasoning should be saved for risky diagnosis or final review
- not every task should run at the most expensive effort level

The parent session may or may not be `xhigh`. This policy does not require a specific parent effort. The point is that the parent plans and supervises, while worker effort is selected by task risk.

### Included Files

The release layout has two files:

```text
.
|-- AGENTS.md
`-- README.md
```

- `AGENTS.md`: the operating policy Codex should follow
- `README.md`: the human-readable explanation

No launcher, script, skill package, or external dependency is required.

### Installation

Copy `AGENTS.md` into the root of the project where you want this behavior.

```text
your-project/
|-- AGENTS.md
|-- src/
`-- ...
```

Then run Codex from that project.

```powershell
cd your-project
codex
```

`README.md` is for GitHub distribution and explanation. Only `AGENTS.md` is required for behavior.

### Core Idea

The policy separates Codex into two roles.

#### Parent Session

The parent is the coordinator.

The parent handles:

- understanding the task
- checking relevant files
- scoping the work
- splitting the work
- spawning workers
- integrating results
- final review
- verification
- rerouting or escalating weak results

#### Workers

Workers perform bounded execution.

Workers handle:

- code
- documentation
- deliverables
- scoped edits
- scoped investigation
- scoped verification

### Workflow

The usual flow is:

1. Codex reads `AGENTS.md` first.
2. The parent gathers just enough context.
3. The parent decides whether real code, documentation, or deliverables are needed.
4. If so, the parent spawns bounded workers instead of implementing directly.
5. The parent gives workers compact context and clear ownership.
6. Workers create or edit the actual files.
7. The parent reviews, integrates, and verifies the result.
8. If the result is weak, the parent reroutes or escalates.

### Standing Approval For Delegation

This policy records a standing user preference for proactive delegation.

Codex does not need to ask every time before spawning a worker when the task justifies it.

However, this does not bypass higher-level platform or tool policy. If the current environment blocks worker spawning, the parent should report the blocker instead of silently implementing the task itself.

### Reasoning Effort Selection

Reasoning effort is not selected by fixed quota math.

Use these criteria:

- risk
- uncertainty
- blast radius
- failure cost

Suggested mapping:

| Effort | Good fit |
|---|---|
| `low` | file scans, simple checks, small fixes |
| `medium` | normal implementation, documentation, ordinary feature work |
| `high` | diagnosis, architecture, migration, flaky tests, security, final review |
| `xhigh` | bounded top-risk work where failure cost is high or `high` was insufficient |

The important rule is not to force the entire job into one effort level.

For example, for a small browser app:

- parent: understand scope and review
- `medium` worker: implement the app
- `low` worker: simple file checks or static checks
- `high` worker: only if a difficult bug or security issue appears

### Token Efficiency

Cost is affected by more than the effort label.

Important factors include:

- input context size
- output length
- hidden reasoning tokens
- tool results
- retries
- number of parallel workers
- whether the full conversation history is passed to workers

The policy therefore prefers:

- compact worker context
- `fork_context=false` for lower-effort workers
- cheap scans
- `medium` for normal implementation
- `high` or bounded `xhigh` only for high-risk judgment
- no blanket high-effort fanout

### Examples

#### Example 1: Small Static Web App

User request:

```text
Make a Minesweeper game that opens directly in a browser.
```

Expected flow:

1. Parent checks whether the project is empty.
2. Parent decides that static HTML/CSS/JS is enough.
3. Parent delegates implementation to a `medium` worker.
4. Worker creates `index.html`, `style.css`, and `script.js`.
5. Parent reviews the files.
6. Parent runs syntax or smoke checks.
7. Parent reports the result and verification.

#### Example 2: Migration Review

User request:

```text
Review this data migration plan for risk.
```

Expected flow:

1. Parent identifies blast radius and failure cost.
2. Cheap scanning can go to a `low` worker.
3. Concurrency, rollback, and data integrity analysis can go to a `high` worker.
4. Parent integrates findings.
5. Parent reports risks and validation requirements.

### Limitations

This policy strongly guides Codex behavior, but worker spawning may not be available in every environment.

It may not work as expected if:

- the Codex client does not support worker spawning
- higher-level policy blocks subagents
- tool permissions are restricted
- the client does not read `AGENTS.md`

In those cases, Codex should report the limitation.

### Summary

This `AGENTS.md` guides Codex to:

- read the local policy first
- keep the parent responsible for planning and supervision
- delegate real deliverables to bounded workers
- choose reasoning effort by task risk
- reduce unnecessary `xhigh` usage
- avoid excessive fanout
- keep final review and verification in the parent

