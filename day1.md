#### Week 1 – Arrays, Two Pointers, Sliding Window

**Topics to complete**
- Arrays, prefix sums.
- Two pointers, sliding window.
- Simple implementation and math.

***Problems to get you started and help you get fimiliar with how cf works***
1.[4A Watermelon (implementation, 800)](https://codeforces.com/problemset/problem/4/A​)

**LOGIC:** 
  - *notihing complex just even odd logic*
```cpp
#include <bits/stdc++.h>
using namespace std;
int main() {
    int n;
    cin>>n;
    if(n < 4) {
        cout << "NO" << endl;
        return 0;
    }
    if(n%2)
        cout<<"NO"<<endl;
    else
        cout<<"YES"<<endl;
    return 0;
}
```

2.[71A Way Too Long Words (implementation, 800)](https://codeforces.com/problemset/problem/71/A​)

**LOGIC** ** *string length*
```cpp
#include <bits/stdc++.h>
using namespace std;
int main() {
    int t;
    cin>>t;
    while (t--)
    {
        
        string a;
        cin>>a;
        int k = a.size();
        if(k>10)
            cout<<a[0]<<k-2<<a[k-1]<<endl;
        else
            cout<<a<<endl;
    }
    
    return 0;
}
```

3.[231A Team (implementation, 800)](https://codeforces.com/problemset/problem/231/A​)

**LOGIC** 
  - *compare if atleast of them know the problem and increase count*
  - *input was in 0 and 1 so used & and | operator*
```cpp
#include <bits/stdc++.h>
using namespace std;
int main() {
    int n;
    cin>>n;
    
    int a, b, c, count = 0;
    while(n--)
    {
        cin>>a>>b>>c;
        if(a & b | b & c | c & a)
            count++;
    }
    cout<<count<<endl;
    
    return 0;
}
```

4.[1669A Division? (implementation, 800)](https://codeforces.com/problemset/problem/1669/A)

**LOGIC** 
  - *if else tree *
```cpp
#include <bits/stdc++.h>
using namespace std;
int main() {
    int t;
    while (t--)
    {
        int n;
        cin>>n;
        if(n<1400)
        {
            cout<<"Division 4"<<endl;
        }
        else if(n>=1400 && n<1600)
        {
            cout<<"Division 3"<<endl;
        }
        else if(n>=1600 && n<1900)
        {
            cout<<"Division 2"<<endl;
        }
        else
        {
            cout<<"Division 1"<<endl;
        }
    }
    
    return 0;
}
```


















**Codeforces Problem Selection**
- Daily total: **6–8 problems**.
- Difficulty bands:
  - 3–4 problems in **800–1000** with tags: `implementation`, `two pointers`, `greedy`.
  - 2–3 problems in **1000–1200** with tags: `two pointers`, `prefix sums`.
- Strategy:
  - Start each day with **2 very easy implementation problems**.
  - Then pick **2 problems tagged `two pointers`** (one easy, one medium).
  - End with **1 prefix sums or simple math problem**.

**Contests (2 Div 3/Div 4)**
- Aim to solve **A, B, and attempt C**.
- After contest, upsolve **all A–C**, even if solved, to solidify patterns.

**Success Criteria**
- Comfortable recognizing two-pointer/sliding-window patterns.
- Can implement them with almost no bugs.