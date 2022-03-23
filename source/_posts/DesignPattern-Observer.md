---
title: Observer
date: 2022-03-16 17:14:05
categories: Design Pattern
tags: Design Pattern
---
 
>  In those systems, the subject is usually named a "stream of events" or "stream source of events", while the observers are called "sinks of events"


觀察者模式，設定一個被觀察物件(subject)，當subject的狀態變更時，觀察者也會有相對的行為，通常是用來處理事件，在此模式下被觀察物件會被稱為<strong>stream of events</strong>
<!-- more -->
## Problem
table中有filter功能，會依照filter選擇同步去調整table內容顯示
## Solution
定義一個資料載體(subject)儲存資料模型或商業邏輯，多個Observer訂閱subject，當subject有異動會**同步廣播**(broadcast)給所有訂閱的Observer，Observer會收到當下subject所儲存的資料



```typescript=
// 宣告被觀察的subject物件
table_date$ = new BehaviorSubject<any>('');
// 當被觀察的subject異動，重新刷新table內容
this.tableData$ = combineLatest([
      this.table_name$,
      this.table_typeId$,
      this.table_proType$,
      this.table_date$,
      this.table_order$,
      this.table_currentPage$,
    ]).pipe(
      debounceTime(800),
      distinctUntilChanged(),
      switchMap(([name, typeId, proType, date, order, currentPage]) => {
        return this.getTableData(name, typeId, proType, date, order, currentPage);
      }),
    );


```

---

https://sourcemaking.com/design_patterns/observer