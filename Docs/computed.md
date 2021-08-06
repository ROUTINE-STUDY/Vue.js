# computed

연결된 data의 값이 변경되었을 때, 복잡한 계산식을 계산해서 값을 캐싱해서 return해주는 속성입니다.

## 캐싱

값을 계산하여 잠시 동안 저장해두는 것을 의미합니다.

```html
<template>
  <p>{{ msg }}</p>
  <button @click="changeMag">문자열 뒤집기</button>
  <hr />
  <p v-if="isDone">{{ reverseString }}</p>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      msg: 'Hello Vue.js!!',
      isDone: false,
    };
  },
  computed: {
    reverseString() {
      console.log('computed');
      return this.msg
        .split('')
        .reverse()
        .join('');
    },
  },
  methods: {
    changeMag() {
      console.log('methods');
      if (this.isDone) this.isDone = false;
      else this.isDone = true;
    },
  },
};
</script>

<style>
p {
  padding: 10px;
  text-align: center;
  font-size: 20px;
}
button {
  display: block;
  margin: 0 auto;
}
</style>
```

위 예제 코드는 'Hello Vue.js!!' 문자열을 뒤집어주는 코드입니다.  
함수를 살펴보면 reverseString()은 msg의 문자열을 뒤집어주는 열할, changeMsg()는 isDone의 boolean 값을 바꿔주기만 합니다.

<hr />

예제 코드를 실행하면 나오는 첫 화면입니다.  
여기서 문자열 뒤집기 버튼을 클릭하면 'Hello Vue.js!!'가 뒤집어진 문자열이 화면에 나타나게 됩니다.

![image](https://user-images.githubusercontent.com/74242937/128501541-286bdd2c-4ee3-4a1a-80f5-0e2e3f0df80f.png)

![image](https://user-images.githubusercontent.com/74242937/128501658-9240afa4-2c48-4864-95da-d129524315c7.png)

이때 콘솔 창을 확인해보면 methods와 computed가 출력된 것을 알 수 있습니다.

![image](https://user-images.githubusercontent.com/74242937/128501697-425d5db3-712d-47f5-b426-9f6ea64d290e.png)

![image](https://user-images.githubusercontent.com/74242937/128501702-c1b3dcb1-946b-4cd2-9f5d-9303bc9c5466.png)

위 사진을 보면 computed는 버튼을 최초의 클릭했을 때 한 번만 출력하고 그 후로는 methods만 계속 출력하는 것을 알 수 있습니다. 이는 computed의 연결된 data값이 변경하지 않는다면 호출하지 않는 것을 알 수 있습니다.

## computed와 methods의 차이

### computed

- 반드시 return 값이 존재해야합니다.
- 캐싱된 data만 사용합니다.
- 연결된 data가 변경되었승ㄹ 경우에만 계산합니다.
- 매개변수를 받을 수 없습니다.

### methods

- 명시적으로 호출될 때만 실행됩니다.
- 매개변수를 받을 수 있습니다.
