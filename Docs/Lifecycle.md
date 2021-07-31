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

### beforeMount

- craeted 라이프 사이클 단계 다음에 실행됩니다.
- render() 함수가 처음으로 실행되고 DOM에 인스턴스가 부착되기 전에 호출되는 단계입니다.

![image](https://user-images.githubusercontent.com/74242937/127744110-7972224b-2a25-4f56-b34b-2629c8eb5ea9.png)

### mounted

- beforeMount 라이프 사이클 단계 다음에 실행됩니다.
- DOM에 인스턴스가 부착되고 호출되고 접근이 가능한 시점이기 때문에 화면 요소를 제어하는 로직을 수행하기 좋은 단계입니다.
- 단, mounted는 자식 컴포넌트가 마운트 되었음을 보장하지 않습니다. 이를 해결하기 위해서 $nextTick() 함수를 사용합니다.

![image](https://user-images.githubusercontent.com/74242937/127744129-03cd3e2a-dc28-4701-ba27-a29d61ba638b.png)

### beforeUpdate

- 컴포넌트에서 사용되는 data의 값이 변해서 DOM에도 그 변화를 적용시켜야 할 때, 변화 직전에 호출되는 라이프 사이클입니다.
- 컴포넌트에서 data가 변경될 때 호출됩니다. 이 말은 data가 변경되지 않는다면 호출되지 않는다는 말을 의미합니다.

![image](https://user-images.githubusercontent.com/74242937/127744140-7296f2eb-3c92-4fa0-a8a6-c97d941e5899.png)

![image](https://user-images.githubusercontent.com/74242937/127744143-8da51076-0e84-43a1-8462-d7ad307abaec.png)

- 위 사진은 아무것도 찍히지 않았지만 밑에 사진에는 data가 출력되었음을 알 수 있습니다.
- beforeUpdate에서는 data 값을 변경하는 로직을 사용하는 것을 추천드립니다.

![image](https://user-images.githubusercontent.com/74242937/127744163-c9a74949-578b-43cd-9814-fc4557afa783.png)

### updated

- data가 변경되고 나서 가상 DOM으로 다시 화면을 그리고 나면 실행되는 라이프 사이클 단계입니다.
- 변경된 data의 DOM과 관련된 로직은 updated에서 추가하는 것을 추천드립니다.
- 단, updated에서 data 값을 변경하게 된다면 무한 루프에 빠질 수 있기 때문에 조심하셔야 합니다.

![image](https://user-images.githubusercontent.com/74242937/127744177-2f27856f-8c10-45fe-9d93-2a5a4946fa5d.png)

### beforeDestroy

- Vue 인스턴스가 파괴되기 직전에 호출되는 라이프 사이클 단계입니다.
- 이 단계에서는 아직 인스턴스에 접근할 수 있기 때문에 Vue 인스턴스의 데이터를 삭제하기 좋은 단계입니다.

### destroyed

- Vue 인스턴스가 파괴되고 나서 호출되는 라이프 사이클 단계입니다.
- Vue 인스턴스에 정의한 모든 속성이 제거되고 하위에 선언한 인스턴스들 또한 모두 파괴됩니다.

참고: [Do it Vue.js 입문](http://www.yes24.com/Product/Goods/58206961)[공식문서](https://v3.ko.vuejs.org/api/options-lifecycle-hooks.html#deactivated)

