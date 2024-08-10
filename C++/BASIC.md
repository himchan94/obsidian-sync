
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
//

//  string_test.cpp

//  cpp_programming

//

//  Created by himchan on 2024/08/10.

//

  
#include <iostream>
#include <string>

  

using namespace std;

int main() {

    string str = "Hello, C++ World!";

    // Hello 문자열 찾기
    size_t pos1 = str.find("Hello");
    cout << pos1 << endl;

    // C 문자 찾기
    size_t pos2 = str.find('C');
    cout << pos2 << endl; // 7

    // Hello 문자열 찾기 시작 인덱스 지정
    size_t start_index = 2;
    size_t pos3 = str.find("Hello", start_index);
    cout << pos3 << endl; // 18446744073709551615
    cout << (pos3 == string::npos) << endl; // 1

    // 존재하지 않는 문자열 찾기
    size_t pos4 = str.find("Python");
    cout << pos4 << endl; // 18446744073709551615

    return 0;

}

```

### 5. 문자열 추가, 수정

```cpp

#include <iostream>

#include <string>

  

using namespace std;

int main() {

    string str = "APPLE";

    // 문자열 추가

    str += ", World!";
    cout << str << endl; // APPLE, World!

    // 문자열 수정

    str[7] = 'P';
    cout << str << endl; // APPLE, Porld!

  

    str.replace(7, 4, "Col");
    cout << str << endl; // APPLE, Cold!

    return 0;

}

```


### 6. 상수 레퍼런스

***C++에서는 함수의 인수로 값을 전달할 때 값을 복사한다. (call by value) 

***함수가 호출될 때마다 복사 비용이 든다. (함수의 인수로 STL 컨테이너 같은 객체 혹은 구조체 등을 넘길 때 이 복사 비용이 성능에 영향을 준다.)***



```cpp

#include <stdio.h>
#include <iostream>
using namespace std;

void modify(int value) {
    value = 10; // 새 공간의 value 변경
    cout << "주소 " << &value << endl; // 주소 0x16fdff36c
    cout << "값 " << value << endl; // 값 : 10
}

int main() {
    int value = 5;
    cout << "주소 : " << &value << endl; // 주소 : 0x16fdff3a8
    cout << "값 : " << value << endl; // 값 : 5
    modify(value);
    cout << "값 : " << value << endl; // 값 : 5
    
    return 0;
    
}
```

