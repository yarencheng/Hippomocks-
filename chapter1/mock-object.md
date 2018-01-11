# Mock Object

除了 C++ static function 和 C function，Hippomocks 也提供 mock class 的方法。

```cpp
#include "hippomocks.h"

class SomeConcrete{
public:
    virtual ~SomeConcrete () {};
    virtual int vertualFunction() { return 0; };
};

TEST(HippoMocksDemo, Object)
{
    MockRepository mocks;

    SomeConcrete* some = mocks.Mock<SomeConcrete>();
    
    mocks.ExpectCall(some, SomeConcrete::vertualFunction).Return(123);

    EXPECT_EQ(123, some->vertualFunction());                                // pass
}
```

pure virtual function 也可以

```cpp
#include "hippomocks.h"

class SomeInterface{
public:
	virtual ~SomeInterface () {};
	virtual int pureVertualFunction() = 0;
};

TEST(HippoMocksDemo, pureVertualFunction)
{
	MockRepository mocks;

	SomeInterface* some = mocks.Mock<SomeInterface>();
	
	mocks.ExpectCall(some, SomeInterface::pureVertualFunction).Return(123);

	EXPECT_EQ(123, some->pureVertualFunction());                              // pass
}
```

但是 Hippomocks 無法 mock 不是 virtual 的 function

```cpp
#include "hippomocks.h"

class SomeConcrete{
public:
	virtual ~SomeConcrete () {};
	int notVertualFunction() { return 0; };
};

TEST(HippoMocksDemo, notVertualFunction)
{
	MockRepository mocks;

	SomeConcrete* some = mocks.Mock<SomeConcrete>();
	
	mocks.ExpectCall(some, SomeConcrete::notVertualFunction).Return(123);

	EXPECT_EQ(123, some->notVertualFunction());                            // fail
}
```



