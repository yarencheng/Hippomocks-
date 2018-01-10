# Call::After

使用 After 讓 MockRepository 在 deconstruct 的時候檢查順序。

```cpp
#include "hippomocks.h"

int first() {
    return 1;
}

int second() {
    return 2;
}

TEST(Demo, After_pass) {                                             // pass

    MockRepository mocks;

    Call& c1 = mocks.ExpectCallFunc(first).Return(111);

    Call& c2 = mocks.ExpectCallFunc(second).After(c1).Return(222);

    first();
    second();
}

TEST(Demo, After_fail) {                                             // fail

    MockRepository mocks;

    Call& c1 = mocks.ExpectCallFunc(first).Return(111);

    Call& c2 = mocks.ExpectCallFunc(second).After(c1).Return(222);

    second();
    first();    
}
```

好像沒有提供 Before ?

