---
title: 資料綁定
date: 2022-03-15 17:03:29
categories: 前端開發
tags: Angular
---
TypeScript與HTML間溝通的橋樑，最主要分為這三種
* 屬性綁定
* 事件綁定
* 雙向綁定


內崁binding (Interpolation)
---
雙向，綁定script 與HTML變數使用
```htmlmixed=
{{data}}
```
<!-- more -->
屬性binding (property binding)
---

屬性綁定，單向，父元件傳遞給子元件，子元件透過在component的class內加入@input接取
```htmlmixed=
[property]='data'
```
```typescript=
@Input() name:string='alan';
```
事件binding (event binding)
---
父元件偵測子元件異動，當有異動時，子元件會emit出指定的物件，再由父元件在ngOnchange()做事件攔截

子元件component.ts
```typescript=
@Output() newItemEvent = new EventEmitter<string>();
this.newItemEvent.emit('hello world');
```
父元件component.html
```htmlmixed=
(event)='getEmitter($event)'
```
雙向binding (two way binding)
---
跟雙大括號一樣效果，讓HTML可以直接呼叫TS中宣告的變數value
```htmlmixed=
[(title)]='name'
<!-- // 等同於 -->
[title]='name' (titleChange)='name=$event'
```
表單控制，要先引入FormModule，有表單控制效果...
```htmlmixed=
[(ngModel)]='testItem'
```