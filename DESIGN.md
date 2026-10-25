# Design brief

## Screen purpose

- Primary action: 여행 일정 확인 및 관리
- Information priorities: 여행 지도와 일정, 예산 및 환율, 준비물 리스트, 여행 정보와 팁
- Left out on purpose: 원본에 없는 홍보 문구, 장식용 통계, 추가 애니메이션
- Required content: 일정 5일, 카테고리별 색상 핀 지도, 핀에서 일정으로 이동, 실제 숙소 예약 링크, 예산·환율 계산기, 준비물 체크리스트, 입국·교통·숙소·비상 정보, 일정 편집·내보내기·불러오기·인쇄 기능

## Layout

Layout: 문서 전체가 유일한 세로 스크롤 소유자이며, 상단 고정 헤더 아래에 가로 탭과 탭별 단일 콘텐츠 영역을 둔다. 모바일에서는 콘텐츠를 한 열로 재배치하고 탭만 가로 오버플로를 허용한다. 본문 내부에 별도 세로 스크롤 컨테이너를 만들지 않는다.

Layout: 여행 일정 화면 - 지도와 일자별 일정 목록을 하나의 세로 흐름으로 탐색 -> document stack (skipped: host unreachable); scroll owner: document; anti-patterns: 지도 내부가 페이지 스크롤을 가로채거나 일정 목록에 별도 세로 스크롤을 만들지 않는다.

## Existing visual system

원본 HTML의 Tailwind 기반 teal/amber/slate 색상, Noto Sans KR 서체, 4px 배수 간격, 8~16px 모서리 반경을 그대로 보존한다.

지도 핀은 기존 카테고리 배지의 의미색을 재사용한다: 이동 purple, 식사 amber, 숙소 emerald, 관광 blue. 핀 클릭 시 해당 일정 카드가 중앙으로 스크롤되고 짧은 teal 배경 강조가 적용된다. `prefers-reduced-motion`에서는 부드러운 스크롤 대신 즉시 이동한다.
