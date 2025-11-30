## I will continue from day one of getting familier with codeforces


1691B Shoe Shuffling (two pointers/greedy, 1000) https://codeforces.com/problemset/problem/1691/B

**LOGIC**
  - *I learned to used iota*
  - *iota(start, end, value the array starts from in 0th index)*
    ```cpp
    vector<int> p(n);
    iota(p.begin(), p.end(), 1);
    iota(start, end, value the array starts from in 0th index)
    ```
  - *we use 2 pointers one i for start of sub array and j for end of subarray*
  - *if the subarray ha atlest 2 elements then it is rotated*
  - *if we find a sub array with 1 element our flag is set to false so at the end we print -1*
  - *else we just pring the array p which we modified*

```cpp
#include <bits/stdc++.h>
using namespace std;
int main() {
    int t;
    cin >> t;
    while(t--) {
        int n;
        cin >> n;
        vector<int> s(n);
        for(int &x : s) cin >> x;

        vector<int> p(n);
        iota(p.begin(), p.end(), 1);

        bool ok = true;
        int i = 0; 

        while(i < n)
        {
            int j = i;
            while (j < n && s[j] == s[i]) j++;

            int len = j - i;
            if ( len == 1 )
            {
                ok = false;
                break;
            }
            for(int k = 0; k < len; k++)
                p[i+k] = i + ((k + 1) % len) + 1;
            i = j;
        }
        if ( !ok )
        {
            cout << -1 << endl;
            continue;
        }

        for(int k = 0; k < n; k++)
            cout << p[k] << " ";
        cout << endl;


    }
    return 0;
}
``` 

58A Chat Room (two pointers/strings, 1000) https://codeforces.com/problemset/problem/58/A​

**LOGIC**
  - *make string hello and counter k = 0*
  - *comparte hello string with input string s[i] == check[k] increase counter*
  - *if counter = 5 means we have hello if not the we dont
```cpp
#include <bits/stdc++.h>
using namespace std;
int main() {
    string s, check = "hello";
    cin >> s;
    int n = s.length();
    int k = 0;
    for(int i = 0; i < n; i++)
    {
        if(s[i] == check[k])
            k++;
        if(k == 5)
        {
            cout << "YES";
            return 0;
        }
        
    }
    cout << "NO";
    
    return 0;
}
``` 
**below question i had to do 1 times to optimize the time complixity**
1744C Traffic Light (two pointers, 1000) https://codeforces.com/problemset/problem/1744/C

**LOGIC**
  - *simple question of two pointers*
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    int t;
    cin >> t;
    
    while(t--) {
        int n;
        char c;
        cin >> n >> c;
        string s;
        cin >> s;
        
        if(c == 'g') {
            cout << 0 << endl;
            continue;
        }
        
        // Precompute the distance to next 'g' for each position
        vector<int> next_g(n);
        int last_g = -1;
        
        // First pass: find positions from right to left
        for(int i = n - 1; i >= 0; i--) {
            if(s[i] == 'g') {
                last_g = i;
            }
            next_g[i] = last_g;
        }
        
        // If no 'g' found in first pass, wrap around
        if(last_g == -1) {
            // This shouldn't happen based on problem constraints
            cout << 0 << endl;
            continue;
        }
        
        int ans = 0;
        
        for(int i = 0; i < n; i++) {
            if(s[i] == c) {
                int dist;
                if(next_g[i] == -1) {
                    // No 'g' after position i, wrap around to first 'g'
                    dist = n - i + next_g[0];
                } else if(next_g[i] >= i) {
                    // 'g' found after position i
                    dist = next_g[i] - i;
                } else {
                    // Wrap around case
                    dist = n - i + next_g[0];
                }
                ans = max(ans, dist);
            }
        }
        
        cout << ans << endl;
    }
    
    return 0;
}
``` 

1832B Maximum Sum (two pointers/prefix, 1000) https://codeforces.com/problemset/problem/1832/B​

**LOGIC**
  - *chutiya question language wasn't clear enough but easy*
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    int t;
    cin >> t;
    
    while (t--) {
        int n, k;
        cin >> n >> k;
        
        vector<long long> a(n);
        long long total = 0;
        
        for (int i = 0; i < n; i++) {
            cin >> a[i];
            total += a[i];
        }
        
        // Sort the array
        sort(a.begin(), a.end());
        
        // Precompute prefix sums for minimums
        vector<long long> prefix(n + 1, 0);
        for (int i = 0; i < n; i++) {
            prefix[i + 1] = prefix[i] + a[i];
        }
        
        // Precompute suffix sums for maximums
        vector<long long> suffix(n + 1, 0);
        for (int i = n - 1; i >= 0; i--) {
            suffix[n - i] = suffix[n - i - 1] + a[i];
        }
        
        long long max_sum = 0;
        
        // Try all possible combinations of operations
        // x = number of type-1 operations (remove 2 minimums)
        // k-x = number of type-2 operations (remove 1 maximum)
        for (int x = 0; x <= k; x++) {
            int num_min_remove = 2 * x;
            int num_max_remove = k - x;
            
            // Sum of smallest 2*x elements using prefix sum
            long long sum_removed = prefix[num_min_remove];
            
            // Add sum of largest (k-x) elements using suffix sum
            sum_removed += suffix[num_max_remove];
            
            // Remaining sum
            long long remaining_sum = total - sum_removed;
            max_sum = max(max_sum, remaining_sum);
        }
        
        cout << max_sum << "\n";
    }
    
    return 0;
}
``` 

