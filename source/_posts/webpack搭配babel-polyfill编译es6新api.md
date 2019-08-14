---
title: webpack搭配babel-polyfill编译es6新api
date: 2018-8-11 10:54:51
tags: 
  - 打包
  - 构建
  - babel
categories: webpack
---

>babel-polyfill 为全局垫片,为开发应用而准备
####  1.安装依赖

    npm install @babel/preset-env @babel/core babel-loader --save-dev
    npm install babel-polyfill -save


####  2.项目中引入
```js
import 'babel-polyfill'

let func=()=>{}
const NUM=45
let arr=[1,2,4]
let a=arr.includes(8)
console.log(a);

let arrB=arr.map(item=>item*2)

console.log('new Set(arrB)',new Set(arrB));


function *fun(){

}
```


####  3.配置
```js
module.exports = {
  entry: {
    app: './app.js'
  },
  output: {
    filename: '[name].bundle.js'
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: [
              ['@babel/preset-env', {
                targets: {
                  browsers: ['>1%', 'last 2 versions']
                }
              }]
            ]
          }
        },
        exclude: '/node_moules/'
      }
    ]
  }
};
```
#### 4.打包
    npx webpack