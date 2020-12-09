##127个常用的JS代码片段，每段代码花30秒就能看懂（五）

#85、minN


此段代码输出数组中前 n 位最小的数。
```
const minN = (arr, n = 1) => [...arr].sort((a, b) => a - b).slice(0, n);


minN([1, 2, 3]); // [1]
minN([1, 2, 3], 2); // [1,2]
```
#86、negate


此函数功能将不满足函数条件的内容筛选出来。
```
const negate = func => (...args) => !func(...args);


[1, 2, 3, 4, 5, 6].filter(negate(n => n % 2 === 0)); // [ 1, 3, 5 ]
```
#87、nodeListToArray


此函数功能将制定的DOM节点以数组的形式输出。
```
const nodeListToArray = nodeList => [...nodeList];


nodeListToArray(document.childNodes); // [ <!DOCTYPE html>, html ]
```
#88. pad


按照指定的长度生成字符串，如果字符串长度不够，可以按照设定的字符在其左右两端补齐，默认为空格字符串。
```
const pad = (str, length, char = ' ') =>
  str.padStart((str.length + length) / 2, char).padEnd(length, char);
  
pad('cat', 8); // '  cat   '
pad(String(42), 6, '0'); // '004200'
pad('foobar', 3); // 'foobar'
```
#89. radsToDegrees


此函数功能将弧度转换成度数。
```
const radsToDegrees = rad => (rad * 180.0) / Math.PI;


radsToDegrees(Math.PI / 2); // 90
```
#90、randomHexColorCode


此段代码用于生成随机的16进制颜色代码。
```
const randomHexColorCode = () => {
  let n = (Math.random() * 0xfffff * 1000000).toString(16);
  return '#' + n.slice(0, 6);
};


randomHexColorCode(); // "#e34155"
```
#91、randomIntArrayInRange


按照指定的数字范围随机生成长度为 n 的数组。
```
const randomIntArrayInRange = (min, max, n = 1) =>
  Array.from({ length: n }, () => Math.floor(Math.random() * (max - min + 1)) + min);
  
randomIntArrayInRange(12, 35, 10); // [ 34, 14, 27, 17, 30, 27, 20, 26, 21, 14 ]
```
#92、randomIntegerInRange


按照指定的范围内生成一个随机整数。
```
const randomIntegerInRange = (min, max) => Math.floor(Math.random() * (max - min + 1)) + min;


randomIntegerInRange(0, 5); // 3
```
#93、randomNumberInRange


该代码段可用于返回指定范围内的随机数（包含小数部分）。
```
const randomNumberInRange = (min, max) => Math.random() * (max - min) + min;


randomNumberInRange(2, 10); // 6.0211363285087005
```
#94、readFileLines


此段代码将读取到的文本内容，按行分割组成数组进行输出。
```
const fs = require('fs');
const readFileLines = filename =>
  fs
    .readFileSync(filename)
    .toString('UTF8')
    .split('\n');


let arr = readFileLines('test.txt');
console.log(arr); // ['line1', 'line2', 'line3']
```
#95、Redirect to a URL


此函数功能将页面导向一个指定的网站地址。
```
const redirect = (url, asLink = true) =>
  asLink ? (window.location.href = url) : window.location.replace(url);
  
redirect('https://www.qianduandaren.com');
```
#96、reverse


此段代码用于将一段字符串进行颠倒。
```
const reverseString = str => [...str].reverse().join('');


reverseString('foobar'); // 'raboof'
```
#97、round


将小数按照指定的位数，进行四舍五入保留。
```
const round = (n, decimals = 0) => Number(`${Math.round(`${n}e${decimals}`)}e-${decimals}`);


round(1.005, 2); // 1.01
```
#98、runPromisesInSeries


通过数组的形式，连续运行多个promise。
```
const runPromisesInSeries = ps => ps.reduce((p, next) => p.then(next), Promise.resolve());
const delay = d => new Promise(r => setTimeout(r, d));


runPromisesInSeries([() => delay(1000), () => delay(2000)]); 
// Executes each promise sequentially, taking a total of 3 seconds to complete
```
#99、sample


从数组中获取一个随机数。
```
const sample = arr => arr[Math.floor(Math.random() * arr.length)];


sample([3, 7, 9, 11]); // 9
```
#100、sampleSize


在数组中随机生选择 n 个元素生成新的数组，如果n大于数组长度，则为随机整个数组的排序。这里使用到了 Fisher–Yates shuffle 洗牌算法。
简单来说 Fisher–Yates shuffle 算法是一个用来将一个有限集合生成一个随机排列的算法（数组随机排序）。这个算法生成的随机排列是等概率的。同时这个算法非常高效。
更多关于 Fisher–Yates shuffle 洗牌算法的内容，你可以点击 阅读原文 进行查看。
```
const sampleSize = ([...arr], n = 1) => {
  let m = arr.length;
  while (m) {
    const i = Math.floor(Math.random() * m--);
    [arr[m], arr[i]] = [arr[i], arr[m]];
  }
  return arr.slice(0, n);
};


sampleSize([1, 2, 3], 2); // [3,1]
sampleSize([1, 2, 3], 4); // [2,3,1]
```
#101、 scrollToTop


此函数功能将页面平滑的滚动到页面的顶部。
```
const scrollToTop = () => {
  const c = document.documentElement.scrollTop || document.body.scrollTop;
  if (c > 0) {
    window.requestAnimationFrame(scrollToTop);
    window.scrollTo(0, c - c / 8);
  }
};


scrollToTop();
```
#102、serializeCookie


此段代码用于将 cookie 序列化成 name-value 的形式方便你存储在 Set-Cookie 头信息里。
```
const serializeCookie = (name, val) => `${encodeURIComponent(name)}=${encodeURIComponent(val)}`;


serializeCookie('foo', 'bar'); // 'foo=bar'
```
#103、setStyle


此段代码用于在相应的DOM节点添加属性和值。
```
const setStyle = (el, ruleName, val) => (el.style[ruleName] = val);


setStyle(document.querySelector('p'), 'font-size', '20px');
// The first <p> element on the page will have a font-size of 20px
```
#104、 shallowClone


此段代码用于浅复制一个对象。
```
const shallowClone = obj => Object.assign({}, obj);


const a = { x: true, y: 1 };
const b = shallowClone(a); // a !== b
```
#105、show


段代码用于显示所有指定的 DOM 元素。
```
const show = (...el) => [...el].forEach(e => (e.style.display = ''));


show(...document.querySelectorAll('img')); // Shows all <img> elements on the page
```
