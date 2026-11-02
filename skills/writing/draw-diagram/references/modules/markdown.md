# 모듈: Markdown

Markdown 문서에 들어가는 그림. 그림을 이미지 파일로 렌더링하고, md에서는 링크로 불러온다.

## 소스 도구

- 수식 기호가 있으면 TikZ, 없으면 SVG로 직접 그림
- 소스 도구의 모듈(`tikz.md` 또는 `svg.md`)도 함께 읽고 그 규칙을 따름

## 파일 배치

```
<문서 폴더>/
  doc.md
  figures/
    <이름>.tex 또는 <이름>.src.svg   소스 (나중에 고칠 수 있게 반드시 함께 둠)
    <이름>.svg                       md가 불러오는 이미지
    <이름>.png                       SVG를 못 쓸 때만
```

- 이름은 내용을 나타내는 영어 소문자 kebab-case (`model-overview`, `sampling-loop`)
- md의 링크는 상대 경로 (`figures/model-overview.svg`)

## 이미지 형식

- 기본은 SVG. 렌더러가 SVG를 지원하지 않으면 PNG 300dpi
- TikZ → SVG: standalone으로 XeLaTeX 컴파일 후 `pdftocairo -svg <이름>.pdf <이름>.svg`
- TikZ → PNG: `pdftoppm -png -r 300 -singlefile <이름>.pdf <이름>`
- 직접 그린 SVG는 그대로 씀

## 배경

- 투명 배경 금지. 다크 모드에서 선과 글자가 사라짐
- TikZ: `tikzpicture` 맨 끝에서 `\dgCanvas` 호출 (`assets/tikz-styles.tex`), standalone은 `border=0pt` (여백은 `\dgCanvas`가 3mm 줌. 바꾸려면 `\dgCanvas[5mm]`). `\pagecolor`나 `show background rectangle`은 쓰지 않음 (SVG 변환에서 빠지거나 컨테이너를 가림)
- SVG: 첫 요소로 `<rect width="100%" height="100%" fill="white"/>`

## md 삽입

```markdown
![그림이 보여주는 것 한 문장](figures/model-overview.svg)

*그림 1. 그림이 보여주는 것 한 문장. 기호 x: 입력 시퀀스, t: diffusion timestep.*
```

- alt 텍스트는 캡션 첫 문장
- 캡션은 이미지 바로 아래 한 줄, 기울임. 번호는 문서 안에서 차례로
- 크기 조절이 필요하면 `<img src="..." width="80%">`. 그 외에는 HTML 태그 쓰지 않음

## 점검

- 이미지를 흰 바탕과 어두운 바탕 HTML에 각각 넣고 Playwright로 스크린샷을 찍어 Read로 봄
- 컨테이너·패널 배경이 흰 바탕에 가려지지 않았는지
- md의 상대 경로가 실제 파일과 맞는지
- 소스 파일이 이미지 옆에 있는지
