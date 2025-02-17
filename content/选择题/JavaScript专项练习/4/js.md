# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.(单选题)下面代码的输出是什么 </summary></b>

```js
function Person(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
}
const member = new Person("Lydia', 'Hallie");
Person.getFullName = () => this.firstName + this.lastName；
console.log(member.getFullName());
```

```
A: TypeError
B: SyntaxError
C: Lydia Hallie
D: undefined undefined
```

答案: A

解析：

您不能像使用常规对象那样向构造函数添加属性。如果要 
一次向所有对象添加功能，则必须使用原型。所以在这种 
情况下应该这样写：

```js
Person.prototype.getFullName = function() {
    return '${this.firstName} ${this.lastName}';
}
```

这样会使member.getFullName()是可用的，为什么样 
做是对的？假设我们将此方法添加到构造函数本身。也 
许不是每个Person实例都需要这种方法。这会浪费大量 
内存空间，因为它们仍然具有该属性，这占用了每个实 
的内存空间。相反，如果我们只将它添加到原型中, 我们只需将它放在内存中的一个位置，但它们都可以访问它！

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>2.(单选题)下面代码的输出是什么 </summary></b>

```js
const person = {
    name: 'Lydia',
    age: 21
}
let city = person.city
city = 'Amsterdam'
console.log(person)
```

```

A: { name: "Lydia",age: 21}
B: { name: "Lydia",age: 21,city: "Amsterdam"}
C: { name: "Lydia",age: 21,city: undefined}
D: "Amsterdam"
```

答案：A

解析：

我们将变量city设置为等于person对象上名为city的属性的值。 这个对象上没有名为city的属性， 因此变量city 的值为 undefined。
请注意， 我们没有引用person对象本身， 只是将变量city设置为等于person对象上city属性的当前值。然后，我们将city设置为等于字符串“Amsterdam”。
这不会更改person对象： 没有对该对象的引用。
因此打印person对象时， 会返回未修改的对象。

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>3.(单选题)下面代码的输出是什么 </summary></b>

```js
(() => {
    let x, y;
    try {
        throw new Error。；
    } catch (x) {
        (x = 1), (y = 2);
        console.log(x);
    )
    console.log(x);
    console.log(y);
))()；
```

```
A: 1 undefined 2
B: undefined undefined undefined
C: 1 1 2
D: 1 undefined undefined
```

答案：A

解析：

catch块接收参数x。当我们传递参数时，这与变量的x不同。这个变量x是属于catch作用域的。
之后，我们将这个块级作用域的变量设置为1, 并设置变量y的值。现在，我们打印块级作用域的变量x , 它等于1。
在catch块之外，x仍然是undefined，而y是2。
我们想在catch块之外的console.log(x)时，它返回undefined , 而 y 返回 2。

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>4.(单选题)下面代码的输出是什么 </summary></b>

```js
let num = 1;
const list = ['A', 'B', 'C', 'D'];
console.log(list[(num += 1)]);
```

```
A: B
B: C
C: SyntaxError
D: ReferenceError
```

答案：B

解析：

通过 += 操作符， 我们对值num进行加1操作。 num有初始值1, 因此1 + 1 的执行结果为2。 数组list的第二项为'C'， console.log(list[2]) 输出'C'

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>5.(单选题)下面代码的输出是什么 </summary></b>

```js
class Chameleon {
    static colorChange(newColor) {
        this.newColor = newColor;
    }
    constructor({
        newColor = 'green'
    } = {}) {
        this.newColor = newColor;
    }
}
const freddie = new Chameleon({
    newColor: 'purple'
})
freddie.colorChange('orange');
```

```
A: orange
B: purple
C: green
D: TypeError
```

答案：D

解析：
colorChange方法是静态的。静态方法仅在创建它们的构造函数中存在，并且不能传递给任何子级。由于freddie是一个子级对象，函数不会传递，所以在freddie实例上不存在freddie方法：抛出TypeError。

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>6.(单选题)下面代码的输出是什么 </summary></b>

