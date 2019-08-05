---
title: css sticky footer的实现
date: 2016-10-11 13:54:51
tags: 
  - css 
  - 布局 
categories: css
---
html
```html
<div class="detail" v-show="isShow">
  <div class="detail-wrapper clearfix">
    <div class="detail-main">
      <p>{{seller.bulletin}}</p>
      <p>{{seller.bulletin}}</p>
      <p>{{seller.bulletin}}</p>
      <p>{{seller.bulletin}}</p>
      <p>{{seller.bulletin}}</p>
    </div>
  </div>
  <div class="detail-close" @click="closeDetail">
    <i class="icon-close"></i>
  </div>
</div>
```
css
```css
.detail
  position: fixed
  top: 0
  left: 0
  width: 100%
  height: 100%
  overflow: auto
  background: rgba(7, 17, 27, 0.8)
  z-index: 100
  .detail-wrapper
    min-height: 100%
    .detail-main
      margin-top: 64px
      padding-bottom: 64px
  .detail-close
    position: relative
    width: 32px
    height: 32px
    margin: -64px auto 0 auto
    font-size: 32px
    clear: both
```
clearfix
```css
.clearfix
  display: inline-block
  &:after
    content: '.'
    display: block
    clear: both
    visibility: hidden
    height: 0
    font-size: 0
    line-height: 0
```
