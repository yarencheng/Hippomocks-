# Legacy C function

```cpp
#include "hippomocks.h"

int legacy_c() {
    return 123;
}

TEST(Demo, legacy_c_test) {

    MockRepository mocks;

    EXPECT_EQ(123, legacy_c());                   // pass

    mocks.ExpectCallFunc(legacy_c).Return(456);

    EXPECT_EQ(456, legacy_c());                   // pass
}
```

# C++ static function

```cpp
#include "hippomocks.h"

class A{
public:
    static int staticFun() {
        return 123;
    }
};

TEST(Demo, static_test) {

    MockRepository mocks;

    EXPECT_EQ(123, A::staticFun());                     // pass

    mocks.ExpectCallFunc(A::staticFun).Return(456);

    EXPECT_EQ(456, A::staticFun());                     // pass
}
```



