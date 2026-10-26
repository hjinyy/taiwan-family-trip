# Design brief

## Screen purpose

- Primary action: 여행 일정 확인 및 관리
- Information priorities: 여행 지도와 일정, 예산 및 환율, 준비물 리스트, 여행 정보와 팁
- Left out on purpose: 원본에 없는 홍보 문구, 장식용 통계, 추가 애니메이션
- Required content: 일정 5일, 카테고리별 색상 핀 지도, 핀↔일정 양방향 이동, 버튼을 눌러 확인하는 현재 위치, 선택 일정의 Google 지도 길찾기, 실제 숙소 예약 링크, 예산·환율 계산기, 준비물 체크리스트, 입국·교통·숙소·비상 정보, 일정 편집·내보내기·불러오기·인쇄 기능

## Layout

Layout: 문서 전체가 유일한 세로 스크롤 소유자이며, 상단 고정 헤더 아래에 가로 탭과 탭별 단일 콘텐츠 영역을 둔다. 모바일에서는 콘텐츠를 한 열로 재배치하고 탭만 가로 오버플로를 허용한다. 본문 내부에 별도 세로 스크롤 컨테이너를 만들지 않는다.

Layout: 여행 일정 화면 - 지도와 일자별 일정 목록을 하나의 세로 흐름으로 탐색 -> document stack (skipped: host unreachable); scroll owner: document; anti-patterns: 지도 내부가 페이지 스크롤을 가로채거나 일정 목록에 별도 세로 스크롤을 만들지 않는다.

Layout: 여행 지도 헤더 - 제목과 상태를 먼저 읽고 현재 위치·선택 일정 길찾기를 오른쪽 도구 묶음에서 실행 -> cluster (skipped: host unreachable); scroll owner: document; anti-patterns: 작은 화면에서 버튼이 지도 밖으로 잘리거나 별도 세로 스크롤을 만들지 않는다.

## Existing visual system

원본 HTML의 Tailwind 기반 teal/amber/slate 색상, Noto Sans KR 서체, 4px 배수 간격, 8~16px 모서리 반경을 그대로 보존한다.

지도 핀은 기존 카테고리 배지의 의미색을 재사용한다: 이동 purple, 식사 amber, 숙소 emerald, 관광 blue. 핀 클릭 시 해당 일정 카드가 중앙으로 스크롤되고 짧은 teal 배경 강조가 적용된다. `prefers-reduced-motion`에서는 부드러운 스크롤 대신 즉시 이동한다.

일정 제목과 카드의 `지도에서 보기` 버튼은 같은 위치 선택 동작을 사용한다. 지도에서는 선택한 일정 핀만 더 크게 표시하고, 선택 상태를 상태 문구로도 알린다. 현재 위치는 사용자가 버튼을 누를 때만 브라우저 권한을 요청하며 저장하지 않는다. 길찾기는 선택한 목적지를 Google 지도 새 탭으로 열고 출발지는 Google 지도에서 결정한다. 지도 조작에는 추가 애니메이션을 넣지 않는다.