```js
const user = {
    name: 'Lydia',
    age: 21
};
const admin = {
    admin: true,
    ...user
};
console.log(admin);
```

```
A: {
    admin: true,
    user: {
        name: "Lydia",
        age: 21
    }
}

B: {
    admin: true,
    name: "Lydia",
    age: 21
}

C: {
    admin: true,
    user: ["Lydia", 21]
}

D: {admin: true}
```

答案：B

解析：

扩展运算符... 为对象的组合提供了可能。 你可以复制对象中的键值对， 然后把它们加到另一个对象里去。 在本例中， 我们复制了user对象键值对，然后把它们加入到admin对象中。 admin对象就拥有了这些键值对, 
所以结果为 

```js
{
    admin: true,
    name: 'Lydia',
    age: 21
}
```

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>7.(单选题)下面代码的输出是什么 </summary></b>

```js
let newList = [1, 2, 3].push(4)
console.log(newList.push(5))
```

```
A: [1, 2, 3, 4, 5]
B: [1, 2, 3, 5]
C: [1, 2, 3, 4]
D: Error
```

答案：D

解析：

.push方法返回数组的长度，而不是数组本身！ 通过将newList 设置为[1, 2, 3].push(4), 实际上 newList 等于数组的新长度： 4。
然后， 尝试在newList上使用.push方法。 由于newList是数值4, 抛出Error。

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>8.(单选题)下面代码的输出是什么 </summary></b>

```js
function compareMembers(person1, person2 = person) {
    if (person1 !== person2) {
        console.log('Not the same!')
    } else {
        console.log('They are the same!')
    }
}
const person = {
    name: 'Lydia'
}
compareMembers(person)
```

```
A: Not the same!
B: They are the same!
C: ReferenceError
D: SyntaxError
```

答案：B

解析：

对象通过引用传递。当我们检查对象的严格相等性（===）时，我们正在比较它们的引用。
我们将"person2"的默认值设置为“person”对象, 并将“person"对象作为"person1”的值传递。
这意味着两个值都引用内存中的同一位置，因此它们是相等的。
运行else语句中的代码块，并记录They are the same!

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>9.(单选题)下面代码的输出是什么 </summary></b>

```js
const box = {
    x: 10,
    y: 20
};
Object.freeze(box);
const shape = box;
shape.x = 100;
console.log(shape);
```

```
A: {x: 100, y:20}
B: {x: 10, y:20}
C: {x: 100}
D: ReferenceError
```

答案：B

解析：
Object.freeze使得无法添加、删除或修改对象的属性（除非属性的值是另一个对象）。
当我们创建变量shape并将其设置为等于冻结对象box时 
shape指向的也是冻结对象。你可以使用Object.isFrozen检查一个对象是否被冻结, 上述情况, Object.isFrozen （ shape ）将返回 true。
由于shape被冻结，并且x的值不是对象，所以我们不能修改属性X。x仍然等于10 , {x ： 10 , y ： 20}被打印。
注意，上述例子我们对属性x进行修改, 可能会导致抛出TypeError异常（最常见但不仅限于严格模式下时）。

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>

<b><details><summary>10.(单选题)下面代码的输出是什么 </summary></b>

```js
const spookyltems = ['A', 'B', 'C'];
({
    item: spookyItems[3]
} = {
    item: 'D'
});
console.log(spookyltems);
```

```
A: ['A', 'B', 'C']
B: ['A', 'B', 'C', 'D']
C: ['A', 'B', 'C', {item: 'D'}]
D: ['A', 'B', 'C', "[object Object]"]
```

答案：B

解析：

通过解构对象们，我们可以从右手边的对象中拆出值，并且将拆出的值分配给左手边对象同名的属性。在这种情况下，我们将值'D'分配给spookyltems[3], 相当于我们正在篡改数组spookyltems , 我们给它添加了值'D'。当输出spookyltems时，结果为磅['A', 'B', 'C', 'D']

[参与互动](https://github.com/yisainan/web-interview/issues/1021)

</details>
