# [Vanilla js](http://vanilla-js.com/)

![](/Users/chooomu/Sites/joy/vanilla/img/01.png)

Vanilla JS는 웹사이트를 들어가서 보면 알 수 있듯이, **순수한 JavaScript를 일컫는 말**이다. Vanilla는 비격식으로 **평범한, 특별할 것 없는** 이라는 뜻을 가진 형용사이다.



## 속도 비교

실제로 Vanilla JS가 얼마나 빠른지에 대한 예시

Dojo, Prototype JS, Ext JS, JQuery, YUI, MooTools 모두 Vanilla JS 코드를 다르게 해석한 것이다.

Vanilla JS는 120만개가 넘는 Operation(ops)을 1초(sec)에 할 수 있다.

### Retrieve DOM element by ID

|              | Code                                                     | ops / sec  |
| ------------ | -------------------------------------------------------- | ---------- |
| Vanilla JS   | document.getElementById('test-table');                   | 12,137,211 |
| Dojo         | dojo.byId('test-table');                                 | 5,443,343  |
| Prototype JS | $('test-table')                                          | 2,940,734  |
| Ext JS       | delete Ext.elCache['test-table']; Ext.get('test-table'); | 997,562    |
| jQuery       | $jq('#test-table');                                      | 350,557    |
| YUI          | YAHOO.util.Dom.get('test-table');                        | 326,534    |
| MooTools     | document.id('test-table');                               | 78,80      |



### Retrieve DOM elements by tag name

|              | Code                                                         | ops / sec |
| ------------ | ------------------------------------------------------------ | --------- |
| Vanilla JS   | document.getElementsByTagName("span");                       | 8,280,893 |
| Prototype JS | Prototype.Selector.select('span', document);                 | 62,872    |
| YUI          | YAHOO.util.Dom.getElementsBy(function(){return true;},'span'); | 48,545    |
| Ext JS       | Ext.query('span');                                           | 46,915    |
| jQuery       | $jq('span');                                                 | 19,449    |
| Dojo         | dojo.query('span');                                          | 10,335    |
| MooTools     | Slick.search(document, 'span', new Elements);                | 5,457     |



## 누가 사용중 일까?

- Facebook
- Google
- YouTube
- Yahoo
- Wikipedia
- Amazon
- Microsoft
- Tumbir
- Apple
- Netflix
- ...



## 다운로드

웹사이트에 있는 여러가지 파일을 다운로드 받으면, 실제로 exe 파일은 없고 0byte가 뜨면서 **"그냥 보로 코딩을 시작해라"** 라는 주석이 뜬다.

JavaScript 코딩에 있어 여러가지 프레임워크/라이브러리가 필요하지 않다는걸 알려주기 위해 만들어진 사이트인것 같다.



## Variable(let, const)

자바스크립트에서 변수를 할당할 수 있는 키워드. ES5까지 변수를 선언할 수 있는 유일한 방법은 var 키워드였다. ES6에서는 var 가지는 단점을 보완하기 위해 let과 const를 도입하게 되었다.

**let은 재할당이 자유롭지만 const는 재할당이 금지**된다. const는 또한 선언과 동시에 할당이 이루어져야 한다. const는 상수라는 뜻, 안정적이라고 해석 할 수 있다.

```javascript
let a = 100;
b = a - 50;
a = 30;
console.log(a, b);
```

결과

`30 50`

```javascript
const a = 100;
b = a - 50;
a = 30;
console.log(a, b);
```

결과

`TypeError:Assignment to constant variable.`

Assignment to constant variable 에러가 발생했다. const로 선언된 변수에 재할당으르 시도할 때 나타나는 에러이다. 변수를 선언할 때는 기본적으로 const를 사용하고 let은 재할당이 필요한 경우에만 한정해 사용하는 습관을 기르자. 생각보다 객체를 재할당하는 경우는 드물다. let을 남발하여 우도치 않은 재할당 방지를 위해 기본적으로 const를 사용하자.



## Data Types

자바스크립트에서 사용할 수 있는 데이터 타입은 string, boolean, number, float등이 있다.

```javascript
const whatString = 'reference';
const whatBoolean = true;
const whatNumber = 123;
const whatFloat = 12.3;
console.log(whatString);
console.log(whatBoolean);
console.log(whatNumber);
console.log(whatFloat);
```

결과

`reference`

`true`

`123`

`12.3`

string은 ""또는 ''로 묶어주면 string타입 "true" 또한 string.

boolean은 true, false를 가지는 타입.

number는 숫자형 타입.

float은 소수점 타입.



## Data with Arrays

데이터 타입을 정렬할 수 있는 방법은 array, object이다.

array는 데이터를 리스트와 같이 저장하는 곳이다.

```javascript
const mon = 'Mon';
const tue = 'Tue';
const wed = 'Wed';
const thu = 'Thu';
const fri = 'Fri';
const sat = 'Sat';
const sun = 'Sun';
console.log(mon, tue, wed, thu, fri, sat, sun);

const dayOfWeek = ['mon', 'tue', 'wed', 'thu', 'fri', 'sat', 'sun'];
console.log(dayOfWeek);
console.log(dayOfWeek[1]);
console.log(dayOfWeek[10]);
```

결과

`Mon Tue Wed Thu Fri Sat Sun`

`['mon', 'tue', 'wed', 'thu', 'fri', 'sat', 'sun']`

`tue`

`undefined`

요일이 각각 변수로 할당 되어 있고 모든 요일을 조회한다고 가정했을때 나열 해서 조회가 가능하나 비효율적이다. 이럴때 하나로 묶어서 사용하는 것이 array. 콤마로 구분되어 array 요소들을 보여줌 string 이외에도 어떤 Data Types이 와도 array를 구성할 수 있음. array 요소에 접근하고 싶으면 인덱스를 통해 접근. 범위가 벗어날 경우에는 undefined가 반환된다.



