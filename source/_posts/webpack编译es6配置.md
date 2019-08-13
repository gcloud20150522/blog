---
title: webpack编译es6配置选项
date: 2018-8-10 11:54:51
tags: 
  - 打包
  - 构建
categories: webpack
---

####  1.安装依赖

    npm install @babel/preset-env @babel/core babel-loader --save-dev


####  2.配置
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