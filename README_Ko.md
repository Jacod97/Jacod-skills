# Jacod-skills

[English](README.md) | 한국어

이 저장소는 문서 작성, 디자인, 개발에 대해 작성자가 선호하는 방식을 재사용 가능한 에이전트 스킬로 모은 것이다. 각 스킬은 실무 지침과 검증 기준을 포함하며, 필요한 경우 템플릿과 다이어그램 스타일을 함께 제공한다.
스킬 지침은 주로 한국어로 작성되어 있다. 필요에 따라 원하는 언어로 번역해 사용한다.

## 제공 스킬

스킬은 두 분류로 나뉜다. `writing`은 문서와 그림, `development`는 코드 계획과 구현을 다룬다.

### Writing

| 스킬 | 용도 | 결과물 |
| --- | --- | --- |
| [write-docs](skills/writing/write-docs/SKILL.md) | 연구 일지, 논문·개념 리뷰, 참고 문서, 연구 계획서 작성 | 문서 종류에 따라 HTML, LaTeX·PDF 또는 설명 문서 |
| [write-readme](skills/writing/write-readme/SKILL.md) | 애플리케이션, 라이브러리, CLI, 연구 저장소, 자료 모음의 소개와 사용법 작성 | 영어 `README.md` |
| [draw-diagram](skills/writing/draw-diagram/SKILL.md) | 모델·모듈 구조, 학습 단계, 처리 흐름 도식화 | 문서용 TikZ, SVG, PNG 다이어그램 |

### Development

| 스킬 | 용도 | 결과물 |
| --- | --- | --- |
| [planning](skills/development/planning/SKILL.md) | 구현 전에 리서치·업데이트·빌드 중 한 모드로 코드 작업을 계획. 코드는 작성하지 않음 | `docs/planning-output.md`와 `docs/task/` 아래 작업 계획서 |
| [implement](skills/development/implement/SKILL.md) | 승인된 작업 계획서를 task 단위로 계획대로 구현 | 코드 변경과 에이전트용 개발일지 `DLFA.md` |

## 스킬 선택

- **연구 문서 — `write-docs`**: 연구 일지는 실험과 결과를 기록한다. 리뷰는 논문과 기술 개념을 설명한다. 참고 문서는 데이터셋, 라이브러리, 코드베이스, 도구를 나중에 찾아보기 좋게 정리한다. 연구 계획서는 목표, 방법, 제안 실험을 정의한다. 본문 작성 전에 목차를 합의하는 절차가 포함된다.
- **저장소 소개와 사용법 — `write-readme`**: 저장소 유형에 맞춰 목적, 기능, 설치, 예제를 구성한다. 공개 동작과 명령은 소스를 확인해 검증한다. 결과물은 영어와 객관적인 문서체로 작성된다.
- **구조·과정 다이어그램 — `draw-diagram`**: 구조도는 구성 요소와 관계를, 흐름도는 단계와 분기를 보여준다. LaTeX에는 TikZ, HTML에는 SVG, Markdown에는 링크된 이미지 파일을 사용한다.
- **구현 계획 — `planning`**: 계획의 각 단계는 합의를 거친 뒤 다음 단계로 넘어간다. 모드는 항상 사용자가 지정하며, 추측하지 않는다.
- **계획 기반 구현 — `implement`**: `planning`의 산출물이 필요하다. 계획에 있는 작업만 구현하고, 계획과 달라진 점, 실패한 시도, 실험 결과는 `DLFA.md`에 기록한다.

### Planning 모드

| 모드 | 목적 | 필수 입력 |
| --- | --- | --- |
| 리서치 | 연구 계획서의 가설을 검증할 실험 코드 계획. 시스템 견고성보다 비교 조건을 쉽게 바꿔 실행하는 것을 우선 | 연구 계획서 |
| 업데이트 | 기존 아키텍처의 설계 의도를 지키면서 기능 추가·수정 계획 | 업데이트 내용. 기존 코드는 직접 읽어 파악 |
| 빌드 | 검증된 연구 코드를 유지보수 가능한 시스템으로 만드는 구조 계획 | 연구 코드 디렉토리, `DLFA.md`, 연구 계획서 |

