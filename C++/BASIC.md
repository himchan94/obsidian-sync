
### SUMMARY

C++ 가지고 놀기 위해 필요한 필수 문법들


### 1. 빌트인 데이터 타입
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


### 2. 형변환

```cpp
#include <iostream>

using namespace sstd;

int main() {
	int i = 65;
	float f = 5.2f;

// 암시적 형 변환(메모리가 큰 float으로 변환됨)
cout << d << endl; // 70.2

// 명시적 형변환
cout << static_cast<int>(d) << endl; // 70
cout << static_cast<int>(i) << endl; // 'A'

return 0;

}
```

### 3. 문자열 선언 및 초기화

```cpp
#include <iostream>
#include <string>

using namespace std;

int main() {
string str1;
string str2 = 'Hello, World!';
string str3(str2) // 문자열 복사
string str4(str2, 0, 5) // 문자열 부분 복사 초기화
string str5(10, '*') // 반복된 문자로 문자열 초기화 "**********"

return 0;
}


```

### 4. 문자열 찾기

**find(찾으려는 문자열)**

**find(찾으려는 문자열, 탐색 시작 위치)**

***찾지 못하면 string::npos 를 반환한다.*


```cpp
#include <iostream>
#include <string>

using namespace std;

int main() {



}



```