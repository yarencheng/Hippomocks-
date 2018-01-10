# ExpectCall vs OnCall

在 mock function 的時候，有兩種方使可以做到 ExpectCall 和 OnCall，兩種都可以定義 mock 的行為，但是 ExpectCall 會檢查是否有執行，OnCall 則不會。

```cpp
#include "hippomocks.h"

bool isOdd(int i) {
	return 0 != i % 2;
}

TEST(Demo, ExpectCall) {                                  // fail

    MockRepository mocks;

    mocks.ExpectCallFunc(isOdd).Return(false);
}

TEST(Demo, OnCall) {                                      // pass

    MockRepository mocks;

    mocks.OnCallFunc(isOdd).Return(false);
}
```



