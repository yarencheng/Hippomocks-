sss

```cpp
#include "hippomocks.h"

int legacy_c() {
	return 123;
}

TEST(Demo, legacy_c_test) {

	MockRepository mocks;

	EXPECT_EQ(123, legacy_c());

	mocks.ExpectCallFunc(legacy_c).Return(456);

	EXPECT_EQ(456, legacy_c());
}
```

sss

