# 모듈: LaTeX 출력

사용: 리뷰, 참조 문서 (기본 서식) / 연구계획서 (학술 변형)

## 시작 파일
- 기본 서식: `assets/latex/base.tex`
- 학술 변형: `assets/latex/academic.tex` (기본 서식 전처리부 + 학술 변형 설정)
- 템플릿 사용 모듈 방식으로 작업 폴더에 복사해 쓴다. `<...>` 자리표시는 모두 바꾼다.
- `assets/latex/kolabels-utf.sty`는 xetexko가 kolabels-utf.sty를 못 찾아 멈출 때 작업 폴더에 함께 복사하는 빈 스텁이다.

## 서식 규칙
- 엔진은 XeLaTeX, 한글은 xetexko.
- 글꼴: 본문 본명조, 제목·소제목 본고딕, 캡션은 본문과 같은 본명조, 고정폭은 DejaVu Sans Mono (한글은 본고딕). 시스템에서 본명조 = Noto Serif CJK KR, 본고딕 = Noto Sans CJK KR. 없으면 `fc-list :lang=ko family`로 설치된 글꼴을 확인한다.
- 표는 booktabs, 긴 텍스트 열은 tabularx(`Y` 열). 그림과 표는 `[H]`로 본문 위치에 고정한다.
- 긴 파일명·코드명은 `\code{}`(`\path`, xurl)로 쓴다. 캡션 안에서는 `\texttt{}`와 `\_`를 쓴다 (`\path`는 캡션에서 오류). 한글이 든 파일명은 `\texttt{...\allowbreak...}`로 쓴다.
- 코드 블록은 listings 대신 fancyvrb의 `Verbatim`을 쓴다 (한글 주석 안정성).
- 수식 기호 설명은 `symbols` 환경, 용어 정의는 `terms` 환경을 쓴다.

```latex
\begin{equation}\label{eq:flow}
  Q = AV
\end{equation}
\begin{symbols}
  \item $Q$: 유량 (m$^3$/s)
  \item $A$: 관 단면적 (m$^2$)
  \item $V$: 유속 (m/s)
\end{symbols}

\begin{terms}
  \item SMPL: 체형 계수와 관절 회전값을 넣으면 사람 몸 형상과 관절 24개의 위치를 계산하는 표준 인체 모델
\end{terms}
```

## 기본 서식 제목부
`base.tex`의 제목부 형태만 쓴다: 제목 한 줄, 그 아래 "작성일 | 기준" 한 줄.

## 학술 변형
- 기본 서식 위에 덮어쓰는 것: 문단 첫 줄 들여쓰기 1.5em(문단 간격 0), 제목 색 없음, `\maketitle` + `abstract`, "초록"·"참고문헌" 이름.
- 엔진·글꼴·`symbols`·`terms` 환경은 기본 서식 그대로 쓴다.
- 모르는 저자는 `\author{}`로 비운다. 별도 표지를 만들지 않는다.
- 수식은 `\label`/`\eqref`, 표·그림은 `\label`/`\ref`로 참조한다.
- 영어 문서면 `xetexko`와 한글 글꼴 설정 대신 `\setmainfont{Latin Modern Roman}`을 쓴다.

## 컴파일
- 두 번 컴파일한다: `latexmk -xelatex -interaction=nonstopmode -halt-on-error` 또는 xelatex 2회. 참고문헌이 있으면 BibTeX/Biber를 함께 돌린다.
- 컴파일 출력을 `.out`으로 리디렉션하지 않는다 (hyperref의 `.out` 파일을 덮어써 다음 컴파일이 깨짐).
- 모든 쪽을 `pdftoppm`으로 렌더링해 확인한다.
- .tex와 .pdf를 함께 전달한다. 컴파일할 수 없으면 그 사실을 밝히고 검증한 .tex만 전달한다.

## 점검
- [ ] 로그에 `!` 오류, Missing character, undefined reference/citation, 눈에 띄는 Overfull \hbox(약 5pt 초과) 없음
- [ ] 모든 쪽을 렌더링해 확인: 여백 밖 글자, 잘린 표, 겹친 그림 없음
- [ ] .tex와 .pdf를 함께 전달
