# 實作原理

> 這頁尚未完成

Hippomocks 在 runtime 會去修改 assembly，當有程式去呼叫被 mock 的物件時，並不會去呼叫原本的實作，會轉而去呼叫 Hippomocks 所產生的 mock 物件。目前支援兩個平台 x86 和 ARM。

---

#### x86

TBD

[https://github.com/dascandy/hippomocks/blob/master/HippoMocks/hippomocks.h\#L298](https://github.com/dascandy/hippomocks/blob/master/HippoMocks/hippomocks.h#L298)

---

#### ARM

TBD

[https://github.com/dascandy/hippomocks/blob/master/HippoMocks/hippomocks.h\#L314](https://github.com/dascandy/hippomocks/blob/master/HippoMocks/hippomocks.h#L314)



