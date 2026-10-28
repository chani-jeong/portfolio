# 정찬 포트폴리오

전북대학교 국제학부·인공지능전공(복수전공) 정찬의 개인 소개 사이트입니다.

- 사이트: https://chani-jeong.github.io/portfolio/
- 저장소: https://github.com/chani-jeong/portfolio
- 테마: [hugo-profile](https://github.com/gurusabarish/hugo-profile) (MIT License)

## 사용 도구와 버전

| 도구 | 버전 | 용도 |
|---|---|---|
| Hugo (extended) | 0.143.0 | 사이트 빌드 (`.github/workflows/hugo-pages.yml`의 `HUGO_VERSION`) |
| Python | 3.9 이상 | 빌드 보조 스크립트 `.github/pages_build.py` 실행 |
| Git | 최신 | 버전 관리, push |
| GitHub Actions / Pages | — | main push 시 자동 빌드·배포 |

## 내 컴퓨터에서 빌드하기 (macOS)

저장소 최상위 폴더에서 실행합니다. Hugo는 `.pages-tools/`에 받아 쓰며 이 폴더는 Git에서 제외됩니다.

```bash
# 1) Hugo 0.143.0 extended 내려받기 (처음 한 번)
mkdir -p .pages-tools/hugo
curl -fL https://github.com/gohugoio/hugo/releases/download/v0.143.0/hugo_extended_0.143.0_darwin-universal.tar.gz | tar -xz -C .pages-tools/hugo

# 2) 배포와 같은 방식으로 빌드 → public/ 폴더 생성
PATH="$PWD/.pages-tools/hugo:$PATH" python3 .github/pages_build.py --build

# 3) 개발 서버로 미리보기 → 터미널에 표시되는 주소 열기, 종료는 Ctrl+C
cd site && ../.pages-tools/hugo/hugo server --config hugo.yaml,pages.json --theme template --themesDir themes
```

## 수정할 파일 위치

| 바꾸고 싶은 것 | 파일 |
|---|---|
| 이름·소개·활동 요약·학력·메뉴 | `site/hugo.yaml` |
| 활동 상세 페이지 | `site/content/projects/*.md` |
| 이미지 | `site/static/images/` |
| 추가 스타일(초점 표시, 줄바꿈) | `site/static/css/custom.css` |
| 테마 화면 수정(카드, 첫 화면) | `site/layouts/` (테마 원본 `site/themes/template/` 위에 덮어씀) |
| 자동 배포 설정 | `.github/workflows/hugo-pages.yml` |

## 수정 후 재배포 확인

```bash
git add <수정한 파일>
git commit -m "변경 내용 설명"
git push
```

1. 저장소 **Actions** 탭에서 방금 push한 커밋의 `Deploy Hugo to GitHub Pages` 실행이 자동으로 시작되는지 확인
2. `build`, `deploy`가 모두 초록색 체크가 될 때까지 대기 (약 1~2분)
3. https://chani-jeong.github.io/portfolio/ 를 강력 새로고침(Cmd+Shift+R)해서 변경 반영 확인
