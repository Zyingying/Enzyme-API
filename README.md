# Enzyme-API

## 说在前头

[Enzyme](https://github.com/airbnb/enzyme)是一个用于React的JavaScript测试实用程序，它使得更容易断言，操作和遍历您的React组件的输出，它模拟了jQuery的API，非常直观，易于使用和学习。

这个api整理来自**airbnb的[gitbook](http://airbnb.io/enzyme)**

它提供三种测试方法。

 - `shallow`
 - `render`
 - `mount`

先解释一个词：`wrapper`
wrapper是enzyme包装好的类，以供api使用


## shallow
`shallow` 在单元测试的过程中，`浅渲染`将一个组件渲染成虚拟DOM对象，并不会渲染其内部的子组件，也不是真正完整的`React Render`,无法与子组件互动。


### shallow(node[, options]) => ShallowWrapper

**参数**

1. node (ReactElement): 要渲染的组件
2. options (Object [optional]):
3. options.context: (Object [optional]): 要传递到组件的上下文

**返回**

`ShallowWrapper`: 在渲染输出后，返回浅渲染`ShallowWrapper`实例


### ShallowWrapper API

#### `.at(index) => ShallowWrapper`

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
#### `.childAt(index) => ShallowWrapper`
返回具有指定索引的子元素到新的wrapper

#### `.find(selector) => ShallowWrapper`
根据选择器，找到渲染树中的节点。

#### `.findWhere(predicate) => ShallowWrapper`
找到渲染树中里被的断言函数返回true的节点
参数：`predicate (ShallowWrapper => Boolean)`
断言函数返回布尔值

#### `.filter(selector) => ShallowWrapper`
过滤当前包装器中与所提供的选择器不匹配的节点。

#### `.filterWhere(predicate) => ShallowWrapper`
过滤当前包装器里被断言函数`predicate`不返回true的节点

#### `.contains(nodeOrNodes) => Boolean`
返回给定的 节点/节点数组 是否在渲染树中的布尔值。


#### `.containsMatchingElement(node) => Boolean`
返回在浅渲染树中是否存在给定的node节点 的布尔值。

#### `.containsAllMatchingElements(nodes) => Boolean`
返回在浅渲染树中是否存在给定的 **所有** react元素 的布尔值。


#### `.containsAnyMatchingElements(nodes) => Boolean`
返回在浅渲染树中是否存在给定react元素 **之一** 的布尔值

#### `.equals(node) => Boolean`
根据期望值，返回当前渲染树是否等于给定节点的 布尔值

#### `.matchesElement(node) => Boolean`
返回当前给定的react元素 是否 匹配浅渲染树 的布尔值

#### `.hasClass(className) => Boolean`
是否有这个className

#### `.is(selector) => Boolean`
当前节点是否与提供的选择器匹配

#### `.exists() => Boolean`
当前节点是否存在

#### `.isEmpty() => Boolean`
弃用: 用 `.exists()` 代替.

#### `.not(selector) => ShallowWrapper`
删除当前`wrapper`中与所提供的选择器匹配的节点。 (与  `.filter()`作用相反)

#### `.children() => ShallowWrapper`
获取当前 `wrapper` 中所有子节点的 `wrapper`.

#### `.childAt(index) => ShallowWrapper`
返回具有指定索引的子元素的 `wrapper`

#### `.parents() => ShallowWrapper`
获取当前节点的所有父级（祖先）


#### `.parent() => ShallowWrapper`

Get a wrapper with the direct parent of the current node.

.closest(selector) => ShallowWrapper

Get a wrapper with the first ancestor of the current node to match the provided selector.

.shallow([options]) => ShallowWrapper

Shallow renders the current node and returns a shallow wrapper around it.

.render() => CheerioWrapper

Returns a CheerioWrapper of the current node's subtree.

.unmount() => ShallowWrapper

A method that un-mounts the component.

.text() => String

Returns a string representation of the text nodes in the current render tree.

.html() => String

Returns a static HTML rendering of the current node.

.get(index) => ReactElement

Returns the node at the provided index of the current wrapper.

.getNode() => ReactElement

Returns the wrapper's underlying node.

.getNodes() => Array<ReactElement>

Returns the wrapper's underlying nodes.

.at(index) => ShallowWrapper

Returns a wrapper of the node at the provided index of the current wrapper.

.first() => ShallowWrapper

Returns a wrapper of the first node of the current wrapper.

.last() => ShallowWrapper

Returns a wrapper of the last node of the current wrapper.

.state([key]) => Any

Returns the state of the root component.

.context([key]) => Any

Returns the context of the root component.

.props() => Object

Returns the props of the current node.

.prop(key) => Any

Returns the named prop of the current node.

.key() => String

Returns the key of the current node.

.simulate(event[, data]) => ShallowWrapper

Simulates an event on the current node.

.setState(nextState) => ShallowWrapper

Manually sets state of the root component.

.setProps(nextProps) => ShallowWrapper

Manually sets props of the root component.

.setContext(context) => ShallowWrapper

Manually sets context of the root component.

.instance() => ReactComponent

Returns the instance of the root component.

.update() => ShallowWrapper

Calls .forceUpdate() on the root component instance.

.debug() => String

Returns a string representation of the current shallow render tree for debugging purposes.

.type() => String|Function

Returns the type of the current node of the wrapper.

.name() => String

Returns the name of the current node of the wrapper.

.forEach(fn) => ShallowWrapper

Iterates through each node of the current wrapper and executes the provided function

.map(fn) => Array

Maps the current array of nodes to another array.

.reduce(fn[, initialValue]) => Any

Reduces the current array of nodes to a value

.reduceRight(fn[, initialValue]) => Any

Reduces the current array of nodes to a value, from right to left.

.slice([begin[, end]]) => ShallowWrapper

Returns a new wrapper with a subset of the nodes of the original wrapper, according to the rules of Array#slice.

.tap(intercepter) => Self

Taps into the wrapper method chain. Helpful for debugging.

.some(selector) => Boolean

Returns whether or not any of the nodes in the wrapper match the provided selector.

.someWhere(predicate) => Boolean

Returns whether or not any of the nodes in the wrapper pass the provided predicate function.

.every(selector) => Boolean

Returns whether or not all of the nodes in the wrapper match the provided selector.

.everyWhere(predicate) => Boolean

Returns whether or not all of the nodes in the wrapper pass the provided predicate function.

.dive([options]) => ShallowWrapper

Shallow render the one non-DOM child of the current wrapper, and return a wrapper around the result.