## 127个常用的JS代码片段，每段代码花30秒就能看懂（六）

# 106、shuffle


使用 Fisher–Yates shuffle 洗牌算法对数组的内容进行随机排序，生成新的数组。
什么是 Fisher–Yates shuffle 洗牌算法? 算法是一个用来将一个有限集合生成一个随机排列的算法（数组随机排序）。这个算法生成的随机排列是等概率的，同时这个算法非常高效。
```
const shuffle = ([...arr]) => {
  let m = arr.length;
  while (m) {
    const i = Math.floor(Math.random() * m--);
    [arr[m], arr[i]] = [arr[i], arr[m]];
  }
  return arr;
};


const foo = [1, 2, 3];
shuffle(foo); // [2, 3, 1], foo = [1, 2, 3]
```
# 107、similarity


查找两个数组之间的交集。
```
const similarity = (arr, values) => arr.filter(v => values.includes(v));


similarity([1, 2, 3], [1, 2, 4]); // [1, 2]
```
# 108、sleep


用于延迟异步函数的执行。
```
const sleep = ms => new Promise(resolve => setTimeout(resolve, ms));


async function sleepyWork() {
  console.log("I'm going to sleep for 1 second.");
  await sleep(1000);
  console.log('I woke up after 1 second.');
}
```
# 109、smoothScroll
用于让指定的DOM节点平滑滚动到可视区域。
```
const smoothScroll = element =>
  document.querySelector(element).scrollIntoView({
    behavior: 'smooth'
  });
  
smoothScroll('#fooBar'); 
// scrolls smoothly to the element with the id fooBar
smoothScroll('.fooBar'); 
// scrolls smoothly to the first element with a class of fooBar
```
# 110、sortCharactersInString


将单词的内容按照字母的顺序进行重新排序。
```
const sortCharactersInString = str => [...str].sort((a, b) => a.localeCompare(b)).join('');


sortCharactersInString('cabbage'); 
// 'aabbceg'
```
# 111、splitLines


用于将一段字符串按照“换行符”分割成数组进行输出。
```
const splitLines = str => str.split(/\r?\n/);
splitLines('This\nis a\nmultiline\nstring.\n'); 
// ['This', 'is a', 'multiline', 'string.' , '']
```
```



```
# 112、stripHTMLTags


格式化去掉 HTML 代码内容，输出文本内容。
```
const stripHTMLTags = str => str.replace(/<[^>]*>/g, '');


stripHTMLTags('<p><em>lorem</em> <strong>ipsum</strong></p>'); 
// 'lorem ipsum'
```
# 113、sum


用于计算数字之和。
```
const sum = (...arr) => [...arr].reduce((acc, val) => acc + val, 0);


sum(1, 2, 3, 4); // 10
sum(...[1, 2, 3, 4]); // 10
```
# 114、tail


用于获取数组除第一个元素之外的所有元素，如果数组只有一个元素，则返回本数组。
```
const tail = arr => (arr.length > 1 ? arr.slice(1) : arr);


tail([1, 2, 3]); // [2,3]
tail([1]); // [1]
```
# 115、take


从数组开始位置截取n个元素，生成新的数组。
```
const take = (arr, n = 1) => arr.slice(0, n);


take([1, 2, 3], 5); // [1, 2, 3]
take([1, 2, 3], 0); // []
```
# 116、takeRight


从数组开始末尾截取n个元素，生成新的数组。
```
const takeRight = (arr, n = 1) => arr.slice(arr.length - n, arr.length);


takeRight([1, 2, 3], 2); // [ 2, 3 ]
takeRight([1, 2, 3]); // [3]
```
# 117、timeTaken


用来计算函数执行的时间。
```
const timeTaken = callback => {
  console.time('timeTaken');
  const r = callback();
  console.timeEnd('timeTaken');
  return r;
};


timeTaken(() => Math.pow(2, 10)); 
// 1024, (logged): timeTaken: 0.02099609375ms
```
# 118、times


按照指定的次数，进行回调函数。
```
const times = (n, fn, context = undefined) => {
  let i = 0;
  while (fn.call(context, i) !== false && ++i < n) {}
};


var output = '';
times(5, i => (output += i));
console.log(output); // 01234
```
# 119、toCurrency


此段代码用于按照指定的货币类型格式化货币数字。
```
const toCurrency = (n, curr, LanguageFormat = undefined) =>
  Intl.NumberFormat(LanguageFormat, { style: 'currency', currency: curr }).format(n);
  
toCurrency(123456.789, 'EUR'); 
// €123,456.79  | currency: Euro | currencyLangFormat: Local
toCurrency(123456.789, 'USD', 'en-us'); 
// $123,456.79  | currency: US Dollar | currencyLangFormat: English (United States)
toCurrency(123456.789, 'USD', 'fa'); 
// ۱۲۳٬۴۵۶٫۷۹ ؜$ | currency: US Dollar | currencyLangFormat: Farsi
toCurrency(322342436423.2435, 'JPY'); 
// ¥322,342,436,423 | currency: Japanese Yen | currencyLangFormat: Local
toCurrency(322342436423.2435, 'JPY', 'fi'); 
// 322 342 436 423 ¥ | currency: Japanese Yen | currencyLangFormat: Finnish
```
# 120、toDecimalMark


用于格式化数字，将其转换成逗号分隔的数字字符串。
```
const toDecimalMark = num => num.toLocaleString('en-US');


toDecimalMark(12305030388.9087); 
// "12,305,030,388.909"
```
# 121、toggleClass


使用 element.classList.toggle() 来切换元素中指定样式类。
```
const toggleClass = (el, className) => el.classList.toggle(className);


toggleClass(document.querySelector('p.special'), 'special'); 
// The paragraph will not have the 'special' class anymore
```
# 122、tomorrow


用于获取明天的日期。
```
const tomorrow = () => {
  let t = new Date();
  t.setDate(t.getDate() + 1);
  return t.toISOString().split('T')[0];
};


tomorrow(); 
// 2019-09-08 (if current date is 2018-09-08)


```
# 123、unfold


基于初始值，和步长生成一个新的数组。
```
const unfold = (fn, seed) => {
  let result = [],
    val = [null, seed];
  while ((val = fn(val[1]))) result.push(val[0]);
  return result;
};


var f = n => (n > 50 ? false : [-n, n + 10]);
unfold(f, 10); 
// [-10, -20, -30, -40, -50]


```
# 124、union


合并两个数组，并删除重复的内容。
```
const union = (a, b) => Array.from(new Set([...a, ...b]));
union([1, 2, 3], [4, 3, 2]);
// [1,2,3,4]
```
# 125、uniqueElements


使用 ES6 的 set 和 …rest 运算去除数组中重复的元素。
```
const uniqueElements = arr => [...new Set(arr)];


uniqueElements([1, 2, 2, 3, 4, 4, 5]); 
// [1, 2, 3, 4, 5]
```
# 126. validateNumber


用于检查参数类型是否是数字。
```
const validateNumber = n => !isNaN(parseFloat(n)) && isFinite(n) && Number(n) == n;


validateNumber('10'); // true
```
# 127. words


将一段英文字符串拆分成单词数组（去除一些特殊符号）。
```
const words = (str, pattern = /[^a-zA-Z-]+/) => str.split(pattern).filter(Boolean);


words('I love javaScript!!'); 
// ["I", "love", "javaScript"]
words('python, javaScript & coffee'); 
// ["python", "javaScript", "coffee"]


```
