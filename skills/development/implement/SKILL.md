---
name: implement
description: planning으로 승인된 작업 계획서(docs/planning-output.md, docs/task/)대로 코드를 구현할 때 사용. 계획에 있는 것만 구현하고, 계획과 다르게 된 것은 DLFA.md(에이전트를 위한 개발일지)에 기록한다. "/implement", "task 01 구현해줘", "계획대로 구현 시작해" 같은 요청.
---

# 구현 (implement)

이 파일은 길잡이다. 규칙 본문은 `references/`에 있다.

```
references/core.md   구현 규칙
references/dlfa.md   DLFA 작성 규칙 (모드별 기록 범위)
assets/DLFA.md       DLFA 양식
```

## 1. 입력 확인

- `docs/planning-output.md`, `docs/task/` 작업 계획서가 있어야 한다. 없으면 planning을 먼저 하라고 알리고 멈춘다.
- 모드(리서치·업데이트·빌드)는 `planning-output.md` 제목에서 읽는다.
- 작업 대상 저장소에 `DLFA.md`가 있으면 읽는다.

## 2. 규칙 로드

1. `references/core.md`를 끝까지 읽는다.
2. `references/dlfa.md`를 끝까지 읽는다.

## 3. 실행할 task 확인

- 어떤 task를 이번에 구현할지 사람에게 묻는다. 선행 task가 끝나지 않은 task를 고르면 그 사실을 알린다.

## 4. 절차 (task마다)

1. task 문서와 대상 파일의 기존 코드를 읽는다
2. 구현
3. 완료 조건 확인. 실행해서 확인할 수 있으면 실행한다
4. 점검 (`core.md`)
5. DLFA 기록 (`dlfa.md`)
6. 사람에게 결과 보고: 결과 한 줄, 계획과 다른 점, 확인하지 못한 것