479A Expression (math/prefix-like, 1000) https://codeforces.com/problemset/problem/479/A

**LOGIC**
  - *dumb ahh question*
```cpp
#include <bits/stdc++.h>
using namespace std;
int main() {
    int a, b, c;
    cin >> a >> b >> c;
    int an = a+b+c;
    an = max(an,a*b*c);
    an = max(an,a+b*c);
    an = max(an,a*b+c);
    an = max(an,(a+b)*c);
    an = max(an,a*(b+c));
    cout << an << endl;
    return 0;
}
``` 

466A Cheap Travel (greedy/two pointers, 1200) https://codeforces.com/problemset/problem/466/A​

**LOGIC**
  - *normal maths*
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    int n, m, a, b;
    cin >> n >> m >> a >> b;
    
    int min_cost = INT_MAX;
    
    // Option 1: Buy only single tickets
    int cost1 = n * a;
    min_cost = min(min_cost, cost1);
    
    // Option 2: Buy only special tickets (ceiling division)
    int num_special = (n + m - 1) / m;  // This is ceil(n/m)
    int cost2 = num_special * b;
    min_cost = min(min_cost, cost2);
    
    // Option 3: Buy some special tickets + individual tickets for remainder
    int full_special = n / m;
    int remainder = n % m;
    int cost3 = full_special * b + remainder * a;
    min_cost = min(min_cost, cost3);
    
    cout << min_cost << endl;
    
    return 0;
}
}
``` 

492B Vanya and Lanterns (two pointers/greedy, 1200) https://codeforces.com/problemset/problem/492/B

**LOGIC**
  - *learned new thing while solving tha cin and cout are synchronized with c stream (scanf and printf)*
  - *so we use below to cut the connection to make it much faster*
    ```cpp
        ios_base::sync_with_stdio(false);
        cin.tie(NULL);
    ```
  - *we use "fixed" so it prints 0.0005 amd not 5e-4*
  - *sutpreceion(n) to set prision*
    ```cpp
    double x = 3.14159265359;
    cout << fixed << setprecision(2) << x;  // Prints: 3.14
    cout << fixed << setprecision(5) << x;  // Prints: 3.14159
    cout << fixed << setprecision(10) << x; // Prints: 3.1415926536
    ```
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    int n, l;
    cin >> n >> l;
    
    vector<int> a(n);
    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }
    
    sort(a.begin(), a.end());
    
    int max_dist = 0;
    for (int i = 1; i < n; i++) {
        max_dist = max(max_dist, a[i] - a[i - 1]);
    }
    
    double radius = max_dist / 2.0;
    
    radius = max(radius, (double)a[0]);
    
    radius = max(radius, (double)(l - a[n - 1]));
    
    cout << fixed << setprecision(10) << radius << endl;
    
    return 0;
}
``` 

122A Lucky Division (math/brute, 1000) https://codeforces.com/problemset/problem/122/A​

**LOGIC**
  - *simple maths*
```cpp
#include <bits/stdc++.h>
using namespace std;

bool isLucky(int n) 
{
    while (n) 
    {
        if (n % 10 != 4 && n % 10 != 7) 
            return false;
        n /= 10;
    }
    return true;
}
int main() 
{
    int a;
    cin >> a;
    bool k = false;
    //to check if its absolutly lucky number

    if(isLucky(a))
    {
        cout << "YES" << endl;
        return 0;
    }
    //to check if its lucky number

    vector<int> arr = {4, 7, 44, 47, 74, 77, 444, 447, 474, 477};
    for (int i = 0; i < arr.size(); i++) 
    {
        if (a % arr[i] == 0) 
        {
            cout << "YES" << endl;
            return 0;
        }
    }
    cout << "NO" << endl;
    return 0;
}
``` 

69A File Name (greedy/two pointers, 1000) https://codeforces.com/problemset/problem/69/A

**LOGIC**
  - *SIMPLE*
```cpp
#include <bits/stdc++.h>
using namespace std;
int main() {
    int n;
    cin >> n;
    int x = 0, y = 0, z = 0;
    for (int i = 0; i < n; i++)
    {
        int a, b, c;
        cin >> a >> b >> c;
        x += a;
        y += b;
        z += c;
    }
    if (x == 0 && y == 0 && z == 0)
        cout << "YES\n";
    else
        cout << "NO\n";
    
    return 0;
}
``` 
#### Strings, Hashing, Binary Search

**Topics**
- Basic string operations, frequency counts.
- Binary search patterns (answer search, boundary finding).
- Intro string hashing (conceptual).