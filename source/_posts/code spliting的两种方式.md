---
title: Code Splitting的两种方法
tags: 
  - 打包
  - 构建
  - 代码分离
categories: webpack
---

##### 一.使用 SplitChunksPlugin 去重和分离 chunk。

webpack.config.js
```js
const path = require('path');

  module.exports = {
    mode: 'development',
    entry: {
      index: './src/index.js',
    },
    output: {
      filename: '[name].bundle.js',
      path: path.resolve(__dirname, 'dist')
    },
    optimization: {
      splitChunks: {
        chunks: 'all'
      }
    }
  };

```
index.js

```js
import _ from 'lodash'

console.log(_.join(['hello','world']))

```


##### 二.使用符合 ECMAScript 提案 的 import() 语法 来实现动态导入。

1.安装依赖
    
    npm install --save-dev @babel/plugin-syntax-dynamic-import
2.配置.babelrc
```json
{
  "plugins": ["@babel/plugin-syntax-dynamic-import"]
}
```
3.webpack.config.js
```js
const path = require('path');

  module.exports = {
    mode: 'development',
    entry: {
     index: './src/index.js'
    },
    output: {
      filename: '[name].bundle.js',
      chunkFilename: '[name].bundle.js',
      path: path.resolve(__dirname, 'dist')
    },

  };
```

4.src/index.js

```js
function getComponent() {
  return import('lodash').then(({ default: _ }) => {
    var element = document.createElement('div');

    element.innerHTML = _.join(['Hello', 'webpack'], ' ');

    return element;
  })
}

getComponent().then(comp=>{
  document.body.appendChild(comp);
})
```

5.打包
    npx webpack
