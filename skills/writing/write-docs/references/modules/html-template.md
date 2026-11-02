# 모듈: HTML 템플릿

사용: 연구일지

## 템플릿 위치
- `assets/html/template.html`. 맨 위 주석에 쓸 수 있는 요소 목록과 차트 JSON 형식이 있다. 디자인을 새로 만들지 않는다.
- 템플릿 주석의 [문체] 절과 이 스킬의 core·word-rule 규칙이 다르면 core·word-rule을 따른다 (예: 개조식 "~함" 허용).

## 고정된 부분 (수정 금지)
- `<head>` 안의 `<style>`, 글꼴 링크, Chart.js 스크립트
- `</main>` 뒤의 차트 렌더러 `<script>`
- 인라인 `style`, 새 class, 아이콘, 이모지, 색 박스, 배지를 추가하지 않는다.

## 사용할 수 있는 요소

| 용도 | 마크업 |
|---|---|
| 제목·부제목·작성 정보 | `<header class="title-block">` 안의 `h1`, `p.subtitle`, `p.byline` |
| 대제목 | `<h2><span class="num">1.</span>…</h2>` |
| 소제목 | `<h3><span class="num">1.1</span>…</h3>` |
| 세부제목 | `<h4>` (번호 없음) |
| 본문 | `<p>` |
| 개조식 | `<ul>`, 순서가 있으면 `<ol>`. 한 단계까지 중첩 |
| 표 | `<figure class="table">` → `<table>` → `<figcaption>`(표 아래) |
| 그림 | `<figure class="fig">` → `<img src="…" alt="…">` → `<figcaption>`(그림 아래) |
| 나란히 2개 | `<div class="fig-row">` 안에 `figure.fig` 두 개 |
| 차트 | `<figure class="fig"><div class="chart"><canvas data-chart='JSON'></canvas></div><figcaption>…</figcaption></figure>` |
| 수식 | `<div class="eq"><span>식</span><span class="eqno">(1)</span></div>` |
| 코드 | `<pre>` |
| 메모 | `<p class="memo">` |
| 각주 | 본문 `<sup class="fn">1</sup>`, 문서 끝 `<ol class="footnotes">` |

- 캡션은 `<span class="label">표 1.</span>캡션` 형식이다. 차트도 "그림"으로 센다.

## 차트 JSON
```
공통   "x":"x축 이름 (단위)", "y":"y축 이름 (단위)", "yMin", "yMax", "yLog":true (선택)
꺾은선 {"type":"line", "labels":[...], "series":[{"name":"","data":[...]}]}
       기준선은 계열에 "dash":true
막대   {"type":"bar", "labels":[...], "series":[...]}
       "highlight":"max" | "min" | 숫자(0부터) → 해당 막대만 색, 나머지 회색
       가로 막대는 "horizontal":true
산점도 {"type":"scatter", "series":[{"name":"","data":[[x,y],...]}]}
원형   {"type":"pie", "labels":[...], "series":[{"data":[...]}]}
       "donut":true, 조각 위 비율 표시는 "showPercent":true, 조각은 6개 이하
```
- 계열은 기본 4개 이하. 적용·미적용 쌍을 비교할 때만 최대 8개.
- 차트 색은 렌더러가 정한다. JSON에 색을 넣지 않는다.
- JSON은 작은따옴표 속성값 안에 들어가므로 JSON 안에서 작은따옴표를 쓰지 않는다.
- 차트 데이터는 실제로 측정한 값만 넣는다.

## 점검
- [ ] `<style>`과 하단 `<script>`가 템플릿과 동일
- [ ] 차트 JSON이 모두 유효 (`JSON.parse`로 확인)
