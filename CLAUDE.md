# CLAUDE.md

Minsoo Song 개인 학술 홈페이지(`ecoses042.github.io`) 저장소에서 작업할 때의 지침.

## 저장소

Jekyll + GitHub Pages 정적 사이트. `main` 에 push 하면 <https://ecoses042.github.io> 에 배포된다.
레이아웃은 researcher(Ankit Sultana) 테마 기반이며, 원본은 `jglovier/resume-template` 포크다.

## 구조

페이지는 `index.md` **하나뿐이다.** `{% include %}` 와 `site.data` 는 저장소 전체에서 사용하지 않는다.

```
index.md                ← 사이트 콘텐츠 전부
_config.yml             ← 제목·설명·URL·네비게이션(nav)·푸터
_layouts/default.html   ← 유일한 레이아웃
css/main.scss → _sass/_style.scss → vars.scss, typography.scss, tables.scss
images/                 ← face.png, soongsil.png, soongsil_nlp.png
cv.tex → Minsoo_Song_CV.pdf
```

2026-09 에 업스트림 템플릿 잔재(`_data/`, `_includes/`, `_assets/`, `_layouts/resume.html`,
`_sass/{_base,_layout,_mixins,_normalize,_resume,_variables}.scss`)를 전부 제거했다.
**이 디렉터리들을 되살리지 말 것.** `_style.scss` 가 import 하는 것은 `vars.scss` 이지 `_variables.scss` 가 아니다.

## 수정 지점

| 바꾸려는 것 | 파일 |
| --- | --- |
| 논문·특허·경력·학력·소개 | `index.md` |
| 상단 메뉴, 사이트 제목·설명 | `_config.yml` |
| 스타일 | `_sass/_style.scss` |
| CV | `cv.tex` 수정 → 컴파일 → `Minsoo_Song_CV.pdf` 덮어쓰기 |

`index.md` 는 마크다운 안에 raw HTML(`<a>`, `<br>`, `<img class="affiliation-logo">`)을 섞어 쓴다.
새 내용을 넣을 때 이 방식을 그대로 따르고, 순수 마크다운으로 바꾸려 하지 말 것.

## 콘텐츠 표기 규칙

Publications 항목:

```markdown
* **논문 제목**<br>
  [<u>Minsoo Song</u>](https://openreview.net/profile?id=~Minsoo_Song2), [공저자](프로필 링크), ...<br>
  *학회명*, published Month D, YYYY.
```

- 본인 이름은 항상 `<u>Minsoo Song</u>` 로 밑줄 처리
- 공저자는 가능하면 OpenReview 프로필로 링크
- 최신 항목이 위로 오도록 정렬
- 특허는 Publications 아래 `## Patents` 섹션에 둔다 (아직 미생성 — `cv.tex` 에는 국내 출원 2건이 이미 있음)

## 논문 / 특허 반영 절차 ★

사용자가 논문이나 특허 내용을 붙여넣으면 **반드시 이 순서를 지킨다.**

1. **초안만 제시** — 위 표기 규칙에 맞춰 정리해 채팅으로 보여준다. 이 단계에서 파일을 수정하지 않는다.
2. **검토받기** — 저자 순서, 학회/저널명, 게재일, 링크(OpenReview·DOI·출원번호)를 확인받는다.
3. **반영** — 승인 후에만 `index.md`(필요 시 `cv.tex`)를 수정한다.

**커밋과 push 는 사용자가 명시적으로 요청할 때만 한다.** 파일 수정까지가 기본 범위다.

## 로컬 실행

```bash
bundle install
bundle exec jekyll serve   # http://localhost:4000
```

## 알려진 이슈

- `favicon.png` 가 어느 레이아웃에서도 참조되지 않는다. favicon `<link>` 가 삭제된 `_includes/head.html` 에만 있었기 때문. 살리려면 `_layouts/default.html` 의 `<head>` 에 추가할 것.
- 이 저장소는 OneDrive 폴더에 있다. 클라우드 전용 파일 상태면 도구에서 파일 읽기와 git 이 실패한다. 폴더 속성에서 "이 장치에 항상 유지"를 켜면 해결된다.
