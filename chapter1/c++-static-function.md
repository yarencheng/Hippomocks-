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



