# UpToDate Expert AI · 진료과별 활용 예시

진료과별 Expert AI 예시 프롬프트를 보여주는 GitHub Pages 사이트입니다. 케이스 데이터는 `cases.json` 하나로 관리되며, 페이지 내 관리자 패널에서 케이스와 진료과를 추가·삭제할 수 있습니다. 사용자 프롬프트 공유는 GitHub Issues(`prompt-share` 라벨)를 게시판으로 사용합니다.

## 배포 방법

1. GitHub에 새 저장소를 만들고 이 폴더의 파일을 모두 업로드합니다. (`index.html`, `cases.json`, `logo.png`, `README.md`)
2. 저장소 **Settings → Pages → Source**에서 `Deploy from a branch`, 브랜치 `main`, 폴더 `/ (root)`를 선택하고 저장합니다.
3. 1–2분 후 `https://<계정명>.github.io/<저장소명>/` 에서 페이지가 열립니다.

기본 브랜치가 `main`이 아니거나 커스텀 도메인을 쓰는 경우, `index.html` 상단의 `CONFIG` 객체에서 `owner`, `repo`, `branch`를 직접 지정하세요.

## 관리자 사용법

1. 페이지 하단의 **관리자** 버튼을 클릭합니다.
2. GitHub Fine-grained personal access token을 입력합니다.
   - 발급 위치: GitHub → Settings → Developer settings → Fine-grained tokens
   - Repository access: 이 저장소만 선택
   - Permissions: **Contents → Read and write**
3. 케이스 추가 / 진료과 추가 / 삭제 후 **저장 (커밋)**을 누르면 `cases.json`에 커밋됩니다.
4. 토큰은 브라우저에 저장되지 않으며 창을 닫으면 사라집니다. 토큰을 다른 사람과 공유하지 마세요.

관리자 패널 없이 GitHub에서 `cases.json`을 직접 수정해도 됩니다. 구조는 다음과 같습니다.

```json
{
  "specialties": [{ "id": "em", "name": "응급의학과" }],
  "cases": [
    {
      "specialtyId": "em",
      "vignette": "케이스 설명",
      "questions": [
        { "label": "질문", "text": "질문 내용" },
        { "label": "F/U 질문", "text": "후속 질문 내용" }
      ]
    }
  ]
}
```

## 프롬프트 공유 및 건의사항 동작 방식

- 페이지 하단 **프롬프트 공유하기** / **건의사항 보내기** 버튼 → 각 양식이 채워진 메일 작성 화면이 열립니다 (`mailto:` 방식이라 사용자 PC의 기본 메일 앱, 보통 Outlook이 실행됨)
- 수신 주소는 `jiseong.kim@wolterskluwer.com` 이며, `index.html`의 `CONTACT_MAIL` 상수에서 변경할 수 있습니다
- 메일 앱이 설정되지 않은 환경을 위해 주소 복사 버튼도 함께 제공됩니다
- 받은 프롬프트 중 좋은 것은 관리자 패널로 정식 케이스에 반영하면 됩니다

## 주의

- 메일 양식에 환자 식별 정보 제외 안내가 포함되어 있지만, 받은 메일에 환자 정보가 섞여 오는 경우가 있는지 확인해 주세요.
- 저장소를 Private으로 만들면 GitHub Pages는 유료 플랜에서만 동작하므로 Public 저장소를 권장합니다.
