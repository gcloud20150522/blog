---
title: webpack编译typescript
date: 2019-2-21 20:54:51
tags: 
  - 打包
  - 构建
categories: typescript
---


##### 1.安装依赖
    npm install typescript ts-loader --save-dev

##### 2.配置 webpack.config.js
```js
module.exports = {
  entry: {
    app: './src/app.ts'
  },
  output: {
    filename: '[name].bundle.js'
  },
  module: {
    rules: [
      {
        test: /\.tsx?$/,
        use: {
          loader: 'ts-loader',
        },
      }
    ]
  }
};
```

##### 3. 配置 tsconfig.json
```json
{
  "compilerOptions": {
    "module": "commonjs",
    "target": "es5",
    "allowJs": true
  },
  "include": [
    "./src/*"
  ],
  "exclude": [
    "./node_module"
  ]
}
```
>ps: 第三方库的声明文件的安装和使用

    npm install @types/lodash --save

  
  app.ts
  ```ts
  import * as _ from 'lodash'

  console.log(_.chunk([12,120,100,101,88],3))

  const NUM=45

  interface Cat{
    name:String,
    gender:String
  }

  function touchCat(cat:Cat){
    console.log('miao~',cat.name);
    
  }

  touchCat({
    name:"Tom",
    gender:"male"
  })

  ```

  安装声明文件后就可以在编译时出现语法错误提示...