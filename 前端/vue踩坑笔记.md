## 通过事件向父级组件发送消息

也就是使用`this.$emit('myEvent')`抛出事件时，父级组件在监听事件时，填写的事件名称是myevent，myEvent是监听不到的，因此建议**始终使用 kebab-case 的事件名。**

```

```

