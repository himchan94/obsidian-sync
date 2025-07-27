### 3.2. 반응형 시스템

```ts

const 변수명 = ref(값);
변수명.value = 새로운_값;

```

### 3.3 반응형 데이터를 준비하는 여러가지 방법

원의 넓이를 DOM에 렌더링 하려고 한다면?


```ts

{{PI * radius * radius}}

```
<mark style="background: #FF5582A6;">위처럼 mustache 안에 공식을 넣어도 동작하지만 Vue의 코딩 규약에서는 머스태시 구문 내에 식을 작성하는 것을 지양하라고 적혀있다.</mark>

