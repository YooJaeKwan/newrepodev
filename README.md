Umami Analytics는 구글 애널리틱스(GA)를 대체할 수 있는 간단하고, 빠르며, 프라이버시를 중시하는 오픈소스 웹 분석 도구입니다.
공식 문서(docs)를 바탕으로, 초기 설정부터 데이터 분석까지 핵심 기능을 정리한 기본 매뉴얼입니다.
1. 시작하기 (Getting Started)
Umami는 크게 Umami Cloud(클라우드 버전)와 Self-hosted(직접 호스팅 버전) 두 가지 방식으로 사용할 수 있습니다. 사용법은 동일합니다.
1.1 웹사이트 추가 (Add Website)
 * Umami 대시보드에 로그인합니다.
 * Settings (설정) > Websites (웹사이트) 로 이동합니다.
 * + Add Website 버튼을 클릭합니다.
 * Name(표시 이름)과 Domain(예: example.com)을 입력하고 저장합니다.
1.2 트래킹 코드 설치 (Install Script)
웹사이트를 등록하면 고유한 트래킹 코드가 생성됩니다.
 * 생성된 웹사이트 항목의 Edit (수정/코드 아이콘) 버튼을 누릅니다.
 * Tracking Code 탭에서 스크립트를 복사합니다.
 * 분석하려는 웹사이트의 <head> 태그 안에 붙여넣습니다.
<!-- end list -->
<script defer src="https://cloud.umami.is/script.js" data-website-id="YOUR-WEBSITE-ID"></script>

> 참고: 스크립트를 넣는 순간부터 방문자 데이터가 자동으로 수집됩니다.
> 
2. 대시보드 및 지표 이해 (Metrics)
대시보드는 직관적으로 구성되어 있으며, 주요 지표는 다음과 같습니다.
| 지표 (Metric) | 설명 |
|---|---|
| Views (페이지뷰) | 웹사이트의 페이지가 조회된 총 횟수입니다. |
| Visitors (방문자) | 특정 기간 동안 방문한 고유(Unique) 사용자 수입니다. |
| Bounce Rate (이탈률) | 페이지에 들어왔다가 상호작용 없이 바로 나간 방문자의 비율입니다. |
| Visit Duration (체류 시간) | 방문자가 사이트에 머무른 평균 시간입니다. |
필터링 기능
대시보드 상단의 그래프나 하단의 리스트(국가, 브라우저 등)를 클릭하면, 해당 조건으로 데이터가 즉시 필터링됩니다. (예: Chrome을 클릭하면 크롬 사용자 데이터만 표시)
3. 이벤트 트래킹 (Tracking Events)
단순 페이지 조회 외에 "회원가입 버튼 클릭", "상품 구매" 등의 행동을 추적하는 기능입니다. 두 가지 방법이 있습니다.
3.1 CSS 클래스 사용 (코딩 없이 추적)
HTML 요소에 class를 추가하여 자동으로 이벤트를 수집합니다. 형식은 umami--<event>--<name> 입니다.
 * 형식: umami--{이벤트타입}--{이벤트이름}
 * 예시:
<!-- end list -->
<button class="umami--click--signup-button">
  회원가입
</button>

3.2 자바스크립트 함수 사용 (Javascript)
개발자가 코드 내에서 직접 이벤트를 전송할 때 사용합니다. window.umami.track 함수를 사용합니다.
// 단순 이벤트 이름 전송
umami.track('signup-button');

// 추가 데이터와 함께 전송 (동적 데이터)
umami.track('purchase', { product: 't-shirt', id: 123 });

4. 데이터 식별 및 관리 (Identify)
특정 사용자의 세션을 식별하여 더 정교한 데이터를 수집할 때 사용합니다 (예: 로그인한 사용자 추적).
umami.identify({
  email: 'user@example.com',
  name: '홍길동',
  id: 123
});

 * 이 기능은 세션 데이터를 사용자 정보와 연결합니다. (GDPR 등 프라이버시 정책에 유의해야 합니다.)
5. 리포트 기능 (Reports)
기본 대시보드 외에 심층 분석을 위한 도구입니다.
 * Insights (인사이트): URL, 브라우저, 국가 등 다양한 세그먼트를 조합하여 데이터를 깊게 파고듭니다.
 * Funnel (퍼널): 사용자가 목표 지점까지 도달하는 단계별 전환율을 분석합니다.
   * 예: 메인 페이지 -> 상품 상세 -> 장바구니 -> 결제 완료
 * Retention (리텐션): 방문자가 시간이 지남에 따라 얼마나 재방문하는지 분석합니다.
요약: Umami 사용 흐름
 * 설치: <head>에 스크립트 한 줄 추가.
 * 확인: 대시보드에서 실시간 방문자 확인.
 * 심화: 버튼 클릭 등 중요 행동에 umami.track() 추가.
 * 분석: 리포트 기능을 통해 사용자 행동 패턴 파악.
다음 단계로 무엇을 도와드릴까요?
 * "리액트(React)나 Next.js 프로젝트에 적용하는 구체적인 코드를 알려줘."
 * "도커(Docker)를 사용해서 직접 서버에 호스팅(Self-hosted)하는 방법을 알려줘."
 * "퍼널(Funnel) 리포트를 설정하는 예시를 보여줘."
