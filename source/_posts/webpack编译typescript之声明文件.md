---
title: webpack编译typescript  --typings安装声明文件
date: 2019-2-21 21:54:51
tags: 
  - 打包
  - 构建
  - ts声明文件
categories: typescript
---


##### 1.安装依赖
    npm install typescript ts-loader --save-dev
    
    npm insatll typings -g
    typings install lodash

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
    "allowJs": true,
    // 添加
    "typeRoots": [
      "./node_modules/@type",
      "./typings/modules"
    ]
  },
  "include": [
    "./src/*"
  ],
  "exclude": [
    "./node_module"
  ]
}
```
>ps: 

  
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