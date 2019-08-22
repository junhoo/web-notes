### ES5
> 继承语法
```
function Human(name) {
  this.name = name
}
Human.prototype.say = function() {
  console.log('我叫' + this.name)
  return undefined
}
function Man(name) {
  Human.call(this.name)
  this.gender = '男'
}

Man.prototype.__proto__ = Human.prototype
Man.prototype.fight = function() {
  console.log('捶你的小心心')
}
```
> 兼容ie
```
function Human(name) {
  this.name = name
}
Human.prototype.say = function() {
  console.log('我叫' + this.name)
  return undefined
}
function Man(name) {
  Human.call(this.name)
  this.gender = '男'
}

// good
var f = function(){} // del Human的name
f.prototype = Human.prototype
Man.prototype = new f()

// bad
function Man(name) {
  Human.call(this.name)
  this.gender = '男'
}
Man.prototype = new Human()

Man.prototype.fight = function() {
  console.log('捶你的小心心')
}
```
> var a = new Fn()
1. 产生一个空对象
2. this = 空对象
3. this.__proto__ = Fn.prototype
4. 执行Fn.call(this.x,y.z...)
5. return this

### ES6
```
class Human{
 constructor(name){
    this.name = name
 }
 run(){
    console.log("我叫"+this.name+"，我在跑")
    return undefined
 }
}
class Man extends Human{
 constructor(name){
    super(name)
    this.gender = '男'
 }
 fight(){
    console.log('糊你熊脸')
 }
}
```