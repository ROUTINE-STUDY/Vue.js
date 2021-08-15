## v-model

v-model 디렉티브를 사용하여 input, checkbox 요소들에 양방향 데이터 바인딩을 생성할 수 있습니다. v-model 디렉티브는 input type 요소를 변경하는 올바른 방법을 자동으로 선택합니다.

```html
<template>
  <h1>{{ msg }}</h1>
  <input type="text" v-model="msg" /> 
</template> 

<script>
  export default {
    name: 'App', 
    data() {
      return {
        msg: '', 
      };
    },
  }; 
</script>

<style></style>
```

이처럼 input 태그에 v-model을 사용함으로써 msg의 데이터가 실시간으로 변해서 화면에 출력되는 것을 볼 수 있습니다. 하지만 여기에도 치명적인 단점이 존재합니다. 영어는 바로바로 업데이트되지만 한글은 모음과 자음이 결합했을 때 비로소 화면에 출력된다는 것입니다.

하지만 한글도 영어와 같이 한 글자씩 출력할 수 있게 할 수 있습니다.

@input을 통해서 msg에 바로 데이터를 업데이트해주는 문구를 작성합니다. $event.target.value를 글씨가 써질 때마다  msg에 할당하여 h1 태그에 출력하게 됩니다.

상황에 맞춰서 한글을 사용하지 않는다면 v-model을 사용하고, 한글을 사용한다면 :value와 @input을 활용하는 것을 추천드립니다.

![image](https://user-images.githubusercontent.com/74242937/129478210-efac03b1-5a20-434b-9290-b0e0199b392c.png)

## checkbox

```html
<template>
  <h1>{{ checked }}</h1>
  <input type="checkbox" v-model="checked" /> 
</template> 

<script>
export default {
  name: 'App',
  data() {
    return {
      checked: false,
    };
  },
};
</script>
```

이 밖에도 input 태그의 수 많은 type들을 활용할 수 있습니다. 
