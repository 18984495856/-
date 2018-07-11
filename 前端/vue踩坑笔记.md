## 通过事件向父级组件发送消息

也就是使用`this.$emit('myEvent')`抛出事件时，父级组件在监听事件时，填写的事件名称是myevent，myEvent是监听不到的，因此建议**始终使用 kebab-case 的事件名。**

```

```

## 通过npm run build生成的项目，无法加载静态资源（404）

修改项目config目录 -> index.js文件的 build.assetsPublicPath : './' 即可修复

```javascript
build: {
    // Template for index.html
    index: path.resolve(__dirname, '../dist/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../dist'),
    assetsSubDirectory: 'static',
    assetsPublicPath: './', //就是修改这一项，把这一项复制过期即可。

    /**
     * Source Maps
     */

    productionSourceMap: true,
    // https://webpack.js.org/configuration/devtool/#production
    devtool: '#source-map',

    // Gzip off by default as many popular static hosts such as
    // Surge or Netlify already gzip all static assets for you.
    // Before setting to `true`, make sure to:
    // npm install --save-dev compression-webpack-plugin
    productionGzip: false,
    productionGzipExtensions: ['js', 'css'],

    // Run the build command with an extra argument to
    // View the bundle analyzer report after build finishes:
    // `npm run build --report`
    // Set to `true` or `false` to always turn it on or off
    bundleAnalyzerReport: process.env.npm_config_report
  }
```

## Vue模板默认的样式和

在Vue模板中的App.vue文件中存在默认样式，建议删掉该样式，以免对后面开发造成影响。

```html
<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
```