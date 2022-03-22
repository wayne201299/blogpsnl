---
title: Design Pattern
date: 2022-03-16 17:21:18
tags: Design Pattern
categories: Design Pattern
---

> Each pattern describes a problem which occurs over and over again ... and then describes the core of the solution to that problem, in such a way that you can use this solution a million times over, without doing it the same way twice. @Christopher Alexander

目前有26種主要的設計模式，又可以分成三大類
* Creational：設計類別或物件的實例化
* Structural：類別的架構，設計的目的是增加類別的功能性、可擴充性
* Behavioral：類別的行為，包含與其他物件互動的方式
<!-- more -->

## 為什麼要使用
* 保持軟體彈性
* 降低耦合度
* 提高重複可用性
* 提升解決軟體問題的能力

## Creational
| Name | Description | 
| -------- | -------- | 
| Abstract Factory |宣告類別但不實做內容|
| Builder    | Separates object construction from its representation|
| Factory Method| Creates an instance of several derived classes     |
| Object Pool| Avoid expensive acquisition and release of resources by recycling objects that are no longer in use     |
| Prototype| A fully initialized instance to be copied or cloned     |
|Singleton| A class of which only a single instance can exist    |

## Structural


| Name | Description |
| -------- | -------- | 
| Adapter| Match interfaces of different classes| 
| Bridge| Separates an object’s interface from its implementation|
| Composite| A tree structure of simple and composite objects|
| Decorator| Add responsibilities to objects dynamically|
| Facade| A single class that represents an entire subsystem|
| Flyweight| A fine-grained instance used for efficient sharing|
| Private Class Data| Restricts accessor/mutator access|
| Proxy| An object representing another object|

## Behavioral
| Name | Description |
| -------- | -------- | 
| Chain of responsibility | A way of passing a request between a chain of objects |
| Command | Encapsulate a command request as an object |
| Interpreter | A way to include language elements in a program |
| Iterator | Sequentially access the elements of a collection |
| Mediator | Defines simplified communication between classes |
| Memento | Capture and restore an object's internal state |
| Null Object | Designed to act as a default value of an object |
|[Observer](/KNOLxdYrSLyFelzwlzUwWQ) |當被觀察物件異動時通知多個物件觸發事件 |
| State | Alter an object's behavior when its state changes |
| Strategy | Encapsulates an algorithm inside a class |
| Template method | Defer the exact steps of an algorithm to a subclass |
| Visitor | Defines a new operation to a class without change |

---

https://cs.lmu.edu/~ray/notes/designpatterns/
https://www.freecodecamp.org/news/the-basic-design-patterns-all-developers-need-to-know/