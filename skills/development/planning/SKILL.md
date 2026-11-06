---
name: planning
description: 코드를 구현하기 전에 작업 계획을 세울 때 사용. 사람이 지정한 모드(리서치, 업데이트, 빌드)에 따라 단계별로 합의하며 docs/planning-output.md와 docs/task/ 작업 계획서를 만든다. 코드는 작성하지 않는다. "/planning research", "업데이트 계획 세워줘", "연구 코드 구조 잡을 계획 짜줘" 같은 요청.
---

# 계획 (planning)

이 파일은 길잡이다. 규칙 본문은 `references/`에 있고, 지정된 모드의 파일만 읽는다.

```
references/core.md           모든 모드 공통 규칙
references/modes/research.md 리서치
references/modes/update.md   업데이트
references/modes/build.md    빌드
assets/                      산출 문서 양식 (planning-output 모드별 3개, task)
```

- 같은 항목에서 규칙이 부딪치면 모드 파일이 이긴다.

## 1. 모드 확인

| 모드 | 하는 일 | 읽을 파일 |
|---|---|---|
| 리서치 | 연구 계획서를 검증할 실험 코드 계획 | `modes/research.md` |
| 업데이트 | 기존 아키텍처에 기능 추가·수정 계획 | `modes/update.md` |
| 빌드 | 검증된 연구 코드를 시스템으로 만드는 구조 계획 | `modes/build.md` |

- 모드는 사람이 정한다. 요청에 모드가 없으면 추측하지 않고 묻는다.

## 2. 규칙 로드

1. `references/core.md`를 끝까지 읽는다.
2. 모드 파일을 읽는다.
3. 작업 대상 저장소에 `DLFA.md`가 있으면 읽는다.

## 3. 절차

1. 모드 확인
2. 규칙 로드
3. 모드 파일의 필수 입력 확인. 없으면 요청하고 멈춘다
4. 모드 파일의 단계를 순서대로 진행. 단계마다 사람과 합의한 뒤 다음 단계로 간다
5. 산출 문서 작성
6. 점검: core 점검 + 모드 점검
7. 사람 검토. 승인하면 끝, 아니면 수정