### 개발 흐름

1. 선택한 모드로 `planning`을 실행해 `docs/planning-output.md`와 `docs/task/` 아래 작업 계획서를 만든다.
2. 계획을 검토하고 승인한다.
3. 선택한 task에 대해 `implement`를 실행한다. 완료된 task는 완료 조건으로 확인하고 저장소 루트의 `DLFA.md`에 기록한다.
4. 리서치 모드 구현 후의 `DLFA.md`는 이후 빌드 모드 계획의 입력이 되어, 검증된 방식과 버린 방식이 이어진다.

## 시작하기

1. 에이전트가 접근할 수 있는 작업 공간에 이 저장소를 내려받는다.
2. 위 목록에서 스킬을 고른다.
3. 해당 `SKILL.md` 경로, 작업 목표, 원자료, 출력 위치를 전달한다. 참조되는 규칙과 템플릿에 접근할 수 있게 유지한다.

아래 예시는 저장소 루트를 작업 디렉토리로 가정한다. 다른 프로젝트에서 작업할 때는 스킬 경로를 맞게 바꾼다.

### 프로젝트 README

```text
skills/writing/write-readme/SKILL.md를 읽고 적용해줘.
이 저장소를 처음 보는 사용자를 위한 영어 README.md를 작성해줘.
제공 스킬과 사용 예시를 포함해줘.
```

### 연구 일지

```text
skills/writing/write-docs/SKILL.md를 읽고 적용해줘.
제공한 실험 설정과 결과로 연구 일지를 만들어줘.
비교 조건과 관찰 내용을 중심으로 목차를 먼저 제안해줘.
결과는 reports/ 아래 HTML로 저장해줘.
```

### 파이프라인 다이어그램

```text
skills/writing/draw-diagram/SKILL.md를 읽고 적용해줘.
데이터 수집, 전처리, 모델 학습, 평가를 담은 흐름도를 그려줘.
README용 SVG로 만들어 figures/ 아래에 저장해줘.
그리기 전에 구성 요소와 연결을 확인받아줘.
```

### 연구 코드 계획과 구현

```text
skills/development/planning/SKILL.md를 리서치 모드로 적용해줘.
docs/research-plan.md의 연구 계획서를 검증할 실험 코드를 계획해줘.
```

```text
skills/development/implement/SKILL.md를 읽고 적용해줘.
docs/task/의 task 01을 구현해줘.
```

스킬 등록을 지원하는 환경에서는 해당 환경의 방식으로 **스킬 폴더 전체**를 등록한다. `SKILL.md`만 복사하면 참조하는 규칙과 템플릿이 빠진다. 새 다이어그램이 필요하면 문서·README 스킬과 함께 `draw-diagram`도 사용할 수 있게 하고, `planning`과 `implement`는 함께 설치한다.

## 요구 사항

스킬을 적용하려면 로컬 파일을 읽고 수정할 수 있는 AI 에이전트가 필요하다. 생성·검증 도구는 결과물에 따라 다르다.

| 작업 | 요구 사항 |
| --- | --- |
| README 작성 | 대상 저장소, 실제 설치·사용 예시, Markdown 뷰어 |
| HTML 연구 일지 | 실험 설정과 결과, 결과 확인용 브라우저 |
| LaTeX 문서와 PDF | XeLaTeX, 필요한 패키지와 글꼴. 기본 한국어 레이아웃은 `xetexko`, Noto Serif CJK KR, Noto Sans CJK KR, DejaVu Sans Mono 사용 |
| 다이어그램 생성·검토 | SVG·HTML 검토용 브라우저와 Playwright, TikZ용 XeLaTeX, PDF를 SVG로 변환할 때 `pdftocairo` |
| 계획과 구현 | 대상 코드 저장소, [Planning 모드](#planning-모드)에 적힌 모드별 입력, 완료 조건 확인을 위한 프로젝트 실행 환경 |

결과물별 세부 요구 사항은 [LaTeX 문서 규칙](skills/writing/write-docs/references/modules/latex.md)과 [다이어그램 도구 선택 안내](skills/writing/draw-diagram/SKILL.md)에 정의되어 있다.
