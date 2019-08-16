---
title: webpack搭配babel-runtime-transform编译es6新api
date: 2018-8-11 12:54:51
tags: 
  - 打包
  - 构建
  - babel
categories: webpack
---

>babel-runtime-transform 为局部垫片,为开发框架而准备
####  1.安装依赖

    npm install @babel/preset-env @babel/core babel-loader --save-dev
    npm install @babel/plugin-transform-runtime  --save-dev
    npm install @babel/runtime --save


####  2.项目根目录新建.babelrc
```json
{
  "plugins": [
    [
      "@babel/plugin-transform-runtime",
      {
        "absoluteRuntime": false,
        "corejs": 2,
        "helpers": true,
        "regenerator": true,
        "useESModules": false
      }
    ]
  ]
}
```
##### 配置项corejs为2,需要安装依赖
    npm install --save @babel/runtime-corejs2


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
        },
        exclude: '/node_moules/'
      }
    ]
  }
};
```
#### 4.app.js
```js   
// import 'babel-polyfill'

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
#### 5.打包
    npx webpack