# 학습 기록 PR 형식

이 문서는 TLI 학습 기록을 GitHub Pull Request로 게시할 때 사용하는 절차와 형식을 정의한다.

## 기존 게시 방식에서 확인한 관례

- 2026-08-16과 2026-08-17 Daily는 각각 Daily 파일 하나만 `docs: add YYYY-MM-DD study reflection` 형식의 커밋으로 `main`에 직접 push했다.
- 저장소의 기존 PR #1은 `Summary`와 `Verification` 두 섹션으로 본문을 작성했다.
- 앞으로는 Daily를 `main`에 직접 push하지 않고, 이 문서의 형식에 따라 별도 브랜치에 push한 뒤 PR을 생성한다.

## 게시 승인 경계

1. Daily와 Concepts 초안은 채팅으로만 제시한다.
2. 사용자가 회고 원문, Concepts 선택, 공부 시간, 게시 경로를 확인한다.
3. 작성자와 분리된 실제 서브 에이전트가 최신 초안을 읽기 전용으로 검수한다.
4. 작성자가 검수 결과를 반영한 최종본과 게시 대상 파일을 채팅으로 다시 제시한다.
5. 사용자가 아래 승인 문구 중 하나를 검수된 최신 최종본을 가리키는 실제 명령으로 사용한 경우에만 파일 작성, commit, push, PR 생성을 진행한다.

최종 게시 승인 문구는 다음과 같다.

- `이대로 Git에 올려줘`
- `최종 Git에 올려줘`
- `완료 Git`
- `Git에 올려줘`
- `Git에 push 해줘`

질문, 인용, 예시, 규칙 논의 과정에서 승인 문구가 나온 것은 게시 승인으로 처리하지 않는다.

최종 게시 승인은 승인된 브랜치의 push와 PR 생성까지를 의미한다. PR merge와 배포는 포함하지 않으며, 각각 별도의 명시적 요청이 있어야 한다.

## 브랜치와 커밋 형식

Daily와 관련 Concepts를 게시하는 기본 브랜치는 다음 형식을 사용한다.

```text
docs/daily-YYYY-MM-DD
```

Daily만 추가하는 기본 커밋 메시지는 다음과 같다.

```text
docs: add YYYY-MM-DD study reflection
```

Daily와 Concepts 또는 지침 문서를 함께 게시하면 변경 단위별로 커밋을 분리할 수 있다. 각 커밋에는 사용자가 승인한 파일만 포함한다.

## PR 제목 형식

Daily만 추가하는 기본 제목은 커밋 메시지와 동일하게 작성한다.

```text
docs: add YYYY-MM-DD study reflection
```

관련 Concepts나 지침 변경이 함께 포함되면 핵심 변경을 모두 포괄하는 짧은 제목을 사용한다.

## PR 본문 형식

기존 PR #1의 관례를 따라 `Summary`와 `Verification`으로 작성한다.

```md
## Summary
- add the YYYY-MM-DD daily study log
- summarize the approved study topics and study time
- preserve the user-approved reflection and include only selected Concepts

## Verification
- completed an independent read-only sub-agent review
- verified the final diff contains exactly the approved files
- passed git diff --cached --check
```

실제 PR에는 수행하지 않은 검증을 적지 않는다. 문제가 있거나 생략한 검증은 그 사실을 그대로 기록한다.

## PR 생성 절차

1. `main`의 최신 상태와 현재 worktree 변경을 확인한다.
2. `docs/daily-YYYY-MM-DD` 브랜치를 생성하거나 해당 브랜치로 이동한다.
3. 사용자가 승인한 최신 최종본만 파일에 반영한다.
4. `git status`와 diff를 확인하고 승인된 정확한 경로만 stage한다.
5. staged diff와 `git diff --cached --check`를 확인한다.
6. 승인된 파일만 commit한다.
7. 작업 브랜치를 remote에 push한다. `main`에는 직접 push하지 않는다.
8. `main`을 base, 작업 브랜치를 head로 하여 위 형식의 PR을 생성한다.
9. 생성된 PR의 제목, 파일 범위, URL을 사용자에게 보고한다.

기존의 관련 없는 변경과 승인되지 않은 untracked 파일은 stage, commit, push 또는 PR에 포함하지 않는다.
