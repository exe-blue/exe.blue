# Working Conventions

병렬 작업하는 AI 에이전트들의 충돌 없는 운영 규칙.

## Branch

형식: `<agent>/<linear-id>-<slug>`

예시:
- `claude/REB-236-regx-spec`
- `forge/REB-234-self-sustaining`
- `seer/REB-237-kyeolso-propagation`

## Commit

Conventional Commits 변형:

```
<type>(<scope>): <subject>
```

타입: `feat`, `fix`, `docs`, `chore`, `refactor`, `test`, `style`

예시:
- `feat(REB-236): regX 첫 시안`
- `docs(AGENTS): 매개체 분리 원칙 링크 추가`
- `chore: TASKS.md 동기화`

## Pull Request

### 제목
`[REB-XXX] 한 문장 요약`

### 본문 필수 섹션
```markdown
## What
무엇을 했는가

## Why
ORIGIN의 어떤 비전에 응답하는가

## Linear
Closes REB-XXX

## Reviewers
어떤 AI에게 리뷰를 요청하는가 (예: @claude @seer)
```

## Merge 조건

1. 1개 이상의 다른 AI 리뷰 LGTM
2. 테스트 통과 (있는 경우)
3. ORIGIN의 명시적 거부 없음 (24시간 무응답 = 묵시적 승인)
4. → squash merge

리뷰 AI가 직접 머지 가능. ORIGIN 호출 불필요.

## Close

- PR 머지 = TASKS.md에서 제거
- Linear 이슈는 Done 자동 전환

## 충돌 해결

- **같은 파일 동시 작업**: 먼저 PR 올린 쪽 우선. 뒤늦은 PR은 rebase
- **설계 충돌**: PR 코멘트에서 두 AI가 직접 합의. 합의 안 되면 ORIGIN 거부권에 위임
- **우선순위 충돌**: TASKS.md 상위 우선순위 우선

## 헌법적 변경

이 파일을 포함한 다음 파일들에 대한 변경은 ORIGIN의 명시적 승인 필요:
- AGENTS.md
- WORKING-CONVENTIONS.md
- docs/MEDIATOR-SEPARATION.md
- docs/PARALLEL-WORKFLOW.md

그 외 모든 작업은 위 머지 조건에 따라 AI 자율.
