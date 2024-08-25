
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


### 7. 참조 레퍼런스

```cpp
#include <stdio.h>
#include <iostream>

using namespace std;

void modify(int& value) {
    value = 10; // 새 공간의 value 변경
    cout << "주소 " << &value << endl; // 주소 0x16fdff3a8
    cout << "값 " << value << endl; // 값 : 10
}

int main() {
    int value = 5;
    cout << "주소 : " << &value << endl; // 주소 : 0x16fdff3a8
    cout << "값 : " << value << endl; // 값 : 5
    modify(value);
    cout << "값 : " << value << endl; // 값 : 10
    
    return 0;
    
}

```


##### & 연산자

1. **참조(Reference)를 선언할 때**

- **문법**: `int& ref = original;`
- **설명**: 변수 `ref`가 변수 `original`을 참조하게 만듭니다. 참조는 원본 변수에 대한 또 다른 이름이 됩니다. 이를 통해 `ref`를 통해 `original`의 값을 변경할 수 있습니다.

```cpp

int x = 5;
int& ref = x; // ref는 x를 참조
ref = 10; // x의 값도 10으로 변경됨


```

2. **주소 연산자(Address-of Operator)로 사용할 때**

- **문법**: `int* ptr = &original;`
- **설명**: 변수 `original`의 메모리 주소를 반환합니다. 이 주소는 포인터에 저장할 수 있습니다.

```cpp
int x = 5;
int* ptr = &x; // ptr는 x의 주소를 가리킴

```


4. **비트 연산자(Bitwise AND Operator)로 사용할 때**

- **문법**: `result = a & b;`
- **설명**: 두 정수의 비트별 AND 연산을 수행합니다. 각 비트가 모두 1인 경우 결과가 1이 됩니다.
   
```cpp

int a = 5; // 0101 
int b = 3; // 0011 
int result = a & b; // 0001 (result는 1)

```


### 8. auto문

STL은 어떤 타입이라도 사용할 수 있도록 구현되어 있다. 하지만 타입이 복잡할 때 실수할 가능성이 있다.
이때 auto 키워드를 사용하면 변수의 타입을 자동으로 추론할 수 있다.

```cpp

#include <iostream>
#include <vector>
#include <map>
#include <string>

int main() {
	auto num = 42;
	cout << num << endl; // 출력값 42


	auto pi = 3.14159; // double로 추론
	cout << pi << endl; 

	auto gretting = string("Hello, world!");
	cout << greeting << endl; // 출력값 : Hello, world!

	return 0;
}
```


### 9. 범위 기반 반복문

***배열이나 컨테이너의 모든 원소를 순회할 때 사용한다. 기본 반복문보다 구현이 쉽고, 가독성이 좋다.


```cpp

#include <iostream>
#include <vector>
#include <map>
#include <set>

using namespace std;

int main() {
    // vector 예
    vector<int> vec = {1, 2, 3, 4, 5};
    for (int num: vec){
        cout << num << " ";
    }
    
    cout << endl;
    // 1 2 3 4 5
    // map 예
    map<string, int> fruitMap = {{"apple", 1}, {"banana", 2}, {"cherry", 3}};
    for (const auto& pair: fruitMap){
        cout << pair.first << " = "<< pair.second << " ";
    }
    
    cout << endl;
    // apple = 1 banana = 2 cherry = 3

    // set 예
    set<string> fruitSet = {"apple", "banana", "cherry"};
    cout << "Set: ";
    for (const auto& fruit : fruitSet){
        cout << fruit << " ";
    }
    
    cout << endl;
    // Set: apple banana cherry
    
    return 0;
}

```



### 10. 반복자(iterator)

***반복자는 C++에서 컨테이너(벡터, 셋, 맵 등의) 종류와 관계없이 원소들을 순회하고 접근할 수 있게 해준다.

###### 순방향 반복자

```cpp

#include <algorithm> // find 함수를 위한 헤더
#include <iostream>
#include <vector>

using namespace std;

int main() {
    vector<int> vec = {10, 20, 30, 40, 50};
    
    for (auto it = vec.begin(); it != vec.end(); ++it){
        cout << *it << " ";
    }
    
    cout << endl;
    // 10 20 30 40 50
    
    auto result = find(vec.begin(), vec.end(), 30);
    if (result != vec.end()){
        cout << "FOUND: " << *result << endl;
    } else {
        cout << "Not found" << endl;
    }
    // FOUND: 30
    return 0;
}

```

```cpp

#include <iostream>
#include <map>
using namespace std;

int main() {
    map<string, int> myMap = {{"apple", 1},{"banana", 2},{"cherry", 3}};
    
    for (auto it = myMap.begin(); it != myMap.end(); ++it){
        cout << it->first << ": " << it->second << endl;
    }
    /**
     apple: 1
     banana: 2
     cherry: 3
     */
    
    auto result = myMap.find("banana");
    if(result != myMap.end()){
        cout << "Found: " << result->first << " -> " << result->second << endl;
    } else {
        cout << "Not found" << endl;
    }
    
    return 0;
}

```



###### 역방향 반복자
rbegin(), rend()를 사용한다. 
rbegin()은 맨 마지막 원소의 위치, rend()는 맨 처음 원소의 바로 직전 위치

```cpp

#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

int main(){
    vector<int> vec = {10, 20, 30, 40, 50};
    
    // 순회하고 출력
    for(auto it = vec.rbegin(); it != vec.rend(); ++it){
        cout << *it << " ";
    }
    cout << endl;
    // 50 40 30 20 10

    auto result = find(vec.rbegin(), vec.rend(), 30);
    if(result != vec.rend()){
        cout << "Found: " << *result << endl;
    } else {
        cout << "Not found" << endl;
    }
    // Found: 30
    
    return 0;
}


```



### 11. STL 컨테이너

***STL 컨테이너는 데이터를 저장하는 객체(벡터, 셋, 맵, 우선순위 큐)


