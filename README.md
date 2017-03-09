# Enzyme-API

[Enzyme](https://github.com/airbnb/enzyme)是一个用于React的JavaScript测试实用程序，它使得更容易断言，操作和遍历您的React组件的输出，它模拟了jQuery的API，非常直观，易于使用和学习。

它提供三种测试方法。

 - `shallow`
 - `render`
 - `mount`

先解释一个词：`wrapper`
wrapper是enzyme包装好的类，以供api使用


# shallow
`shallow` 在单元测试的过程中，`浅渲染`将一个组件渲染成虚拟DOM对象，并不会渲染其内部的子组件，也不是真正完整的`React Render`,无法与子组件互动。


### shallow(node[, options]) => ShallowWrapper

**参数**

1. node (ReactElement): 要渲染的组件
2. options (Object [optional]):
3. options.context: (Object [optional]): 要传递到组件的上下文

**返回**

`ShallowWrapper`: 在渲染输出后，返回浅渲染`ShallowWrapper`实例


## ShallowWrapper API

### `.at(index) => ShallowWrapper`

返回当前索引的的节点到 wrapper
在当前包装器的给定索引处返回节点周围的包装器。

**参数**

+ `index (Number)`: 从0开始的整数，来选择取回的第几个节点

**返回**

`ShallowWrapper`

**例子**
```javascript
const wrapper = shallow(<MyComponent />);
expect(wrapper.find(Foo).at(0).props().foo).to.equal("bar");

```

**类似方法**
`.get(index) => ReactElement`

---
### `.childAt(index) => ShallowWrapper`
返回具有指定索引的子元素到新的wrapper

