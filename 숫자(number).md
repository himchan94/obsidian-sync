
C나 자바의 경우, 정수(소수점이 이하가 없는 숫자)와 실수(소수점 이하가 있는 숫자)를 구분해서 int, long, float, double 등과 값은 다양한 숫자 타입을 제공한다.

하지만 자바스크립트는 독특하게 하나의 숫자 타입만 존재한다.

- 숫자 타입은 배정밀도 64비트 부동소수점 형식을 따른다.
(https://vanillaani.tistory.com/6)
즉, 모든 수를 실수로 처리하며, 정수만 표현사기 위한 데이터 타입이 별도로 존재하지 않는다.

정수, 실수, 2진수, 8진수 16진수 리터럴은 모두 메모리에 배정밀도 64비트 부동소수점 형식의 2진수로 저장된다. 자바스크립트는 2진수, 8진수 16진수를 표현하기 위한 데이터 타입을 제공하지 않기 때문에 이들 값을 참조하면 모두 10진수로 해석된다.

```
var binary = 0b1000001;
var octal = 0o101;
var hex = 0x41;

console.log(binary); // 65;
console.log(octal); // 65;
console.log(hex); // 65;
console.log(binary === octal); // true
console.log(octal === hex); // true


```

**자바스크립트의 숫자 타입은 모든 수를 실수로 처리한다.**
(정수로 표시된다 해도 사실은 실수다.)


```
console.log(1 === 1.0) // true;
console.lg(3 / 2); // 1.5
```


숫자 타입은 추가적으로 세 가지 특별한 값도 표현할 수 있다.
- Infinity : 양의 무한대
- -Infinity: 음의 무한대
- NaN: 산술 연산 불가