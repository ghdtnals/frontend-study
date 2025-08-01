# Q: 브라우저 렌더링 원리에 대해 설명해주세요.

사용자가 요청한 데이터를 브라우저가 받아 화면에 나타내는 과정은 브라우저 내부의 렌더링 엔진이 담당합니다.
렌더링 엔진은 HTML과 CSS를 파싱하여 각각 DOM 트리와 CSSOM 트리를 생성하고, 이를 결합해 렌더 트리를 구성합니다.
렌더 트리를 바탕으로 요소의 위치와 크기를 계산한 뒤, 시각적 요소를 그리는 페인트와 페인트 레이어를 합치는 컴포지팅 과정을 거쳐 최종적으로 웹 페이지가 화면에 나타납니다.

다만, JavaScript는 렌더링 엔진이 아닌 자바스크립트 엔진에 의해 실행됩니다.
HTML 파서는 <script> 태그를 만나면 자바스크립트 엔진에 제어를 넘기고, 파싱을 일시 중단한 채 해당 스크립트가 로드되고 실행될 때까지 기다립니다.
스크립트 실행이 완료되면, 중단했던 위치부터 다시 HTML 파싱을 이어가며 DOM 트리를 생성합니다.

## 💬 예상되는 꼬리 질문?

### 1. JavaScript 실행으로 인한 렌더링 지연을 어떻게 해결할 수 있을까?
   JavaScript가 렌더링을 지연시키지 않도록, body 태그 하단에 script를 위치시키거나 defer와 async 속성을 사용해 비동기 로딩을 적용하는 것이 좋다.

   #### 1-1. defer와 async란?

### 2. 렌더링 최적화를 위한 주요 방법은?
   reflow와 repaint 발생을 최소화하고, JavaScript는 상황에 맞게 defer와 async 속성을 사용해 로딩을 최적화할 수 있다.
   또한, lazy loading을 적용하면 사용자 시점에 따라 이미지를 지연 로딩하여 초기 페이지 렌더링 속도를 개선할 수 있다.

   #### 2-1. reflow와 repaint란?
   reflow: 요소의 크기나 위치가 변화했을 때, 브라우저가 전체 또는 일부의 레이아웃을 다시 계산하는 과정
   repaint: 요소의 레이아웃에는 영향을 주지 않지만, 요소의 시각적 스타일이 변화했을 때, 브라우저가 해당 요소를 다시 화면에 그리는 과정
   #### 2-2. reflow와 repaint 과정을 최소화하는 방법은?
