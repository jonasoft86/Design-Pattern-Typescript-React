# [Day5] 老闆：來一碗大腸麵線 ─ 工廠方法(Factory Method)

嗨 大家好 我是一路爬坡的阿肥

轉眼間 中秋連假就要結束了  
不過很快雙十連假就可以飛去澎湖渡假啦(灑花)  
啊 等一下(是真的突然想到)  
那不就表示就連在澎湖也要記得發文嗎 😳

---

## 情境描述

阿肥工作幾年後，終於存到了圓夢基金，在附近廟口開一家麵線店，希望可以看到每位客人吃完麵線後滿足的笑容。

阿肥只會做簡單的滷大腸跟處理蚵仔，所以目前只有大腸麵線跟蚵仔麵線。客人只要在菜單上勾哪一個，並且交給阿肥，稍等片待就可以拿到熱騰騰的麵線了。

然而，這兩種麵線看似作法都差不多，但是仔細一看原來有些不同：

- 大腸麵線： 麵線糊 > 大腸 > 香菜 > 醋 ...(客人的需求) > 裝袋
- 蚵仔麵線：麵線糊 > 蚵仔 > 胡椒粉 > 蒜泥 ...(客人的需求) > 裝袋

阿肥說這是他的堅持，每種料都有它適合搭配的佐料，除非客人有特別要求，不然這兩種麵線加的會是不同的佐料

## 暴力解決法

每收到菜單，阿肥就按照腦海中的順序一一加入主料跟佐料。以程式來看的話就像這樣：

```typescript
type T_Flavor = "intestine" | "oyster";
interface I_Order {
  product: T_Flavor;
  tableware?: string[];
  bag?: boolean;
}

//TODO 待改
class VermicelliStore {
  /**
   * order: 接收菜單
   */
  public static order(order: I_Order): I_Order {
    let result: I_Order = { ...order, product: null };
    if (order.product == "intestine")
      result.product = this.makeIntestineFlavor();
    else if (order.product == "oyster")
      result.product = this.makeIntestineFlavor();

    result.product.prepareTableware();
    result.product.bagging();

    return result;
  }
  /**
   * prepareTableware: 準備餐具
   */
  private static prepareTableware() {
    //...
  }
  /**
   * bagging: 準備裝袋
   */
  private static bagging() {
    //...
  }
  /**
   * makeIntestineFlavor: 製作大腸麵線
   */
  private static makeIntestineFlavor() {
    //...
  }
  /**
   * makeOysterFlavor: 製作蚵仔麵線
   */
  private static makeOysterFlavor() {
    //...
  }
}
```

## 簡單工廠

## 工廠方法

## 小結

---

### 參考資料

- [設計模式 - 工廠方法及抽象工廠](https://blog.techbridge.cc/2017/05/22/factory-method-and-abstract-factory/)
