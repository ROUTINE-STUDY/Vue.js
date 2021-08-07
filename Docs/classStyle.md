# 클래스와 스타일 바인딩

데이터 바인딩의 일반적인 요구사항은 엘리먼트의 클래스 목록과 인라인 스타일을 조작하는 것입니다. 클래스와 스타일 모두 속성이므로, v-bind를 사용하여 처리할 수 있습니다.

## 사용방법

```html
<template>
  <h1 v-bind:class="{ active: isActive }" @click="activate">
    Hello Vue.js!(isActive = {{ isActive }})
  </h1>
  <h1 :class="{ active: isActive }" @click="activate">
    Hello Vue.js!(isActive = {{ isActive }})
  </h1>
</template>

<script>
export default {
  name: 'App',
  data() {
    return { isActive: false };
  },
  methods: {
    activate() {
      this.isActive = true;
    },
  },
};
</script>

<style>
h1 {
  color: blue;
}
.active {
  color: red;
  font-weight: bold;
}
</style>
```

class를 사용해 style을 넣을 때 보통은 class = 'style'의 형식으로 작성합니다.  
Vue.js에서는 v-bind:class(약어 -> :class)를 활용해서 객체를 전달하여 클래스를 동적으로 전환할 수 있습니다.  
위 코드는 active 클래스는 isActive의 진실성에 의해 결정되는 구문입니다.

![image](https://user-images.githubusercontent.com/74242937/128609954-1a7b0814-b935-4311-8a48-2d198397e8f5.png)

![image](https://user-images.githubusercontent.com/74242937/128609958-fc0c8cae-d260-4584-bd45-302a5da81b6c.png)

isActive의 값이 처음에는 false였지만 h1태그를 클릭함으로써 true로 변경되어 active 클래스가 활성화되는 모습입니다.  

:class에 더 많은 필드를 포함하면 다음과 같이 랜더링 됩니다.

```html
<template>
  <h1 :class="{ active: true, 'text-danger': false }" class="static">
    Hello Vue.js!
  </h1>
</template>
```
![image](https://user-images.githubusercontent.com/74242937/128609977-12b9f665-2bb4-4289-aaf9-bf5b3e097f1f.png)

class명을 작성할 때는 보통 - 와 \_를 사용하여 작명합니다. 이때 싱글쿼트를 감싸주면 문제없이 사용할 수 있습니다.

## 바인딩되는 속성이 많을 경우

:class 객체 구문에 이보다 많은 필드를 넣는다고 생각하면 코드의 가독성이 떨어질 수 있습니다. 이를 깔끔하게 해 줄 수 있는  것은 스크립트 data에 객체를 사용하여 사용하면 훨씬 깔끔하게 작성할 수 있습니다.

```html
<template>
  <h1 :class="classObject" class="static">Hello Vue.js!</h1>
</template>

<script>
export default {
  name: 'App',
  data() {
    return { classObject: { isActive: true, hasError: false } };
  },
  methods: {
    activate() {
      this.isActive = true;
    },
  },
};
</script>
```

## 배열 구문 활용하기

배열을 :class에 전달하여 클래스 목록을 적용할 수 있습니다.

```html
<template>
  <h1 :class="[activeClass, errorClass]">Hello Vue.js!</h1>
</template>

<script>
export default {
  name: 'App',
  data() {
    return { activeClass: 'active', errorClass: 'text-danger' };
  },
};
</script>
```

![image](https://user-images.githubusercontent.com/74242937/128610043-7536b7f5-dd22-43db-bf8d-945b1fda9b96.png)

클래스명을 반복해서 써야 할 때가 있다면 유용하게 사용할 수 있습니다.  

배열 안에서도 true, false를 활용할 수 있습니다.

1. 삼항 연산자 활용

```html
<div :class="[isActive ? active : '', errorClass]"></div>
```

- isActive가 true라면 active, false라면 클래스를 적용시키지 않는 것입니다.
- 
2. 배열 안에 객체 구문 활용

```html
<div :class="[{ active: isActive }, errorClass]"></div>
```

- isActive가 true라면 active 클래스 선언, isActive가 false라면 active 클래스 선언하지 않음

# 인라인 스타일 바인딩하기

## 인라인 스타일이란

style 태그를 사용하지 않고 스크립트와 html 태그에서 스타일을 적용하는 것을 말합니다.

```html
<template>
  <h1 :style="{ color: activeColor, fontSize: fontSize + 'px' }">
    Hello Vue.js!!
  </h1>
</template>

<script>
export default {
  name: 'App',
  data() {
    return { activeColor: 'red', fontSize: 30 };
  },
};
</script>

<style></style>
```

다음과 같이 랭더링 됩니다.

![image](https://user-images.githubusercontent.com/74242937/128610105-8762b4cf-158b-477a-b8c3-bf610633b8ac.png)

- :style 객체 구문에 css style을 작성합니다.
- style의 속성은 스크립트를 활용하여 바인딩합니다.

## 바인딩되는 속성이 많을 경우

위에서 했던 방식과 똑같으므로 자세한 설명은 하지 않고 코드만 보여드리겠습니다.

```html
<template>
  <h1 :style="styleObject">Hello Vue.js!!</h1>
</template>

<script>
export default {
  name: 'App',
  data() {
    return { styleObject: { color: 'red', 'font-weight': '100' } };
  },
};
</script>

<style></style>
```

- 위와 같이 객체를 활용하면 됩니다.

## 객체를 2개 이상 활용하기

:style의 문법에서 배열 구문을 사용하면 됩니다.

```html
<template>
  <h1 :style="[styleObject, bakcgroundStyle]">Hello Vue.js!!</h1>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      styleObject: { color: 'red', 'font-weight': '100' },
      bakcgroundStyle: { backgroundColor: 'blue' },
    };
  },
};
</script>

<style></style>
```

<hr>

참고문서: [Vue.js 공식문서](https://v3.ko.vuejs.org/guide/class-and-style.html#%E1%84%80%E1%85%A2%E1%86%A8%E1%84%8E%E1%85%A6-%E1%84%80%E1%85%AE%E1%84%86%E1%85%AE%E1%86%AB-2)
