---
title: 如何乾淨的寫Angular
date: 2022-03-23 14:25:48
categories: 前端開發
tags: [Angular,Design Pattern] 
---
* 每行字數不要超過80個字元
* 當HTML上的元素擁有超過一個屬性時，分行寫
* 檔案命名時不要切超過三個段落(~~example-name-tmp.ts~~)
* 開發專案前先規劃好目錄命名原則
* 使用code formatter (TS ES lint)
* 將外部URL放在enviroment下
* 不要直接在component中呼叫API，寫service去把API request 包起來
* 語意化命名變數
* 在同一個component中，如果需要data，不要使用session
* 建立一個common service去取得local或session的storage
* **在service中不要調整到UI，單純處理邏輯**
* **使用HTTP Interceptor 去處理任何的HTTP request、error handling、loader....**
* Unit test every functionality.    :face_with_raised_eyebrow: 
<!-- more -->
* 為每個變數建立data-type、interface
* Follow branching model and use Source Control for the versioning of code. :face_with_raised_eyebrow: 
* 盡量避免使用render、document、setTimeout、detectChange
* 使用async-await 而不是 ~~promise~~
* 刪除被註解的code及沒有使用到的變數或方法
* 驗證String時，使用正則表示式regex
* 使用解構賦值，增加程式碼閱讀性
    ```typescript=
    const arr = [‘a’, ‘b’];
    const [x, y] = arr;
    console.log(x); // a
    console.log(y); //b
    ```
* Validate null or length by using (!) not operator
    ```typescript=
    !res.length & res[i].class == null or !res[i].name
    ```
* After the declaration of a constant, give some (1–2) line gap. :face_with_one_eyebrow_raised: 
* HTML TS 的排版很重要，縮排會影響到顯示
* 要記得在ngDesroy中取消訂閱所有Observable、behaviour subject、route params，不然會造成記憶體洩漏(memory leak)
* 在template(componet.html)中不要使用function/method
* 使用Observerble時不要用await
* Don’t use the <font color='#f00'>**this**</font> keyword in Angular component HTML templates. All the variables/member methods are resolved in the class by default.
* **Observable變數命名尾巴加上＄**
* Keep route names as const. It will prevent accidental typos
    ```typescript=
    export class ROUTE { 
     public static readonly LOGIN = ‘/login’; 
     public static readonly RECRUITMENTS = ‘/recruitments’; 
     public static readonly RECRUITMENT_EDIT = ‘/recruitments/:id’; 
    } 
    ```
* short circuit method
    一般判斷式
    ```typescript=
    if (isValid){ 
    gotoLogin(); 
    }
    ```
    clean way
    ```typescript=
    isValid && gotoLogin();
    ```
* 用hexacode表示顏色
* 幫img加入alt屬性，當找不到圖片時至少還知道那張是什麼圖片
* Use square([]) brackets for the dynamic link. As we know, with the image tag, we use the src attribute. So, if you want to add a dynamic image path, then you can use square brackets here.
* If you want to add any validation on the component template, fetch the string by constant or enum.
* In the case of comments, the first char should be Capital and the full stop should be at last.
* Imports correction. Properly format the imports.
* **在每個method加入回傳的格式**
* There should be no modification of input emitter properties.
* Cross-verify everything that you copy-paste in your code.
* 移掉不需要的console.log，超常忘記的



---

[20+ Angular Code Improvement Tips You Need To Learn Now](https://javascript.plainenglish.io/20-angular-code-improvement-tips-you-need-to-learn-now-af57cab58c69)
