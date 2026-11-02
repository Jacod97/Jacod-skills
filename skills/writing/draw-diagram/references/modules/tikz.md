# 모듈: TikZ

LaTeX 문서에 들어가는 그림. 들어갈 곳이 LaTeX면 묻지 않고 이 모듈을 쓴다.

## 출력 형태

- LaTeX 문서 안: `figure` 환경 안에 `tikzpicture`를 직접 넣음. 문서 전처리부에 `\usepackage{tikz}`와 `\input{tikz-styles.tex}` 추가
- 단독 그림: `\documentclass[tikz,border=4pt]{standalone}`. 엔진은 XeLaTeX. 글꼴은 그림이 들어갈 문서와 같게 (write-docs 문서면 그 전처리부의 글꼴 설정을 그대로 가져옴)
- 전달: `.tex` + `.pdf`. 요청하면 PNG도 (`pdftoppm -png -r 300`)
- 이미지로 내보낼 때(Markdown 문서 등)는 `tikzpicture` 맨 끝에서 `\dgCanvas`로 흰 바탕을 깖. 자세한 것은 `modules/markdown.md`

## 스타일

- `assets/tikz-styles.tex`를 작업 폴더에 복사해서 `\input`. 원본은 수정하지 않음
- 스타일 이름: `module`, `data`, `scalar`, `chip`, `op`, `reduce`, `branch`, `container`, `repeatbox`, `flow`, `ref`, `zoom`, `skip`, `symlabel`, `namelabel`, `panellabel`
- 모듈 색은 `module, fill=dgXxx`로 지정. 팔레트는 `assets/palette.md`
- 그림마다 새 스타일이 필요하면 그림 파일 안 `\tikzset`에 추가. 같은 스타일이 두 그림 이상에서 필요해지면 원본에 올리자고 제안

## 작성 규칙

- 배치는 상대 위치(`right=of`, `below=6mm of`)와 `node distance`로. 절대 좌표 남발 금지
- 같은 종류 박스 폭은 `minimum width`나 `text width`로 통일
- 직각 화살표는 `-|`, `|-`. 꺾임이 둘 이상이면 `++(x,0) |-` 같은 경유점
- 컨테이너는 `fit=(...)`와 `on background layer`
- 반복은 `repeatbox` + 위에 `$N\times$`
- 확대선은 `zoom` 스타일로, 원래 박스의 모서리와 확대 패널의 모서리를 이음
- 수식 기호는 `$...$`. 본문과 같은 매크로 사용
- 내용물 그림은 노드 안 `\includegraphics[height=...]`. 이미지는 content-images 모듈로 만듦
- 글자 크기 `\small`, 기호 `\normalsize`. 그림 폭은 `\linewidth` 기준. 넘치면 `\resizebox` 대신 배치를 고침

## 점검

- XeLaTeX 컴파일 오류 없음. 로그의 `Missing character`, `Overfull` 확인
- PDF를 PNG로 바꿔 Read로 직접 봄
- 글자가 박스 밖으로 넘치거나 화살표가 박스를 관통하지 않는지
- 그림을 문서에 넣었을 때 글자 크기가 본문 캡션보다 작아지지 않는지
