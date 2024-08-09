
### SUMMARY

C++ 가지고 놀기 위해 필요한 필수 문법들


### 빌트인 데이터 타입
```cpp

#include <iostream>

using namespace std;

int main() {
	int a = 13;
	int b = 4;

// 비교 연산이 참이면 1을, 거짓이면 0을 반환한다.
cout << (a == b) << endl; // 0
cout << (a != b) << endl;
cout << (a > b) << endl;
cout << (a < b) << endl;
cout << (a >= b) << endl;
cout << (a <= b) << endl;

// 비트 연산
cout << (a & b) << endl; // 4
cout << (a | b) << endl; // 13



double d = 2.5;
float f = 1.5f;

cout << sizeof(d) << endl; // 8
cout << sizeof(f) << endl; // 4

cout << d << " " << f << endl; // 2.5 1.5
cout << d + f << endl; // 4
cout << d- f << endl; // 1
cout << d * f << endl; // 3.75;
cout << d / f << endl; // 1.66667



return 0;
}



```