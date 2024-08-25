
### 1. STL 컨테이너

***STL 컨테이너는 데이터를 저장하는 객체(벡터, 셋, 맵, 우선순위 큐)


###### 1) 벡터

```cpp

#include <vector>

using namespace std;

int main() {
    vector<int> v;
    vector<int> v2 = {1,2,3,4,5};
    vector<int> v3(4, 3);
    vector<int> v4(v3); // 복사

    return 0;
}


```

2차원 배열
```cpp

#include <iostream>
#include <vector>

using namespace std;

int main(){
    vector<vector<int>> v1;
    
    int rows = 3;
    int cols = 4;
    vector<vector<int>> v2(rows, vector<int>(cols));
    
    int val = 9;
    vector<vector<int>> v3(rows, vector<int>(cols, val));
    
    vector<vector<int>> v4 = {
        {1,2,3,},
        {4,5,6},
        {7,8,9},
    };

    return 0;
}


```

```cpp

#include <iostream>
#include <vector>

using namespace std;

int main(){
    vector<int> v = {2, 3, 4, 5};
    
    // 맨 뒤에 원소 삽입
    v.push_back(6);
    
    // 맨 뒤의 원소 삭제
    v.pop_back();

    return 0;
}
```

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main(){
    vector<int> v = {2, 3, 4, 5};

    // 맨 앞에 원소 삽입
    v.insert(v.begin(), 1) // v: {1, 2, 3, 4, 5}
    
    // 맨 앞에 원소 삭제
    v.erase(v.begin()); // v: {2, 3, 4, 5}
    
    return 0;
}
```

##### 2) 셋
***Set은 중복을 허용하지 않고, 저장된 데이터를 자동으로 정렬하는 컨테이너


```cpp
#include <iostream>
#include <set>

using namespace std;

int main() {
    set<int> s1; // 빈 셋 선언
    set<int> s2 = {3, 1, 3, 2, 5};
    set<int> s3(s2); // 다른 셋을 사용하여 초기화
    
    
    return 0;
}
```

```cpp
#include <iostream>
#include <set>

using namespace std;

int main() {
    set<int> numbers = {1, 2, 3, 4, 5};
    int targets[] = {3, 7};
    
    for(int target: targets){
        auto it = numbers.find(target);
        
        if(it != numbers.end()){
            cout << "원소 " << target << "를 찾았습니다. 값: " << *it << endl;
        } else {
            cout << "원소 "<< target << "를 찾지 못했습니다." << endl;
        }
    }
    // 원소 3를 찾았습니다. 값: 3
    // 원소 7를 찾지 못했습니다.
    return 0;
}

```

```cpp
#include <iostream>
#include <set>

using namespace std;

int main() {
    set<int> s = {1, 3, 2, 1, 5};
    
    // 원소 4 삽입
    s.insert(4);
    
    // 원소 2 삭제
    s.erase(2);
    
    // 원소 4가 있는지 확인 후 삭제
    auto it = s.find(4);
    if(it != s.end()){
        s.erase(it);
    }
    return 0;
}

```


##### 3) 맵

***Map은 키와 값을 쌍으로 갖는 컨테이너다. 

***키와 값의 쌍을 entry라고 하며, STL에서는 std:pair 타입으로 표현한다.

***내부는 균형 이진 탐색트리로 구성되어 있기 때문에 항상 키 값을 기준으로 데이터가 자동 정렬된다.

```cpp
#include <map>
#include <string>
using namespace std;

int main() {
    // 빈 맵 선언
    map<string, double> employeeSalaries;
    
    map<string, double> studentGrades = {
        {"John", 3.7},
    };
    
    return 0;
}
```


***맵에서 특정 키에 접근
- [] 연산자 활용하기 // studentScores["Alice"]
- find() 메서드 할용하기 // studentScored.find("Charlie")

주의할 점은 [] 연산자를 통해 접근하려는 키가 맵에 없으면, 맵에 현재 키를 추가한다.
***즉, 맵에 없는 키에 접근하려고 하면 오류가 발생하는 것이 아니라 새로운 키가 만들어진다.

```cpp

