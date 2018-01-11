# 次數限制

提供方法檢查 mock function 執行的次數，只支援一般的 virtual function mock，不支援 C++ static 和 C function

```cpp
#include "hippomocks.h"

class SomeConcrete{
public:
    virtual ~SomeConcrete () {};
    virtual void fn() {};
};

TEST(HippoMocksDemo, Times_Pass)
{
    MockRepository mocks;

    SomeConcrete* some = mocks.Mock<SomeConcrete>();
    mocks.ExpectCalls(some, SomeConcrete::fn, 2);           // pass

    some->fn();

    some->fn();
}

TEST(HippoMocksDemo, Times_Fail)
{
    MockRepository mocks;

    SomeConcrete* some = mocks.Mock<SomeConcrete>();
    mocks.ExpectCalls(some, SomeConcrete::fn, 2);           // Fail

    some->fn();
}
```



