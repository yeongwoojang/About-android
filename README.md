## 안드로이드 공부용 레포지토리입니다.

### 안드로이드 4대 컴포넌트
* **액티비티(Activity)**
* **서비스(Service)**
* **방송 수신자(BroadCast Receiver)**
* **콘텐트 제공자(Content Provider)**

1. **액티비티(Activity) :**
사용자가 어플리케이션과 상호작용하는 화면이며 모든 안드로이드 어플리케이션은 액티비티로 구성되어있다. 간단히 말하면 사용자와의 상호작용을 담다아는 인터페이스(UI..?)라고 할 수 있다.
안드로이드 어플리케이션은 반드시 하나이상의 액티비티를 포함하고 있는데 "안드로이드 스튜디오"를 통해 프로젝트를 생성하면 MainActivity가 자동으로 생성되어 어플리케이션의 조건을 만족시킨다.
그리고 이 액티비티는 생명주기(Life Cycle)를 가지는데 액티비티의 활동에 따라 각각의 콜백함수를 재정의 하여 원하는 기능을 구현할 수 있다.

2. **서비스(Service) :**
서비스는 사용자와 직접적으로 상호작용하는 요소는 아니고 주로 **백그라운드(Background)** 에서 어떠한 작업을 처리하기 위해 사용한다. 사용자의 UI를 방해하지 않으면서 백그라운드에서 작업을 처리하기 때문에 별도의 Thread에서 동작하는 것처럼 착각할 수 있지만 **서비스는 MainThread** 에서 동작하기 때문에 **서비스 내에서 별도의 스레드를 생성** 하여 작업을 처리해야 한다.
서비스는 애플리케이션이 종료되어도 백그라운드에서 계속 동작한다.

3. **방송 수신자(BroadCast Receiver) :**
브로드캐스트 리시버는 안드로이드 OS로부터 발생하는 각종 이벤트와 정보를 받아와 핸들링하는 컴포넌트이다. **ex) : 기기 부팅시 앱초기화, 네트워크 끊김, 배터리 부족 알림, 문자 수신 등등**
즉, 안드로이드 OS에서 문자 메시지가 오면 모든 앱에 메시지가 왔다는 하나의 정보를 Broadcast해준다. 쉽게 말해서 어떠한 이벤트가 발생했다고 방송해준다 라고 이해하면 될 것 같다.
이 방송으로 인해 받은 정보(이벤트)를 Broadcast Receiver를 구현하면 처리할 수 있다.

4. **콘텐츠 제공자(Content Provider) :**
콘텐츠 제공자는 데이터를 관리하고 다른 어플리케이션의 데이터를 제공하는데 사용되는 컴포넌트이다. 쉽게 이야기하면 A와 B 사이에 데이터를 공유한다고 이해하면 될 것 같다. 이는 
SQLite 등을 통해 데이터를 관리하며 인텐트(Intent)를 통해 작은 데이터들을 공유한다면 콘텐츠 프로바이더는 음악, 사진등 용량이 큰 데이터들을 공유하는데 적합하다.

## 안드로이드 생명주기(Android LifeCycle)
**onCreate() ▶ onStart() ▶ onResume() ▶ onPause() ▶ onStop() ▶ onDestroy순으로 실행.**  
_상황에 따라 onRestart() 메소드가 호출되기도 한다._  
* **onCreate() :** 액티비티가 생성될 때 호출되며 UI 초기화에 사용된다.
* **onStart() :** 액티비티가 사용자에게 보여지기 바로 전에 호출된다.
* **onRestart() :** 액티비티가 멈췄다가 다시 시작되기 바로전에 호출된다.
* **onResume() :** 액티비티가 사용자와 상호작용하기 바로 전에 호출된다.
* **onPause() :** 다른 액티비티가 보여질 때 호출된다. 데이터 저장, 스레드 중지 등의 처리를 하기에 적당하다.
* **onStop() :** 액티비티가 더이상 사용자에게 보여지지 않을 때 호출된다. 메모리가 부족할 경우에는 호출되지 않을 수도 있다.
* **onDestroy :** 액티비티가 소명될 때 호출된다. 액티비티 내에서 **finish()** 를 호출하거나 시스템이 메모리 확보를 위해 액티비티를 제거할 때 호출된다.  

이러한 메소드들은 콜백함수로써 해당이벤트에 대한 원하는 작업을 재정의 해주면 된다.
