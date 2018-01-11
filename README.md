# 簡介

Hippomocks 是一個 C++ 的 mocking framework。它可以抽換掉 C++ static function 或是 legacy C function。

當撰寫 C++ 的 unit test 的時候，目前主流的 unit test framework 都沒有辦法針對 legacy code 做 mock，導致如果一個 C++ class 有使用到 C++ static function 或是 legacy C function 將很難寫出可以測試的程式\(testable code\)，Hippomocks 雖然不能解決 testable 的問題，但是可以透過抽換掉 legacy code 讓一些不能被測試的程式還是可以寫出 unit test。

[Hippomocks 官方 Wiki](https://www.gitbook.com/book/yarencheng/hippomocks/edit#)

#### 先減少耦合

這裡要特別聲明，在寫 C++ unit test 的時候，如果你發現你一定要 mock C++ static function 才能寫 unit test 的時候，代表你程式的耦合\(coupling\)太高，你應該優先考慮修改你的程式碼，降低未來的技術負債，除非萬不得已才使用 Hippomocks 或是其他類似的工具。

