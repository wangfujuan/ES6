##### 使用场景
当作永远不会重复的字符串
如果一个Symbol要反复被使用，可以用Symbol.for()

##### 声明定义
```javascript
let hd = Symbol();
console.log(hd) // Symbol()

let hd = Symbol(); // 或者 []、{}
let edu = Symbol(); // 或者 []、{}
console.log(hd == edu); // 结果都为 false

let cms = Symbol.for('hdcms');
let edu = Symbol.for('hdcms');
console.log(cms == edu) // true

let hd = Symbol('描述知道是哪个');
console.log(hd.toString()); // Symbol(描述知道是哪个)
console.log(hd.description); // 描述知道是哪个

let cms = Symbol.for("hdcms");
// 通过 keyFor 或者 description 来获的描述
console.log(Symbol.keyFor(cms)); // hdcms
```
##### 解决字符串耦合问题
```javascript
let grade = {
    "张三": {js: 98, css: 90},
    "张三": {js: 10, css: 20},
}
console.log(grade); // 只有一条数据，前面的被后面的覆盖了

let user1 = "张三";
let user2 = "张三";
let grade = {
    // [变量]
    [user1]: {js: 98, css: 90},
    [user2]: {js: 10, css: 20},
}
console.log(grade);

let user1 = {
    name: "张三",
    key: Symbol()
};
let user2 = {
    name: "张三",
    key: Symbol()
};

let grade = {
    [user1.key]: {js: 98, css: 90},
    [user2.key]: {js: 10, css: 20},
}
console.log(grade[user1.key]);
```
##### Symbol 在缓存容器中的使用

