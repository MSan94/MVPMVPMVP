## MVP 패턴
- MVC의 단점을 보완하기 위해 만들어진 패턴
  - 뷰에서 컨트롤러의 역할까지 모두 담당하기에 뷰가 너무 거대해지고, 안드로이드 api에 종속되어 테스트가 힘들다.

## MVP란?
- MVP는 3가지 요소로 이루어져 있다.
  - Model : 데이터, 상태, 비즈니스 로직 담당
  - View : xml,View(Activity,Fragment)가 View에 해당하며, Presenter에 이벤트 전달
  - Presenter : View로 부터 받아온 이벤트를 처리하고 , Model 업데이트

## MVP 진행
- View에서 이벤트 발생
- View는 Presenter에 이벤트 전달
- Presenter에서 로직 처리
- Model update or Model getData
- Presenter에서 View 업데이트

## Google 제공 MVP 문서
https://github.com/android/architecture-samples/tree/todo-mvp-kotlin

