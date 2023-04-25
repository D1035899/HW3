# 作業3 詐欺遊戲-釣魚網站

`
姓名: 張牧翔
學號: D1035899
`

- 目標網站: [https://course.fcu.edu.tw/](https://course.fcu.edu.tw/)
- 作業網站: [https://d1035899.github.io/HW3/](https://d1035899.github.io/HW3/)
- 說明網站: [https://github.com/D1035899/HW3/blob/master/README.md](https://github.com/D1035899/HW3/blob/master/README.md)
- Code Repo: [https://github.com/D1035899/HW3](https://github.com/D1035899/HW3)

---

## 目錄

- [作業3 詐欺遊戲-釣魚網站](#作業3-詐欺遊戲-釣魚網站)
  - [目錄](#目錄)
  - [目標網頁介紹](#目標網頁介紹)
  - [修改code講解](#修改code講解)
    - [增加flex與grid排版](#增加flex與grid排版)
    - [刪除不需要的當案](#刪除不需要的當案)
    - [Radio button 轉換頁面](#radio-button-轉換頁面)
    - [下載檔案不完全](#下載檔案不完全)
    - [驗證碼](#驗證碼)
    - [使用者輸入帳號密碼之後續](#使用者輸入帳號密碼之後續)
  - [與原網站的差異](#與原網站的差異)
  - [心得](#心得)

---

## 目標網頁介紹

該網頁為逢甲大學的選課系統登入介面，而學校會在即將開學期間，以及學期期中考前開放加退選，所以如果透過釣魚網站得到使用者的帳號密碼，就能將該學生的課程亂選一通，或是將他選的課變成自己的課。

---

## 修改code講解

### 增加flex與grid排版

- flex排版

  - 我在網頁上方的title裡加入了flex排版，但是如果沒有做任何的處理的話，上面標題的位置會跑至最左邊，這是因為flex的預設排版是由左到右、上到下，因此我在`#topContent`裡面加入了`flex-direction: row-reverse;`來讓flex的row起始位置變成由右到左，這樣一來標題就會回到最右邊了
   ![flex](files/Images/flex.png)
  >單純增加`<display: flex;>`後的變化

   ![flex_fix](files/Images/flex_fix.png)
  >增加flex排版的css片段
- grid排版

  - 透過將網頁上方的細項連結的`<td>`元素增加一個class名為gridLayout，並且在css裡增加相關的selector，且設定網格的排版位置以及格與格之間的寬度，來達到跟目標網站一樣的效果。如果只單純增加`display: grid;`，格子的起始位置會在最左邊，且不設定的話會是單行多列，因此要使用`grid-template-columns`來設定有幾行，並且透過`grid-column-gap`設定格線寬度，還有透過`justify-content`調整整體layout的位置

   ![flex](files/Images/grid.png)
   >單純增加`<display: grid;>`後的變化

   ![gird_fix](files/Images/grid_fix.png)
   >增加grid排版的css片段

   ![gird_fix](files/Images/grid_class.png)
   >於html新增的class: gridLayout，以便控制grid的使用

### 刪除不需要的當案

這次的目標網站有很多用不到的js檔，因此經過測試之後，就將下載下來的js檔都刪除，並且將部分的`<script>`也刪除，因為不影響網頁使用上的問題。

### Radio button 轉換頁面

原本目標網站有兩種語言的頁面(中文/英文)，並且透過`Radio Button`來做轉換，但是因為在刪除檔案的時候好像也把該功能刪掉了，導致`Radio Button`點了之後不會有反應，因此就新增了新的`<script>`來做語言轉換。

![login](files/Images/login.png)
![change_to_zh](files/Images/change_to_zh.png)
>轉換語言的`Radio Button`

![change_to_en](files/Images/change_to_en.png)
>透過偵測點擊`onclick`function來實現切換語言

### 下載檔案不完全

在下載原始網頁之後發現，有部分的圖片沒有顯示，後來才發現因為該圖片被放在原始的css檔案裡，因此就重新把圖片抓下來，就能正常顯示了。
![download](files/Images/download.png)
>剛下載下來的樣子

![original](files/Images/original.png)
>修改css以及下載漏掉的圖片後

![fix](files/Images/fix.png)
>透過修改`#topContent`裡的`background-image`元素後，就能正常顯示了

### 驗證碼

由於下載下來之後，網頁的驗證碼圖片不會更新，因此我直接把原網站的驗證碼圖片位址複製到我修改的code裡，如此一來，驗證碼圖片就會隨著網頁整理而刷新。
而在驗證碼旁邊的刷新按鈕，也是因為在刪檔案的時候，不小心刪掉刷新功能，因此也實作了一個onclick來刷新驗證碼。
![code](files/Images/code.png)
>驗證碼圖片位址以及按鈕樣式

### 使用者輸入帳號密碼之後續

在使用者輸入帳號密碼並點擊登入按鈕之後，會觸發`alertbox`提示，告知使用者網頁系統錯誤，然後重載頁面(實際上是將使用者導引回原本的網站)

![alertBox](files/Images/alert_box.png)
>code實作

![systemcall](files/Images/systemcall.png)
![systemcall2](files/Images/systamcall2.png)
>網頁提示(中/英)

---

## 與原網站的差異

我所復課的網頁實際上差異非常的小，只差在登入帳號上的排版有些微的不同，原網站的驗證碼刷新按鈕是貼齊輸入框，但我的並沒有，估計是因為我轉換成button的形式去寫。另外，radio button之間的寬度也有些微的不同，但我不太確定要如何去做修改。

![fake](files/Images/fake.png)
![origin](files/Images/origin.png)

>左圖: 復刻網站
>右圖:  原始網站

---

## 心得

我覺得這次的作業稍微有點麻煩，因為當你要復刻網站的時候，必須先把目標網頁的code抓下來分析他怎麼寫的。
而大部分的網站都做得很完善，所以在瀏覽code的時候會覺得很亂，不知道該從哪裡看，以及要刪除那些code。
後來發現只要邊看鱉comment一些code，看看那些code會不會有甚麼影響，如此一來，就能快速了解那些是不需要的部分。
透過這次的作業讓我的看code能力又更進步了一點。
