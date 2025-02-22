# 簡介

- 多吃水果有益身體健康，不過該怎麼挑選水果才是既健康又經濟呢？

- 以R語言建立的Shiny應用

- 透過簡易的互動介面，輕鬆查詢「當日」的水果NP值(Nutrition-Price Value)排行

# 安裝
```
library(devtools)

install_github("sulaxd/fruitRank")
```

# 執行
```
library(fruitRank)

run_fruitRank()
```

# 畫面簡介
## 最新水果價格
![image](https://cloud.githubusercontent.com/assets/5773822/21128998/05c95f98-c13a-11e6-8d04-6b825d12be62.png)

## 水果營養
![image](https://cloud.githubusercontent.com/assets/5773822/21129024/2e5f51e2-c13a-11e6-996d-a852e459b1b1.png)

## 水果排名
- 目前較為困難之處：

    - 水果種類繁多，分類上較不容易，例如以**農產品行情資料來源**的水果關鍵字：
    
         - 「鳳梨」：釋迦-鳳梨釋迦、鳳梨-其他、鳳梨-牛奶鳳梨、鳳梨-開英、鳳梨-進口、鳳梨-金鑽鳳梨
        
    - 不同資料來源(**農產品行情**與**食品營養成分**)的水果名稱不同，難以對應(Mapping)，下方以**食品營養成分**為例：
    
         - 「鳳梨」：突目1號鳳梨、鳳梨平均值(雜交種)、甘蔗鳳梨、甜蜜蜜鳳梨、金鑽鳳梨、牛奶鳳梨、鳳梨釋迦


![image](https://cloud.githubusercontent.com/assets/5773822/21129036/3aa013ce-c13a-11e6-93c8-b0cefe5cdb60.png)

# 資料來源

1. [農產品行情](http://m.coa.gov.tw/OpenData/FarmTransData.aspx)

1. [食品營養成份資料庫](https://consumer.fda.gov.tw/Food/TFND.aspx?nodeID=178#)

1. [衛生福利部國民健康署-食物營養與熱量](http://www.hpa.gov.tw/BHPNet/Web/healthtopic/TopicArticle.aspx?No=201308300011&parentid=201205100003)

# 分數計算說明

1. 參考上述資料來源**衛生福利部國民健康署-食物營養與熱量**文章中的「國人膳食營養素參考攝取量」，制定「男女各年齡層及身孕狀況之每日各營養素建議量表」，以下稱其為「表1」

1. 運用**食品營養成份資料庫**與**農產品行情**之營養與價格資料，求得「當日各水果每100克所含有的各營養成分份量與價格表」，以下稱其為「表2」

1. 給定各營養成分之權重，維生素系列各為**10%**，葉酸及菸鹼素各為**10%**，鈣、磷、鎂、鐵與鋅各為**2%**。

1. 當使用者選擇某年齡層、性別與身孕狀況後，依據其條件將「表1」篩選為「表3」，並將「表2」各水果營養份量值除以「表3」，求得「各水果每100克可提供單日所需營養建議值之比例」

1. 對各營養成份進行標準化後，將各水果的各營養成份上各自之權重，並乘上10(將水果單位從每100克提升為每1000克)

1. 對各水果的營養成分變數值進行加總後，除以每日各水果之每公斤批發價，即視為該水果每公斤所含的「總營養加總分數」

# License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/3.0/tw/"><img alt="創用 CC 授權條款" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/3.0/tw/88x31.png" /></a>

fruitRank由[Will Kuan](https://github.com/Willdata)、[Conner Chang](https://github.com/ConnerChang)、[Deron Liu](https://github.com/deli1028)和[Andrew Tang](https://github.com/sulaxd)共同製作，以<a rel="license" href="http://creativecommons.org/licenses/by-sa/3.0/tw/">創用CC 姓名標示-相同方式分享 3.0 台灣 授權條款</a>釋出。
