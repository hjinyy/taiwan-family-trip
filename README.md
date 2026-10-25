# 대만 가족여행 일정표

4박 5일 가족여행 일정, 예산, 준비물, 여행 정보를 한 페이지에서 확인하는 정적 사이트입니다. 여행 지도는 일정 카테고리별 색상 핀을 표시하며, 핀을 누르면 연결된 일정 카드로 이동합니다.

## GitHub Pages 배포

1. 저장소의 `Settings > Secrets and variables > Actions`에 `GOOGLE_MAPS_API_KEY`를 추가합니다.
2. `Settings > Pages > Build and deployment`에서 소스를 `GitHub Actions`로 선택합니다.
3. `main` 브랜치에 푸시하면 배포 워크플로가 사이트를 게시합니다.

Google Maps 키에는 `Maps JavaScript API` 제한과 `https://hjinyy.github.io/*` 웹사이트 리퍼러 제한을 적용하세요. 키는 Git 기록에 저장되지 않지만 브라우저용 지도 키는 배포된 페이지에서 보일 수 있으므로 리퍼러 제한이 필수입니다.
