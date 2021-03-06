[返回目录](../vue框架常用知识点.md)

**` vue中典型的问题 `**

1. 通过数组下标修改数组的值，数据改变了，但是视图没有刷新？
    - 首先，数组的长度和数组中某个值被修改，是无法被监听到的
    - vue中监听数组的变化，只能通过push, splice, 直接赋值等方法，才能出发数组的监听事件
    - 所以，当通过数组的下标去修改数组的时候，并没有触发数组的watcher方法，所以视图没有更新
    
  
2. 对对象进行增删改查，数据改变了，但是试图没有刷新？
    - 首先，对象的增删改查，在vue中是无法被直接监听到的
    - 一般的对象监听都会加上深度监听(deep: true)，但是深度监听，是监听不到对象新增的属性的


3. 1和2的解决方法：
    ```
    第一种：
      this.$set(object, key, value)

    第二种：
      this.$forceUpdate()(强制刷新)
    ```
    - 一般监听数组，会使用深度监听: 
    ```
      deep: true
    ```

4. vue的生命周期函数，methods，watch等里面不能使用箭头函数
    - 首先this指向的都是那个调用这个方法的对象
    - vue中当前实例的this，必须得指向当前实例，所以需要使用普通函数
    - 假如使用箭头函数的话，this就会指向该实例的父级实例
    

[返回目录](../vue框架常用知识点.md)
