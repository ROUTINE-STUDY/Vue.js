## 이벤트 리스너

v-on 디렉티브는 @기호(약어)로, DOM 이벤트를 듣고 트리거 될 때와 JavaScript를 실행할 때 사용합니다.
- v-on:click="" == @click=""

```html
<template>
  <button @click="increase">Click!</button>
  <h1>{{ count }}</h1>
</template>

<script>
export default {
  name: 'App',
  data() {
    return { count: 0 };
  },
  methods: {
    increase() {
      this.count++;
    },
  },
};
</script>

<style></style>
```

![image](https://user-images.githubusercontent.com/74242937/128902950-740269cc-8474-40f3-ba99-2205938dab23.png)

위 예제는 버튼을 클릭하면 숫자가 1씩 오르는 예제입니다. button태그에 @click 이벤트에 increase 메서드를 연결하여 사용합니다.

## 메서드 이벤트 핸들러

JavaScript에서는 많은 이벤트 핸들러가 존재합니다. 하지만 로직이 복잡하기 때문에 JavaScript로 넘겨주기 어렵습니다. 그렇기 떄문에 이를 넘겨주기 위해서 함수의 파라미터에 event를 추가해 줍니다.

- handler(event)의 event는 다른 단어를 사용해도 상관없습니다.

```html
<template>
  <button @click="handler">Click!</button>
</template>

<script>
export default {
  name: 'App',
  data() {
    return { count: 0 };
  },
  methods: {
    handler(event) {
      console.log(event);
    },
  },
};
</script>

<style></style>
```

![image](https://user-images.githubusercontent.com/74242937/128903056-b4b96b1d-9d3a-411d-afa3-158001103dcb.png)

event를 넘겨주면 DOM에서 사용가능한 이벤트들이 나오게됩니다. 모든이벤트를 하나씩 설명하긴 너무 많으니 공부하면서 하나씩 찾아보는것을 추천합니다.

## 인라인 메서드 핸들러

DOM에 이벤트를 사용할 때 주의해야 할 사항이 있습니다. 위 예제에서 @click="handler('Hello')" 같이 인자를 넘겨주면 이벤트는 활성화되지 않습니다.

```html
<template> 
  <button @click="handler('Hello')">Click!</button> 
</template>
```

![image](https://user-images.githubusercontent.com/74242937/128903145-c2bc62c5-58cf-4229-b569-4e96ae9f4314.png)

인자를 넘겨줌으로써 이벤트객체는 사라지고 Hello가 출력됩니다. 이를 해결하기 위해 인자로 $envet를 같이 넣어주면 Hello와 이벤트객체가 같이 나오게 됩니다.

```html
<template>
  <button @click="handler('Hello', $event)">Click!</button>
</template>

<script>
export default {
  name: 'App',
  data() {
    return { count: 0 };
  },
  methods: {
    handler(msg, event) {
      console.log(msg);
      console.log(event);
    },
  },
};
</script>
```

![image](https://user-images.githubusercontent.com/74242937/128903220-aee4ed6a-ac2f-4630-8e0e-a7c6e16821ca.png)

## 복합 이벤트 핸들러

버튼 태그 한개에 두개의 함수를 사용하고 싶을때는 다음과 같이 사용합니다.

```html
<template>
  <button @click="handler(), handler2()">Click!</button>
</template>

<script>
export default {
  name: 'App',
  data() {
    return { count: 0 };
  },
  methods: {
    handler() {
      console.log('handler');
    },
    handler2() {
      console.log('handler2');
    },
  },
};
</script>
```

![image](https://user-images.githubusercontent.com/74242937/128903302-5b52b7dd-cf5b-40ad-bdb7-50d305d4eb88.png)

함수 사이에 콤마(,)를 작성해 주시면 됩니다. 여기서 주의할점은 함수명뒤에 ()를 붙여줘야 합니다. 붙이지 않고 사용하면 정상적으로 작동하지 않습니다.
