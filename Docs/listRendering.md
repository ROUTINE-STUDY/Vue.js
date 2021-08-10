# v-for

v-for 디렉티브를 사용하여 배열을 기반으로 리스트를 렌더링 한 수 있스니다.

```html
<template>
  <ul>
    <li v-for="framework in frameworks" :key="framework">{{ framework }}</li>
  </ul>
</template>

<script>
export default {
  name: 'App',
  data() {
    return { frameworks: ['React', 'Vue.js', 'Angular'] };
  },
  methods: {
    handler() {
      this.isShow = !this.isShow;
    },
  },
};
</script>

<style>
li {
  font-size: 20px;
}
</style>
```

![image](https://user-images.githubusercontent.com/74242937/128885915-cc78bc3d-83f2-4e11-98d8-dc0d6309dc58.png)

v-for 디렉티브는 item in items 형태로 특별한 문법이 필요합니다. 여기서 items는 원본 데이터 배열이고 item은 반복되는 배열 엘리먼트의 별칭입니다. 또한 v-for를 사용할 때는 :key 속성을 사용해야 합니다.

## :key

key는 Vue가 노드를 식별하는 일반적인 메커니즘이기 때문에 v-for와 특별히 연관되지 않는 다른 용도로도 사용됩니다.

## v-for의 index

v-for 디렉티브는 item in items에서 (item, index) in items 형태로 작성한다면 다음과 같이 나타납니다.

```html
<template>
  <ul>
    <li v-for="(framework, index) in frameworks" :key="index">
      {{ framework }} - {{ index }}
    </li>
  </ul>
</template>
```

![image](https://user-images.githubusercontent.com/74242937/128886120-acc668e4-d089-4811-902e-2cd28e6efa2d.png)

index는 이름을 바꿔서 사용하셔도 상관없습니다. 이는 배열의 인덱스를 가리킵니다. 또한 :key는 고유한 내용을 작성해야 하므로  index를 넣는 것을 추천드립니다.

## v-for 객체 활용

v-for를 사용하여 객체의 속성을 반복할 수도 있습니다.

```html
<template>
  <ul>
    <li v-for="framework in frameworks" :key="framework.id">
      {{ framework.name }} - {{ framework.id }}
    </li>
  </ul>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      frameworks: [
        { name: 'React', id: 0 },
        { name: 'Vue.js', id: 1 },
        { name: 'Angular', id: 2 },
      ],
    };
  },
  methods: {
    handler() {
      this.isShow = !this.isShow;
    },
  },
};
</script>

<style>
li {
  font-size: 20px;
}
</style>
```

