## 안드로이드 공부용 레포지토리입니다.

### 안드로이드 4대 컴포넌트
* **액티비티(Activity)**
* **서비스(Service)**
* **방송 수신자(BroadCast Receiver)**
* **콘텐트 제공자(Content Provider)**

1. **액티비티(Activity)**
사용자가 어플리케이션과 상호작용하는 화면이며 모든 안드로이드 어플리케이션은 액티비티로 구성되어있다. 간단히 말하면 사용자와의 상호작용을 담다아는 인터페이스(UI..?)라고 할 수 있다.
안드로이드 어플리케이션은 반드시 하나이상의 액티비티를 포함하고 있는데 "안드로이드 스튜디오"를 통해 프로젝트를 생성하면 MainActivity가 자동으로 생성되어 어플리케이션의 조건을 만족시킨다.
그리고 이 액티비티는 생명주기(Life Cycle)를 가지는데 액티비티의 활동에 따라 각각의 콜백함수를 재정의 하여 원하는 기능을 구현할 수 있다.

2. **서비스(Service)**
