## 127个常用的JS代码片段，每段代码花30秒就能看懂（三）

# 43、getColonTimeFromDate


此段代码从Date对象里获取当前时间。
```
const getColonTimeFromDate = date => date.toTimeString().slice(0, 8);
getColonTimeFromDate(new Date()); // "08:38:00"


```
# 44、getDaysDiffBetweenDates


此段代码返回两个日期之间相差多少天
```
const getDaysDiffBetweenDates = (dateInitial, dateFinal) =>
  (dateFinal - dateInitial) / (1000 * 3600 * 24);
  
getDaysDiffBetweenDates(new Date('2019-01-13'), new Date('2019-01-15')); // 2
```
# 45、getStyle


此代码返回DOM元素节点对应的属性值。
```
const getStyle = (el, ruleName) => getComputedStyle(el)[ruleName];


getStyle(document.querySelector('p'), 'font-size'); // '16px'


```
# 46、getType


此段代码的主要功能就是返回数据的类型。
```
const getType = v =>
  v === undefined ? 'undefined' : v === null ? 'null' : v.constructor.name.toLowerCase();
  
getType(new Set([1, 2, 3])); // 'set'


```
# 47、hasClass


此段代码返回DOM元素是否包含指定的Class样式。
```
const hasClass = (el, className) => el.classList.contains(className);
hasClass(document.querySelector('p.special'), 'special'); // true


```

48、head


此段代码输出数组的第一个元素。
```
const head = arr => arr[0];


head([1, 2, 3]); // 1


```
# 49、hide
此段代码隐藏指定的DOM元素。
```
const hide = (...el) => [...el].forEach(e => (e.style.display = 'none'));


hide(document.querySelectorAll('img')); // Hides all <img> elements on the page




```
# 50、httpsRedirect
此段代码的功能就是将http网址重定向https网址。
```
const httpsRedirect = () => {
  if (location.protocol !== 'https:') location.replace('https://' + location.href.split('//')[1]);
};


httpsRedirect(); // If you are on http://mydomain.com, you are redirected to https://mydomain.com


```
# 51、indexOfAll
此代码可以返回数组中某个值对应的所有索引值，如果不包含该值，则返回一个空数组。
```
const indexOfAll = (arr, val) => arr.reduce((acc, el, i) => (el === val ? [...acc, i] : acc), []);


indexOfAll([1, 2, 3, 1, 2, 3], 1); // [0,3]
indexOfAll([1, 2, 3], 4); // []
```
# 52、initial
此段代码返回数组中除最后一个元素的所有元素
```
const initial = arr => arr.slice(0, -1);


initial([1, 2, 3]); // [1,2]const initial = arr => arr.slice(0, -1);
initial([1, 2, 3]); // [1,2]




```
# 53、insertAfter
此段代码的功能主要是在给定的DOM节点后插入新的节点内容
```
const insertAfter = (el, htmlString) => el.insertAdjacentHTML('afterend', htmlString);


insertAfter(document.getElementById('myId'), '<p>after</p>'); // <div id="myId">...</div> <p>after</p>
```
# 54、insertBefore
此段代码的功能主要是在给定的DOM节点前插入新的节点内容
```
const insertBefore = (el, htmlString) => el.insertAdjacentHTML('beforebegin', htmlString);


insertBefore(document.getElementById('myId'), '<p>before</p>'); // <p>before</p> <div id="myId">...</div>
```
# 55、intersection
此段代码返回两个数组元素之间的交集。
```
const intersection = (a, b) => {
  const s = new Set(b);
  return a.filter(x => s.has(x));
};


intersection([1, 2, 3], [4, 3, 2]); // [2, 3]




```
# 56、intersectionBy
按照给定的函数处理需要对比的数组元素，然后根据处理后的数组，找出交集，最后从第一个数组中将对应的元素输出。
```
const intersectionBy = (a, b, fn) => {
  const s = new Set(b.map(fn));
  return a.filter(x => s.has(fn(x)));
};


intersectionBy([2.1, 1.2], [2.3, 3.4], Math.floor); // [2.1]
```
# 57、intersectionBy
按照给定的函数对比两个数组的差异，然后找出交集，最后从第一个数组中将对应的元素输出。
```
const intersectionWith = (a, b, comp) => a.filter(x => b.findIndex(y => comp(x, y)) !== -1);


intersectionWith([1, 1.2, 1.5, 3, 0], [1.9, 3, 0, 3.9], (a, b) => Math.round(a) === Math.round(b)); // [1.5, 3, 0]




```
# 58、is
此段代码用于判断数据是否为指定的数据类型，如果是则返回true。
```
const is = (type, val) => ![, null].includes(val) && val.constructor === type;


is(Array, [1]); // true
is(ArrayBuffer, new ArrayBuffer()); // true
is(Map, new Map()); // true
is(RegExp, /./g); // true
is(Set, new Set()); // true
is(WeakMap, new WeakMap()); // true
is(WeakSet, new WeakSet()); // true
is(String, ''); // true
is(String, new String('')); // true
is(Number, 1); // true
is(Number, new Number(1)); // true
is(Boolean, true); // true
is(Boolean, new Boolean(true)); // true
```
# 59、isAfterDate
接收两个日期类型的参数，判断前者的日期是否晚于后者的日期。
```
const isAfterDate = (dateA, dateB) => dateA > dateB;


isAfterDate(new Date(2010, 10, 21), new Date(2010, 10, 20)); // true
```
# 60、isAnagram
用于检测两个单词是否相似。
```
const isAnagram = (str1, str2) => {
  const normalize = str =>
    str
      .toLowerCase()
      .replace(/[^a-z0-9]/gi, '')
      .split('')
      .sort()
      .join('');
  return normalize(str1) === normalize(str2);
};


isAnagram('iceman', 'cinema'); // true
```
# 61、isArrayLike
此段代码用于检测对象是否为类数组对象,是否可迭代。
```
const isArrayLike = obj => obj != null && typeof obj[Symbol.iterator] === 'function';


isArrayLike(document.querySelectorAll('.className')); // true
isArrayLike('abc'); // true
isArrayLike(null); // false


```
# 62、isBeforeDate
接收两个日期类型的参数，判断前者的日期是否早于后者的日期。
```
const isBeforeDate = (dateA, dateB) => dateA < dateB;


isBeforeDate(new Date(2010, 10, 20), new Date(2010, 10, 21)); // true
```
# 63、isBoolean


此段代码用于检查参数是否为布尔类型。
```
const isBoolean = val => typeof val === 'boolean';


isBoolean(null); // false
isBoolean(false); // true
```
