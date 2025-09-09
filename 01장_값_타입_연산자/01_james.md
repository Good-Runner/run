# [1장] 값, 타입, 연산자

## 1. NaN에 대해 설명해 주세요.

NaN은 정상적인 수치로 표현할 수 없는 결과를 나타내는 숫자 타입 값입니다. 주로 수학적 계산이 불가능할 때 생성됩니다. 문자열이나 다른 타입 값이 NaN으로 자동 변환되는 것은 아니며, NaN 자체가 숫자 타입이기 때문에 특정 상황에서만 발생합니다.

```js
console.log(0 / 0); // -> NaN
console.log(Math.sqrt(-1)); // -> NaN
```

NaN의 특징은 자기 자신과도 같지 않다는 점입니다.

```js
console.log(NaN === NaN); // -> false
```

## 2. 어떠한 값이 NaN인지 아닌지 확인하기 위해 NaN과 직접 비교할 수 있나요?

아니요, NaN은 자기 자신과도 같지 않은 특수한 값입니다. 따라서 NaN과 어떤 값을 비교하면 결과는 언제나 false입니다.

```js
const string = "Not a number";
console.log(NaN === string); // -> false
console.log(NaN === NaN); // -> false
```

어떠한 값이 NaN인지 확인하기 위해서는 Number.isNaN() 메서드를 사용해야 합니다.

```js
const x = 0 / 0;
const y = 90;
const z = "some string";

console.log(Number.isNaN(x)); // -> true
console.log(Number.isNaN(y)); // -> false
console.log(Number.isNaN(z)); // -> false
```

## 3. 자바스크립트의 논리 연산자의 동작 방식을 설명해 주세요.

자바스크립트에는 총 3개의 논리 연산자가 있습니다.

1. AND 연산자 `&&`

- 모든 피연산자가 true일 때 true를 반환합니다

```js
console.log(true && true); // -> true
console.log(true && false); // -> false
```

- 왼쪽 값이 falsy인 경우 왼쪽 값을, 아니면 오른쪽 값을 반환합니다

  ```js
  const x = 100;
  const y = 0;

  console.log(true && x); // -> 100
  console.log(false && x); // -> false
  console.log(y && x); // -> 0
  ```

2. OR 연산자 `||`

- 하나 이상의 피연산자가 true일 때 true를 반환합니다
  ```js
  console.log(true || false); // -> true
  ```
- 왼쪽 값이 truthy인 경우 왼쪽 값을, 아닌 경우 오른쪽 값을 반환합니다

  ```js
  const x = 100;
  const y = 0;

  console.log(true || x); // -> true
  console.log(false || x); // -> 100
  console.log(x || 1); // -> 100
  ```

3. NOT 연산자 `!`

- 피연산자의 불리언 값을 반전시킵니다
  ```js
  console.log(!true); // -> false
  console.log(!100); // -> false
  ```

## 4. 자바스크립트에서 문자열 타입 값과 숫자 타입 값을 연산할 수 있는 이유를 알려주세요.

자바스크립트는 동적 타입 언어이므로 각 값의 타입이 런타임 중 결정됩니다. 이러한 유연함 때문에 변수는 런타임 중 언제든 타입이 변경될 수 있으며, 언어 내부 규칙에 따라 암묵적 타입 변환이 일어나 타입이 다른 값 간의 연산도 가능합니다.

```js
var shouldBeNumber = 10;
shouldBeNumber = "Not a number"; // -> OK
```

`+` 연산자의 경우 문자열 결합이 우선되므로, 피연사자 중 하나가 문자열이면 나머지 값도 문자열로 변환 `-`, `*`, `/` 등 다른 산술 연산자는 문자열 피연사자를 숫자로 변환한 뒤 계산합니다.

```js
console.log("5" - 1); // -> 4
console.log("5" + 1); // -> 51
```

## 5. 이스케이프 문자란 무엇인가요?

이스케이프 문자란 백슬래시(`\`)로 시작하는 특수한 문자이며, 문자열 안에서 직접 입력하기 어려운 문자를 표현할 때 사용합니다. 대표적으로 줄바꿈을 뜻하는 `\n`, 탭을 뜻하는 `\t`이 있습니다. 또한 따옴표, 백슬래시 등 실제로 문자열 안에서 다른 문자와 충돌이 일어날 수 있는 값을 표현하기 위해 사용하기도 합니다.

```js
console.log("Hello\nWorld!");
// ->
// Hello
// World

console.log("Tab\tSeparated");
// -> Tab Separated

console.log('James says: "Hello!"');
// -> James says: "Hello!"
```
