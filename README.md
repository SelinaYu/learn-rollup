# README

---
## Quickstart
```
# Clone the repo
git clone https://github.com/SelinaYu/learn-rollup.git

# Move into the repo
cd learn-rollup/

# Install dependencies
npm install

# Start the watcher
npm run dev
```
## 为什么使用Rollup？
我们模块化项目时，往往会遇到只需要模块中某些方法，有些方法并未被调用的情况。使用webpack进行打包的时候，往往会把这整个模块依赖都打包到js文件中。前些天看了下使用webpack遇到这种情况的处理，可以[戳这里][1]看详情。然而，Rollup,据说使用一种`shaking tree`技术，只将需要的代码提取出来打包，能大大减小代码体积。并听说Webpack2也将支持`tree-shaking`。
## 如何使用Rollup打包
可以参考下面两篇教程
[如何使用Rollup打包JavaScript][2]
[如何使用Rollup打包样式文件并添加LiveReload][3]

但是，当我进行到**安装LiveReload自动刷新浏览器**会出现下面的报错。
>WebSocket connection to 'ws://localhost:35729/livereload' failed: Error in connection establishment: net::ERR_CONNECTION_REFUSED

解决方法：
安装插件
```
npm install --save-dev rollup-plugin-livereload
```
在rollup.config.js中，添加
```
import livereload from 'rollup-plugin-livereload';
.....
export default {
  entry: 'src/scripts/main.js',
  dest: 'build/js/main.min.js',
  format: 'iife',
  sourceMap: 'inline',
  plugins: [
    livereload(),
    ....
    ]
};
```
而package.json中scripts只需要添加下面命令就能自动刷新：
```
 "dev": "rollup -c --watch",
```
  [1]: https://zhuanlan.zhihu.com/p/21748318?refer=starkwang
  [2]: http://www.w3cplus.com/javascript/learn-rollup-js.html
  [3]: https://www.w3cplus.com/javascript/learn-rollup-css.html