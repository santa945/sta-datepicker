# sta-datepicker

## 介绍
离散型的时间选择器，普通的时间选择器要么只能单选，要么只能选返回，不可以随意选择若干个时间，同时大众的时间选择器选择结束回收起来，很不方便，这个组件可以方便前端开发嵌套进自定义的弹窗中，自己控制展开收起

## 安装依赖

```js
npm install
```

## 运行
* 将`webpack.config.js`中的`entry`改为`'./src/main.js'`, `output=> filename`改为`'build.js',`,运行`npm run dev`,即可打开案例查看
* 默认的配置`entry: './src/index.js'`和`filename: 'datePicker.min.js'`用于生成静态组件包，运行`npm run build`可打包压缩过的**组件包js**

## 使用场景

![sta-datepicker使用场景](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b6a8627ac6324ccabb859b92d0f39da4~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)