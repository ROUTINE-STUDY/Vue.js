# 라이프사이클이란?

모바일 앱을 비롯하여 일반적으로 애플리케이션이 가지는 생명주기를 말합니다.

![image](https://user-images.githubusercontent.com/74242937/127695754-d1f990f3-76f0-4a1e-9862-0f010006e58c.png)

### beforeCreate

- 인스턴스가 초기화된 직후, 데이터 관찰 및 이벤트/감시자(watcher) 설정 전에 동기적으로 호출됩니다. 즉 data 속성과 methods 속성이 아직 인스턴스에 정의되어 있지 않기 때문에 화면 요소에 접근할 수 없는 상태입니다.
![image](https://user-images.githubusercontent.com/74242937/127695815-036ca5f7-c050-4343-a2b4-780e38ae566f.png)

### created

- beforeCreate 라이프 사이클 단계 다음에 실행됩니다.
- 인스턴스가 생성된 후 동기적으로 호출됩니다. 이 단계에서 인스턴스는 data, computed, methods 등 정의되기 때문에 정의된 값에 접근하여 로직을 실행할 수 있습니다.
- 단, 화면요소에 부착되기 전이기 때문에 DOM 요소에는 접근할 수 없습니다.

![image](https://user-images.githubusercontent.com/74242937/127695890-555c4412-e0d5-4c0b-a957-6ad357702a16.png)
