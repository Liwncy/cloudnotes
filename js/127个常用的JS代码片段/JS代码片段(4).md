##127个常用的JS代码片段，每段代码花30秒就能看懂（四）

#64、getColonTimeFromDate


用于判断程序运行环境是否在浏览器，这有助于避免在node环境运行前端模块时出错。
```
const isBrowser = () => ![typeof window, typeof document].includes('undefined');


isBrowser(); // true (browser)
isBrowser(); // false (Node)
```
#65、isBrowserTabFocused


用于判断当前页面是否处于活动状态（显示状态）。



```
const isBrowserTabFocused = () => !document.hidden;isBrowserTabFocused(); // true
```
#66、isLowerCase


用于判断当前字符串是否都为小写。
```
const isLowerCase = str => str === str.toLowerCase();


isLowerCase('abc'); // true
isLowerCase('a3@$'); // true
isLowerCase('Ab4'); // false
```
```



```
#67、isNil


用于判断当前变量的值是否为 null 或 undefined 类型。
```
const isNil = val => val === undefined || val === null;


isNil(null); // true
isNil(undefined); // true
```
```



```
#68、isNull


用于判断当前变量的值是否为 null 类型。
```
const isNull = val => val === null;


isNull(null); // true
```
```



```
#69、isNumber


用于检查当前的值是否为数字类型。
```
function isNumber(n) {
    return !isNaN(parseFloat(n)) && isFinite(n);
}


isNumber('1'); // false
isNumber(1); // true
```
```



```
#70、isObject


用于判断参数的值是否是对象，这里运用了Object 构造函数创建一个对象包装器，如果是对象类型，将会原值返回。
```
const isObject = obj => obj === Object(obj);


isObject([1, 2, 3, 4]); // true
isObject([]); // true
isObject(['Hello!']); // true
isObject({ a: 1 }); // true
isObject({}); // true
isObject(true); // false
```
#71、isObjectLike


用于检查参数的值是否为null以及类型是否为对象。
```
const isObjectLike = val => val !== null && typeof val === 'object';


isObjectLike({}); // true
isObjectLike([1, 2, 3]); // true
isObjectLike(x => x); // false
isObjectLike(null); // false
```
#72、isPlainObject


此代码段检查参数的值是否是由Object构造函数创建的对象。
```
const isPlainObject = val => !!val && typeof val === 'object' && val.constructor === Object;


isPlainObject({ a: 1 }); // true
isPlainObject(new Map()); // false
```
```



```
#73、isPromiseLike


用于检查当前的对象是否类似Promise函数。
```
const isPromiseLike = obj =>
  obj !== null &&
  (typeof obj === 'object' || typeof obj === 'function') &&
  typeof obj.then === 'function';
  
isPromiseLike({
  then: function() {
    return '';
  }
}); // true
isPromiseLike(null); // false
isPromiseLike({}); // false
```
```



```
#74、isSameDate


用于判断给定的两个日期是否是同一天。
```
const isSameDate = (dateA, dateB) => dateA.toISOString() === dateB.toISOString();


isSameDate(new Date(2010, 10, 20), new Date(2010, 10, 20)); // true
```
```



```
#75、isString


用于检查当前的值是否为字符串类型。
```
const isString = val => typeof val === 'string';


isString('10'); // true
```
#76、isSymbol


用于判断参数的值是否是 Symbol 类型。
```
const isSymbol = val => typeof val === 'symbol';


isSymbol(Symbol('x')); // true
```
#77、isUndefined


用于判断参数的类型是否是 Undefined 类型。
```
const isUndefined = val => val === undefined;


isUndefined(undefined); // true
```
#78、isUpperCase


用于判断当前字符串的字母是否都为大写。
```
const isUpperCase = str => str === str.toUpperCase();


isUpperCase('ABC'); // true
isLowerCase('A3@$'); // true
isLowerCase('aB4'); // false
```
#79、isValidJSON


用于判断给定的字符串是否是 JSON 字符串。
```
const isValidJSON = str => {
  try {
    JSON.parse(str);
    return true;
  } catch (e) {
    return false;
  }
};


isValidJSON('{"name":"Adam","age":20}'); // true
isValidJSON('{"name":"Adam",age:"20"}'); // false
isValidJSON(null); // true
```
```



```
#80、last


此函数功能返回数组的最后一个元素。
```
const last = arr => arr[arr.length - 1];


last([1, 2, 3]); // 3
```
#81、matches


此函数功能用于比较两个对象，以确定第一个对象是否包含与第二个对象相同的属性与值。
```
onst matches = (obj, source) =>
  Object.keys(source).every(key => obj.hasOwnProperty(key) && obj[key] === source[key]);
  
matches({ age: 25, hair: 'long', beard: true }, { hair: 'long', beard: true }); // true
matches({ hair: 'long', beard: true }, { age: 25, hair: 'long', beard: true }); // false


```
#82、maxDate


此代码段查找日期数组中最大的日期进行输出。
```
const maxDate = (...dates) => new Date(Math.max.apply(null, ...dates));


const array = [
  new Date(2017, 4, 13),
  new Date(2018, 2, 12),
  new Date(2016, 0, 10),
  new Date(2016, 0, 9)
];
maxDate(array); // 2018-03-11T22:00:00.000Z
```
#83、maxN


此段代码输出数组中前 n 位最大的数。
```
const maxN = (arr, n = 1) => [...arr].sort((a, b) => b - a).slice(0, n);


maxN([1, 2, 3]); // [3]
maxN([1, 2, 3], 2); // [3,2]
```
#84、minDate


此代码段查找日期数组中最早的日期进行输出。
```
const minDate = (...dates) => new Date(Math.min.apply(null, ...dates));


const array = [
  new Date(2017, 4, 13),
  new Date(2018, 2, 12),
  new Date(2016, 0, 10),
  new Date(2016, 0, 9)
];
minDate(array); // 2016-01-08T22:00:00.000Z
```
