# vue 平台練習作品

上一篇： [vue-cli & firebase 簡介](https://hackmd.io/s/rkQkGSu5Q)

---

下載範例：

https://github.com/anita8004/vue-dashboard-customer

在選定位置打開終端機輸入以下內容

```
git clone https://github.com/anita8004/vueShopTest.git 
cd vueShopTest
npm install || yarn install
```

:::warning
|| 是 or 的意思
:::

start 需要一些時間，完成後會顯示：

![](https://i.imgur.com/PUs0JoY.png)

然後ctrl + 左鍵點擊網址

---

## 加入自己的firebase設定

1. 進入專案

![](https://i.imgur.com/ePxyAPa.png)

2. 進入後，點擊新增應用程式，選取平台 -> 選最右邊

![](https://i.imgur.com/Z85LsIV.png)
![](https://i.imgur.com/fPBZ6Gk.png)

3. 複製程式碼

![](https://i.imgur.com/Qx3D1SG.png)

4. 打開main.js

剛剛複製的程式碼這邊只需要 config 的部分就好了
用config的部分替換掉以下程式碼

```javascript
let config = {}
```

---

## 執行

```
npm start || yarn start
```

---

## 預設系統帳密

admin@admin.com

admin123456

---

## 平台功能介紹

- 註冊
- 登入
- App平台
- 使用者管理
  - 使用者資料編輯
  - 使用者刪除
  - 更改使用者權限
- 權限管理
  - 設定權限群組
  - 編輯權限群組
  - 刪除權限群組
- 操作紀錄