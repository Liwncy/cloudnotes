## 9 个功能强大的 JavaScript 技巧

### 1、全部替换
我们知道 string.replace() 函数仅替换第一次出现的情况。
你可以通过在正则表达式的末尾添加 /g 来替换所有出现的内容。
```
var example = "potato potato";
console.log(example.replace(/pot/, "tom")); 
// "tomato potato"
console.log(example.replace(/pot/g, "tom")); 
// "tomato tomato"
```
### 2、提取唯一值
通过使用 Set 对象和展开运算符，我们可以创建一个具有唯一值的新数组。
```
var entries = [1, 2, 2, 3, 4, 5, 6, 6, 7, 7, 8, 4, 2, 1]
var unique_entries = [...new Set(entries)];
console.log(unique_entries);
// [1, 2, 3, 4, 5, 6, 7, 8]
```
### 3、 将数字转换为字符串
我们只需要使用带空引号的串联运算符。
```
var converted_number = 5 + "";
console.log(converted_number);
// 5
console.log(typeof converted_number); 
// string
```
### 4、将字符串转换为数字
我们需要的只是 + 运算符。
请注意它仅适用于“字符串数字”。
```
the_string = "123";
console.log(+the_string);
// 123


the_string = "hello";
console.log(+the_string);
// NaN
```
### 5、随机排列数组中的元素
我每天都在这样做。
```
var my_list = [1, 2, 3, 4, 5, 6, 7, 8, 9];
console.log(my_list.sort(function() {
    return Math.random() - 0.5
})); 
// [4, 8, 2, 9, 1, 3, 6, 5, 7]
```
### 6、 展平二维数组
只需使用展开运算符。
```
var entries = [1, [2, 5], [6, 7], 9];
var flat_entries = [].concat(...entries); 
// [1, 2, 5, 6, 7, 9]
```
### 7、 缩短条件语句
让我们来看这个例子：
```
if (available) {
    addToCart();
}
```
通过简单地使用变量和函数来缩短它：
```
available && addToCart()
```
### 8、动态属性名
我一直以为必须先声明一个对象，然后才能分配动态属性。
```
const dynamic = 'flavour';
var item = {
    name: 'Coke',
    [dynamic]: 'Cherry'
}
console.log(item); 
// { name: "Coke", flavour: "Cherry" }
```
### 9、使用 length 调整/清空数组
我们基本上覆盖了数组的 length 。
如果我们要调整数组的大小：
```
var entries = [1, 2, 3, 4, 5, 6, 7];  
console.log(entries.length); 
// 7  
entries.length = 4;  
console.log(entries.length); 
// 4  
console.log(entries); 
// [1, 2, 3, 4]
```
如果我们要清空数组：
```
var entries = [1, 2, 3, 4, 5, 6, 7]; 
console.log(entries.length); 
// 7  
entries.length = 0;   
console.log(entries.length); 
// 0 
console.log(entries); 
// []
```
