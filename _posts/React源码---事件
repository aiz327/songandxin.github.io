### React事件源码(V15.6.2)

#### React事件源码追溯

· ReactDefaultInjection
ReactDom调用ReactDefaultInjection.inject()方法，初始化内部的默认策略和设置
如：reconciletransaction、batchingstrategy和事件等

通过EventPluginHub注入eventpluginorder、eventplugin
每个eventplugin都包含一部分event定义，包含在eventTypes中，里面有冒泡、捕获阶段的事件名（onClick、onClickCapture）及事件所依赖的topevent(topOnClick)

```javascript

var eventTypes = {
  mouseEnter: {
    registrationName: 'onMouseEnter',
    dependencies: ['topMouseOut', 'topMouseOver']
  },
  mouseLeave: {
    registrationName: 'onMouseLeave',
    dependencies: ['topMouseOut', 'topMouseOver']
  }
};

```
事件注册流程
ReactDomComponent =>
ReactBrowserEventEmitter =>
ReactEventListener =>
trapBubbledEvent|trapBubbledEvent =>
事件绑定在document上，事件名及处理函数（ReactEventListener.dispatchEvent）作为参数

事件执行流程
ReactEventListener.dispatchEvent =>
ReactUpdates.batchedUpdates =>
ReactDefaultBatchingStrategy.batchedUpdates =>  通过dispatchEvent调用react的批处理程序
ReactDefaultBatchingStrategyTransaction.perform => 经过事务处理调用

