---
title: flex实现左边固定宽度右边自适应布局
date: 2016-11-12 20:54:51
tags: 
  - 布局
  - flex
categories: css
---
html
```html
<div class="goods">
  <div class="menu-wrapper">
    <ul>
      <li v-for="(food,index) in goods" :key="index" class="menu-item">
        <span class="text border-1px">
          <span v-show="food.type>0" class="icon" :class="classMap[food.type]"></span>
          {{food.name}}
        </span>
      </li>
    </ul>
  </div>
  <div class="foods-wrapper"></div>
</div>
```
css
```css
.goods
  position: absolute
  top: 174px
  bottom: 46px
  overflow: hidden
  display: flex
  .menu-wrapper
    flex: 0 0 80px
    width: 80px
    background: #f3f5f7
  .food-wrapper
    flex: 1
```
