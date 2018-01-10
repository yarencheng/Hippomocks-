# 動作

透過 Call::Return 直接指定 回傳值

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

Call::Throw 可以指定要丟出例外

```cpp
#include "hippomocks.h"

void no_throw() {
	return;
}

TEST(Demo, Throw) {

	MockRepository mocks;

	EXPECT_NO_THROW({                                   // pass
		no_throw();
	});

	std::exception e;

	mocks.ExpectCallFunc(no_throw).Throw(e);

	EXPECT_THROW({                                      // pass
		no_throw();
	}, std::exception);
}
```



透過 Call::Do 傳入 function handler 可以執行更複雜的動做

```cpp
#include "hippomocks.h"

bool isOdd(int i) {
	return 0 != i % 2;
}

TEST(Demo, Do) {

	MockRepository mocks;

	EXPECT_TRUE(isOdd(1));                                       // pass

	auto fn = [](int){

		cout << "do something special ..." << endl;

		return false;
	};

	mocks.ExpectCallFunc(isOdd).Do(fn);

	EXPECT_FALSE(isOdd(1));                                      // pass
}
```



