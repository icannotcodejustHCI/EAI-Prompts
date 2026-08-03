# UpToDate Expert AI · 진료과별 활용 예시

진료과별 Expert AI 예시 프롬프트를 보여주는 GitHub Pages 사이트입니다. 케이스 데이터는 `cases.json` 하나로 관리되며, 페이지 내 관리자 패널에서 케이스와 진료과를 추가·삭제할 수 있습니다. 사용자 프롬프트 공유는 GitHub Issues(`prompt-share` 라벨)를 게시판으로 사용합니다.

## 배포 방법

1. GitHub에 새 저장소를 만들고 이 폴더의 파일을 모두 업로드합니다. (`index.html`, `cases.json`, `.github/ISSUE_TEMPLATE/prompt-share.md`, `README.md`)
2. 저장소 **Settings → Pages → Source**에서 `Deploy from a branch`, 브랜치 `main`, 폴더 `/ (root)`를 선택하고 저장합니다.
3. 1–2분 후 `https://<계정명>.github.io/<저장소명>/` 에서 페이지가 열립니다.
4. **Settings → General → Features**에서 **Issues**가 켜져 있는지 확인합니다. (프롬프트 공유 기능에 필요)

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

## 프롬프트 공유 동작 방식

- 페이지 하단 **내 프롬프트 공유하기** → 양식이 채워진 GitHub 이슈 작성 화면으로 이동 (GitHub 계정 필요)
- 이슈 템플릿에 의해 `prompt-share` 라벨이 자동 적용되며, 페이지가 이 라벨의 이슈를 불러와 하단에 표시합니다
- 공유된 프롬프트 중 좋은 것은 관리자 패널로 정식 케이스에 반영하면 됩니다
- 부적절한 공유는 이슈를 닫으면 페이지에서 사라집니다 (open 이슈만 표시)

## 주의

- 공유 안내에 환자 정보 비식별화 문구가 포함되어 있지만, 관리자도 이슈에 환자 식별 정보가 없는지 주기적으로 확인하는 것이 좋습니다.
- 저장소를 Private으로 만들면 GitHub Pages는 유료 플랜에서만 동작하고, Issues API 공개 조회도 막히므로 Public 저장소를 권장합니다.
