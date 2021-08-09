## v-if

v-if 디렉티브는 조건에 따라 블록을 렌더링 할 때 사용합니다. 블록은 디렉티브의 표현식이 true 값을 반환할 때만 렌더링 됩니다.

```html
<template>
  <button @click="handler">Click</button>
  <h1 v-if="isShow">Hello Vue.js!!</h1>
</template>

<script>
export default {
  name: 'App',
  data() {
    return { isShow: true };
  },
  methods: {
    handler() {
      this.isShow = !this.isShow;
    },
  },
};
</script>

<style></style>
```

![image](https://user-images.githubusercontent.com/74242937/128674871-ceb57538-e871-4800-a58e-67f0dffaded1.png)

isShow는 true이고 Click 버튼을 클릭하면 true와 false가 매번 바뀌는 예제입니다.  
첫 화면에는 isShow가 true이기 때문에 DOM에 나왔고 클릭 후에는 h1태그가 <!-- v-if -->으로 변환됩니다.

## v-else

v-if에서 조건이 맞지 않는다면 v-else가 있는 태그가 DOM에 표시됩니다.

```html
<template>
  <button @click="handler">Click</button>
  <h1 v-if="isShow">Hello Vue.js!!</h1>
  <h1 v-else>Goodbye Vue.js!!</h1>
</template>
```

![image](https://user-images.githubusercontent.com/74242937/128674950-11398b12-bacb-4d99-a41f-9def45491d0b.png)

isShow가 true일 때 'Hello Vue.js!!'의 태그가 DOM에 나타나고, false 일 때는 'Goodbye Vue.js!!'가 DOM에 나타나게 됩니다.

## v-if, v-else-if, v-else 사용 시 주의할 점

v-if, v-else-if, v-else 디렉티브를 사용 시 태그 중간에 관련 없는 디렉티브가 있다면 오류가 나타나게 됩니다.

```html
<template>
  <button @click="handler">Click</button>
  <h1 v-if="isShow">Hello Vue.js!!</h1>
  <!-- 'v-else' directives require being preceded by the element which has a 'v-if' or 'v-else-if' directive -->
  <h2>test</h2>
  <h1 v-else>Goodbye Vue.js!!</h1>
</template>
```

## v-show

v-show는 v-if와 매우 유사한 디렉티브입니다. else 구문은 없지만 마찬가지로 true와 false로 화면에 출력할지 안 할지 정할 수 있습니다.

```html
<template>
  <button @click="handler">Click</button>
  <h1 v-show="isShow">Hello Vue.js!!</h1>
</template>
```

사진의 개발자 도구를 보시면 h1 태그에 style="display: none"이 없었다가 생긴 것을 알 수 있습니다. v-show는 display 속성만 전환하며 항상 DOM에 랜더링 돼서 남아있는 것을 알 수 있습니다.

## v-if와 v-show의 차이점

v-if는 초기 랜더링 시, 조건이 false라면 아무 작업도 하지 않고 화면을 출력하게 됩니다. 그 이후에 조건이 true로 변해야지만 DOM에 랜더링 하게 됩니다.  
v-show는 조건이 true이든 false든 상관없이 무조건 DOM에 랜더링 됩니다.  
이를 보면 알 수 있는 것은 v-if는 전환 비용이 높고, v-show는 초기 랜더링 비용이 높습니다. 개발할 때 각각 상황에 맞게 사용해야 웹에 성능을 저하시키지 않고 개발하실 수 있습니다.

<hr> 

참고: [Vue.js 공식문서](https://v3.ko.vuejs.org/guide/conditional.html#v-show)

