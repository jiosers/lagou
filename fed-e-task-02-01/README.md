# part2 简单题
## 第一题
* 工作原理：对申明的每个变量设置引用技术，判断当前计数是否为0，当数字为0时就立即回收。
* 优缺点：1.对于无引用数据可立马回收，从而最大减少程序暂停。2.对于循环引用的对象无法回收，同时时刻回收会导致性能开销大。
  

## 第二题
* 标记整理算法的工作流程：1、遍历所有对象标记活动对象。2、遍历所有对象查找为标记的活动对象并且对其空间进行位置移动。3、回收空间。
  

## 第三题
* v8新生代垃圾回收过程：新生代垃圾回收将内存空间分为两个空间，一个Form空间，用来存放活动对象，另一个To空间，空闲空间。活动对象都存储于Form空间。检查Form空间存活的对象，若对象存活，则检查对象是否需要晋升，若符合条件则将对象晋升至老生代，否则将对象从Form中拷贝至To空间，若对象不存活，则释放不存活对象的空间。然后对其Form空间以及To空间进行交换，完成释放。

## 第四题
* 增量标记算法的运用场景及工作原理：增量标记算法的运用场景主要是针对老生代垃圾回收造成全停顿时间过长而引用的一套优化算法。它的主要原理就是将一次老生代垃圾回收造成的停顿进行标记的过程，分成很多小步，每执行一小步就让应用逻辑执行一段时间再进行一小步的GC，这样交替来完成一次标记。

# part2 代码实现

## 代码题1

* 练习一
    ```
    const isLastInStock = fp.flowRight(fp.prop('in_stock'), fp.last)
    ```
* 练习二
    ```
    const firstName = fp.flowRight(fp.prop  ('name'), fp.fist)
    ```

* 练习三
    ```
    const getDollar = (item) => item.dollar_value
    const averageDollarValue = fp.flowRight(_average, fp.map(getDollar))
    ```

* 练习四
  ```
  const sanitizeNames = fp.flowRight(_underscore, fp.toLower, fp.join(' '))
  ```

## 代码题2
* 练习一
  ```
  let ex1 = mayBe.map(fp.map(fp.add(3)))._value
  ```
* 练习二
  ```
  let ex2 = xs.map(fp.first)._value
  ```
* 练习三
  ```
  safeProp('name', user).map(fp.first)._value
  ```
* 练习四
  ```
  let ex4 = (n) => {
    return n = MayBe.of(n).map(parseInt)._value
  }
  ```

