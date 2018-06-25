## 编译前端工程时缺少vue-loader以及style解析失败

[来源](https://segmentfault.com/q/1010000014770071?sort=created)

[vue官方在github上的解答](https://github.com/vuejs/vue-loader/issues/1238)

>vue-loader@15.*之后除了必须带有VueLoaderPlugin 之外，还需另外单独配置css-loader。                      

```javascript
const VueLoaderPlugin = require('vue-loader/lib/plugin')  

module.exports = {
  // ...
  module: {
    rules: [
      {
        test: /\.vue$/,
        loader: 'vue-loader'
      },
      {
        test: /\.css$/,
        use: ['style-loader','css-loader']  //这个需要执行npm i style-loader安装。
      }
    ]
  }
  plugins: [
    new VueLoaderPlugin()
  ]
}
```

