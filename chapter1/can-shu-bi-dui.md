# 參數比對

利用 Call::With\(\) 比對參數

```cpp
#include "hippomocks.h"

bool isOdd(int i) {
	return 0 != i % 2;
}

TEST(Demo, With) {

	MockRepository mocks;

	EXPECT_TRUE(isOdd(1));                              // pass
	EXPECT_FALSE(isOdd(2));                             // pass

	mocks.ExpectCallFunc(isOdd).With(1).Return(false);
	mocks.ExpectCallFunc(isOdd).With(2).Return(true);

	EXPECT_FALSE(isOdd(1));                             // pass
	EXPECT_TRUE(isOdd(2));                              // pass
}
```

也支援多個參數

```cpp
#include "hippomocks.h"

bool isSame(int a, int b) {
	return a == b;
}

TEST(Demo, With) {

	MockRepository mocks;

	EXPECT_TRUE(isSame(1, 1));                                 // pass
	EXPECT_FALSE(isSame(1, 2));                                // pass

	mocks.ExpectCallFunc(isSame).With(1, 1).Return(false);
	mocks.ExpectCallFunc(isSame).With(1, 2).Return(true);

	EXPECT_FALSE(isSame(1, 1));                                // pass
	EXPECT_TRUE(isSame(1, 2));                                 // pass
}
```

透過 Match 傳入自訂的方法比對參數

```cpp
#include "hippomocks.h"

bool isOdd(int i) {
	return 0 != i % 2;
}

TEST(Demo, Match) {

	MockRepository mocks;

	EXPECT_TRUE(isOdd(1));                                    // pass
	EXPECT_FALSE(isOdd(2));                                   // pass
	
	auto m1 = [](int i){ return i == 1; };
	auto m2 = [](int i){ return i == 2; };

	mocks.ExpectCallFunc(isOdd).Match(m1).Return(false);
	mocks.ExpectCallFunc(isOdd).Match(m2).Return(true);

 	EXPECT_FALSE(isOdd(1));                                   // pass
        EXPECT_TRUE(isOdd(2));                                    // pass
}
```