## Data with Objects

object와 array의 다른 점은 object는 key, value로 구성된다는 것. array는 데이터를 정렬된 방식으로 접근할 수 없다. 단순히 순서에 의해 나열했을 뿐이다. 정보를 담는다면 일일이 몇 번째 있는지 기억해야 하므로 효율적이지 않은 방법이다.

```javascript
const arrayInfo = ['reference', 32, 'Korea'];
console.log(arrayInfo);
console.log(arrayInfo[1]);

const objectInfo = {
  name:'reference',
  age:32,
  country:'Korea',
  favAnimal:['dog','cat'],
  favFood:[
    {
      name:'hamburger'
    },
    {
      name:'pizza'
    },
    {
      name:'rice noodle'
    }
  ]
};
console.log(objectInfo);
console.log(objectInfo.age);

objectInfo.age = 40;

console.log(objectInfo.age);

objectInfo = true;
```

결과

`['reference', 32, 'Korea']`

`32`

`{
  name:'reference',
  age:32,
  country:'Korea',
  favAnimal:['dog','cat'],
  favFood:[
    {
      name:'hamburger'
    },
    {
      name:'pizza'
    },
    {
      name:'rice noodle'
    }
  ]
}`

`32`

`40`

`TypeError:Assignment to constant variable.`

object는 key를 지정하여 value값을 담는다. objectInfo는 object에 다양한 정보를 담고 있다. 여기서 기억해야 할 것은 자바스크립트 문법과 규칙이다. array와 object의 선언, 접근 방법 등이다.

const는 상수라고 했는데 objectInfo를 const로 선언했다. 이후 중간에 objectInfo.age = 40;을 통해 값을 변경했다. object 타입의 변수에 참조 변수에 대해서는 값이 변경 가능하다. objectInfo = true;를 통해 const로 선언된 변수에 재할당이 불가하다는 것을 에러를 통해 다시 한번 확인 할수 있다.



## Function with Object

```javascript
console.log(console);
```

결과

`Console {
  log:[Function:bound consoleCall], ...
}`

console은 여러가지 함수를 가지고 있는 object이다. console.log를 비롯해 alert등의 함수들은 내장 함수(built-in function)라고 한다. 함수는 어떤 기능, 행위를 표현한 것. 필요한 곳에 원하는 만큼 사용할 수 있다.

```javascript
console.log('VanilaJS With Single');
console.log("VanilaJS With Double");

function vanilaJS(param){
  console.log('VanilaJS With ${param}');
}

vanilaJS('Object');
vanilaJS('function');
vanilaJS('argument');

function vanilaJS_return(param){
  return 'VanilaJS With ${param}';
}

const vanila = vanilaJS_return('return');
console.log(vanila);
```

결과

`VanilaJS With Single`

`VanilaJS With Double`

`VanilaJS With Object`

`VanilaJS With function`

`VanilaJS With argument`

`VanilaJS With return`

자바스크립트에서 스트링을 표현할 때 ''(싱글),""(더블)로 표현해 준다. 이런 방식은 변수와 함께 문자열을 만들 때 불편하다. 그래서 나온것이 백틱이다. 백틱을 사용하여 ${변수}를 사용하면 간단하게 만들 수 있다.

```javascript
const calculator = {
  plus: function(a, b){
    return a + b;
  },
  minus: function(a, b){
    return a - b;
  },
  muliti: function(a, b){
    return a * b;
  },
  division: function(a, b){
    return a / b;
  }
};

const plus = calculator.plus(7, 7);
const minus = calculator.minus(10, 5);
const muliti = calculator.muliti(15, 5);
const division = calculator.division(20, 5);

console.log(plus);
console.log(minus);
console.log(muliti);
console.log(division);
```

결과

`14`

`5`

`75`

`4`

간단하게 calculator Object에 계산식 함수 4개를 만들어보았다. console.log와 유사한 점을 찾아보자.



## DOM(Document Object Model)

```html
<body>
  <h1 id="title">This Work!</h1>
<script>
```

```css
body{background:orange;}
h1{color:#fff;}
```

```javascript
const title = document.getElementById('title');
console.log(document);
console.log(title);
title.innerHTML = 'Hi! From JS';
```

document.getElementById를 통해 title 이이디를 가지는 요소에 접근할 수 있다. document 그 자체를 console.log로 확인하면 index.html이 그대로 나타난다. DOM은 자바스크립트 html에 있는 모든 요소를 반환하여 객체로 변환한다. 타이틀을 innerHTML를 통해 변경할 수도 있다. 이렇게 자바스크립트로 html을 바꿀 수 있다. 

그 외에도 getElementByClassName, getElementByTagName, querySelector 등을 숙지 해야 함.

### Event

자바스크립트는 이벤트에 반응하기 위해서 만들어짐. 이벤트란 웹사이트에서 발생하는 click, resize, submit, change등 이며 이런 이벤트를 제어할 수 있다.

```javascript
function handleResize(event){
  console.log(event);
}
window.addEventListener('resize', handleResize);
```

자바스크립트는 이벤트를 받기 기다리고 있다. 여기서 어떤 이벤트를 ㄱ다리는 이벤트를 다룰 함수와 함께 명시해 줘야 한다. 모든 이벤트를 기다릴 수는 없기 때문. 이벤트 함수를 정의할 때마다 자바스크립트는 event 객체를 자동적으로 함수에 주입.

```javascript
const title = document.querySelector('#title');
function handleClick() {
  title.style.color = 'black';
}
title.addEventListener('click', handleClick);
```

querySelector를 통해 title 객체를 할당받고 click시 title에 대한 color를 변경