#include <iostream>
#include <map>

using namespace std;

int main(){
    // 맵 생성
    map<string, int> studentScores;
    
    // 키-값 쌍 추가
    studentScores["Alice"] = 95;
    studentScores["Bob"] = 88;
    studentScores["Charlie"] = 92;
    
    // [] 연산자를 사용하여 키에 접근 - 키가 있는 경우
    int scores = studentScores["Alice"];
    cout << scores << endl; /// 출력 값: 95
    
    // [] 연산자를 사용하여 키에 접근 - 키가 없는 경우
    int score2 = studentScores["rabiit"];
    cout << score2 << endl; // 출력값 : 0
    
    // find() 메서드를 사용하여 키에 접근
    auto it = studentScores.find("Charlie"); //
    if(it != studentScores.end()){
        int score3 = it->second;
        cout << score3 << endl; // 출력값: 92
    }
    
    return 0;
}

```


```cpp
#include <iostream>
#include <map>
#include <string>

using namespace std;

int main(){
    map<string, int> myMap = {{"Apple", 1}, {"Banana", 2}, {"Cherry", 3}};
    
    myMap["Banana"] = 10;
    
    for(auto it: myMap){
        cout << it.second << endl;
    }
    return 0;
}

```

```cpp
#include <iostream>
#include <map>
#include <string>

using namespace std;

int main(){
    map<int, string> myMap;
    
    // 삽입
    myMap.insert(make_pair(1, "Apple"));
    myMap.insert({2, "Banana"});
    myMap[3] = "Cherry";
    
    // 삭제
    myMap.erase(2);
    for (const auto &pair : myMap){
        cout << pair.first << ": " << pair.second << endl;
    }
    /**
     1: Apple
     3: Cherry
     */
    
    auto it = myMap.find(3);
    if(it != myMap.end()){
        myMap.erase(it);
    }
    
    // 삭제 후 맵 출력
    for(const auto &pair : myMap){
        cout << pair.first << ": " << pair.second << endl;
    }
    /**
     1: Apple
     */
    return 0;
}
```


##### 4) 정렬되지 않은 셋과 맵

***내부적으로 이진 탐색 트리가 아닌 해시 기반이기 때문에 데이터를 자동정렬하지 않는다. 

***시간복잡도는 O(1) 이지만, 최악의 경우 O(N)일 수도 있다.

```cpp
#include <iostream>
#include <unordered_set>

using namespace std;

int main(){
    unordered_set<int> myUnorderedSet;
    
    // 삽입
    myUnorderedSet.insert(3);
    myUnorderedSet.insert(1);
    myUnorderedSet.insert(4);
    myUnorderedSet.insert(2);
    
    for (int num: myUnorderedSet){
        cout << num << " ";
    }
    cout << endl;
    // 2 4 1 3
    
    return 0;
}
```

```cpp
#include <iostream>
#include <unordered_map>

using namespace std;

int main(){
    unordered_map<string, int> myUnorderedMap;
    
    // 삽입
    myUnorderedMap["apple"] = 3;
    myUnorderedMap["banana"] = 1;
    myUnorderedMap["cherry"] = 4;
    myUnorderedMap["date"] = 2;

    for (const auto& pair : myUnorderedMap){
        cout << pair.first << ": " << pair.second << endl;
    }
    /**
     date: 2
     cherry: 4
     banana: 1
     apple: 3
     */
    
    return 0;
}

```


### 2. STL의 알고리즘


##### 1) count

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main() {
    vector<int> v = {1, 4, 3, 4, 5, 4, 5};
    
    // 5라는 값이 벡터 v에 몇 번 나타나는지 세기
    auto ret = count(v.begin(), v.end(), 5);
    
    cout << ret << endl;
    return 0;
}

```


##### 2) sort

- sort(시작 반복자, 끝 반복자)
- sort(시작 반복자, 끝 반복자, 비교 함수)
