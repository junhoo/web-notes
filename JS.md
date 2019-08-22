[TOC]
# -
## 简介

### ES6
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

### ES5
```
var f = function(){} // del Human的name
f.prototype = Human.prototype
Man.prototype = new f()

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