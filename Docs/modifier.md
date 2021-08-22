## v-model 수식어

1. .lazy

기본적으로, v-model은 각 input 이벤트 후 입력과 데이터를 동기화 합니다. lazy 수식어를 추가하여 change이벤트 이후에 동기화 할 수 있습니다. 즉, 글자 또는 문장을 입력한 후에 Enter 또는 포커스가 사라졌을때 문구가 나타나게 됩니다.

```html
<template>
  <h1>{{ msg }}</h1>
  <input type="text" v-model.lazy="msg" /> 
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
```

2. .number

사용자 입력이 자동으로 숫자로 형변환 되기를 원하면, v-model이 관리하는 input에 number 수식어를 추가하면 됩니다.

```html
<template> 
  <h1>{{ msg }}</h1> 
  <input type="text" v-model.number="msg" /> 
</template>
<script>
  export default {
    name: 'App',
    data() {
      return {
        msg: 0,
      };
    },
    watch: {
      msg() {
        console.log(typeof this.msg);
      },
    },
  }; 
</script>
```

![1](https://user-images.githubusercontent.com/74242937/130352216-9c14d92e-9a19-4e99-a6b8-5535e16db488.png)

![2](https://user-images.githubusercontent.com/74242937/130352219-4276763b-e1fd-4e16-9c4e-9e36e6a24804.png)

숫자를 받아서 로직을 처리해야 할 경우에 유용하게 쓰일 것 같습니다.

3. .trim

사용자가 입력한 내용에서 자동으로 앞뒤 공백을 제거하는 트림처리가 되길 바란다면, v-model이 관리하는 input에 trim 수식어를 추가하면 됩니다.

```html
<template> 
  <h1>{{ msg }}</h1> 
  <input type="text" v-model.trim="msg" />
</template>

<script> 
  export default {
    name: 'App',
    data() {
      return {
        msg: ' Hello Vue.js!!',
      };
    },
  }; 
</script>
```

![3](https://user-images.githubusercontent.com/74242937/130352237-4915b99d-fa97-46b2-b2c3-6b8f2732f0f6.png)

이와 같이 input 태그에는 공백이 있지만 출력하는 h1태그에는 앞뒤에 공백이 사라져서 보이는 것을 알 수 있습니다.
