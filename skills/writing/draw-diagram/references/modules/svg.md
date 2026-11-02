# 모듈: SVG

HTML 문서(연구일지 등)에 들어가는 그림. 직접 작성한 인라인 SVG.

## 출력 형태

- HTML 문서 안: `<figure>` 안에 `<svg>`를 직접 넣고 `<figcaption>`에 캡션
- 단독 그림: `.svg` 파일
- 자동 배치 도구(Mermaid, Graphviz)는 쓰지 않음. 색·모양·정렬 규칙을 지킬 수 없음

## 작성 규칙

- `viewBox`로 크기 지정, `width="100%"`
- 색은 `assets/palette.md`의 HEX. `<style>` 안 클래스로 정의 (`.m-blue { fill: #BFDFFB }`)
- 화살촉은 `<defs>`에 `<marker>` 하나만 정의해서 모든 선에 씀
- 직각 화살표는 `<path d="M x y H x2 V y2">`처럼 H·V 명령만
- 글자는 `<text>`, `text-anchor="middle"`, `dominant-baseline="central"`. 글꼴은 페이지 글꼴 상속
- 수식 기호는 `<tspan font-style="italic">`과 `baseline-shift`로 아래첨자. 복잡한 수식은 TikZ로 넘길지 사용자에게 물음
- 같은 종류 박스는 같은 `width`·`height`
- 내용물 그림은 `<image href="...">`. 이미지는 content-images 모듈로 만듦

## 점검

- Playwright로 HTML이나 SVG를 열어 스크린샷을 찍고 Read로 직접 봄
- 글자가 박스 밖으로 넘치지 않는지 (SVG는 자동 줄바꿈이 없음)
- 밝은 배경과 어두운 배경 모두에서 선과 글자가 보이는지 (문서가 다크 모드를 지원할 때)
