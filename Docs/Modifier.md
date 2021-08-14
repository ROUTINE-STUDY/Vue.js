## 이벤트 수식어

이벤트 핸들러 내부에서 event.preventDefault() 또는 event.stopPropagation()를 호출하는 것은 매우 보편적인 일입니다. 메서드 내에서 쉽게 이 작업을 할 수 있지만, DOM 이벤트 세부 사항을 처리하는 대신 데이터 로직에 대한 메서드만 사용할 수 있으면 더 좋습니다.

이 문제를 해결하기 위하여, Vue.js는 v-on이벤트에 이벤트 수식어를 제공합니다. 수식어는 점으로 된 접미사입니다.

### 사용 방법

```html
<template>
  <a href="https://google.co.kr" target="_blank" @click.prevent="handler" >Google</a > 
</template> 

<script>
  export default {
    name: 'App',
    methods: {
      handler() {
        console.log('Google'); 
      }, 
    }, 
  }; 
</script>

<style></style>
```

![image](https://user-images.githubusercontent.com/74242937/129445920-8cfb28e7-2a90-4855-ac10-7e61d988c0ca.png)

위 예제처럼 @click. prevent(함수 안에 event.preventDefault와 같은 기능)로 체이닝 하면 사용하실 수 있습니다.  
다른 수식어 들은 간단한 설명만 작성하겠습니다.

- .stop: 클릭 이벤트 전파를 중단합니다.
- .capture: 이벤트 버블링의 반대되는 기능. 즉, 내부 엘리먼트를 대상으로 하는 이벤트가 해당 엘리먼트에서 처리되기 전에 먼저 처리합니다.
- .self: event.target과 event.currentTarget이 동일한 경우에만 트리거를 처리합니다.
- .once: 클릭 이벤트는 단 한 번만 처리합니다.
- .passive: 함수의 로직 완료를 기다리지 않고 화면의 행동을 먼저 취합니다. 성능 향상을 기대할 수 있습니다.

## 키 수식어

키 수식어는 input 태그 같이 키를 눌러서 사용할 때 활성화되는 이벤트입니다.
```html
<template>
  <input type="text" @keydown="handler" />
</template>

<script>
export default {
  name: 'App',
  data() {
    return {};
  },
  methods: {
    handler(event) {
      console.log(event.key);
    },
  },
};
</script>

<style></style>
```

![image](https://user-images.githubusercontent.com/74242937/129445965-e8c01248-fbc2-4ba2-aa2f-099a1fa87f36.png)

- 한글 입력 시에는 Process가 출력됩니다.

이와 같은 이벤트를 간단하게 사용하기 위해서 @keydown.enter=""를 사용하시면 Enter를 눌렀을 때 똑같이 이벤트가 작동합니다.

## 키 명령어

Vue는 가장 흔히 사용되는 키에서 명령어를 제공합니다.

- .enter
- .tab
- delete("Delete"와 "Backspace" 키 모두를 캡처합니다.)
- .esc
- .space
- .up
- .down
- .left
- .right

## exact 수식어

.exact 수식어는 다른 시스템 수식어와 조합해 그 핸들러가 실행되기 위해 정확한 조합이 눌러야 하는 것을 요구합니다.

```html
<!-- 아래코드는 Alt 또는 Shift와 함께 눌렀을 때도 실행됩니다.-->
<button @click.ctrl="onClick">A</button>
<!-- 아래코드는 Cntl키만 눌려져 있을 때 실행됩니다.-->
<button @click.ctrl.exact="onCtrlClick">A</button>
<!-- 아래 코드는 시스템 키가 눌리지 않은 상태인 경우에만 작동합니다.-->
<button @click.exact="onClick">A</button>
```

## 마우스 버튼 수식어

- .left
- .right
- .middle
