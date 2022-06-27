# 配色主題
配色主題可以改變 **WitherTorch 的介面顏色**

## 安裝
將寫好的主題檔案放入 WitherTorch 資料夾底下的 Themes 資料夾 (沒有那個資料夾的話請自行建立一個)，<br/>
然後打開 WitherTorch，從介面設定的介面主題中挑選要套用的主題檔案名稱，最後重啟程式即可完成套用。

## 編寫主題
### 檔案格式
配色主題是JSON 格式的檔案，結構如下：
```json
{
  "default":{
    "_comment": "預設的子配色主題"
  }
  "overrides":[
    {
      "target_blur":[
        "介面材質ID", "第二個介面材質ID", "..."
      ],
      "_comment": "在 target_blur 包含目前所設定的介面材質的情況下才會套用的子配色主題"
    }
  ]
}
```
### 子配色主題的結構 (所有子項目都不是必要的)
```json
{
  "_comment": "根節點 (可能是 default 或 overrides 下的子項目)",
  "base_background_color": "視窗的基礎背景顏色",
  "splash_screen_back_color": "啟動畫面的背景顏色",
  "splash_screen_text_color": "啟動畫面的文字顏色",
  "page_color": "視窗頁面的背景顏色",
  "setting_page_color": "主視窗中設定頁面的二層選單的背景顏色",
  "wizard_back_color": "'精靈'視窗的背景顏色 (目前僅套用在建立伺服器視窗上)",
  "serverList_background_color": "主視窗中伺服器列表的背景色",
  "serverList_bottomBar_background_color": "主視窗中伺服器列表下方按鈕列的背景色",
  "brushes": {
    "_comment": "繪製過程中所使用的所有筆刷，格式如下",
    "筆刷ID": "筆刷色彩",
    "筆刷ID2": "筆刷色彩2"
  }
}
```

### 色彩格式

WitherTorch 支援兩種色彩格式

第一種是直接填寫顏色的名稱或16進位顏色編碼
#### 範例
```json
{
  "serverList_background_color": "#FFFFFF",
  "page_color": "white",
  "base_background_color": "#00000000",
  "brushes": {
      "app.control.fore": "black"
  }
}
```

第二種是填寫顏色的RGB數值(有四個子項目(r,g,b,a，其中 a 為顏色的透明度)，四個數值皆為可選項，r,g,b 不填的話預設是0，a 不填的話預設是255 (不透明))
#### 範例
```json
{
  "serverList_background_color": {"r": 255,"g": 255,"b": 255},
  "page_color": {"r": 255,"g": 255,"b": 255},
  "base_background_color": {"a": 0},
  "brushes": {
      "app.control.fore": {"r": 0,"g": 0,"b": 0,"a": 255}
  }
}
```

### 筆刷格式

筆刷格式除了色彩模式那兩種外，還支援引用其他筆刷
#### 範例
```json
{
  "brushes": {
      "app.control.fore": {"r": 0,"g": 0,"b": 0,"a": 255},
      "app.textbox.fore": "$app.control.fore"
  }
}
```
