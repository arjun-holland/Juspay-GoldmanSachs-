# Problem
<img width="522" height="521" alt="image" src="https://github.com/user-attachments/assets/8bfc8909-9dc5-4707-a347-49d6438b22b6" />

# Ituition
## Brute Force
<img width="696" height="327" alt="image" src="https://github.com/user-attachments/assets/6032c0c7-f53c-4035-978f-0295ccdf3771" />

```
#include <bits/stdc++.h>
using namespace std;

int main() {
    int N, X;
    cin >> N >> X;
    vector<int> A(N);
    for (int i = 0; i < N; i++) cin >> A[i];

    long long count = 0;

    // Check all subsegments
    for (int i = 0; i < N; i++) {
        int C = 0;
        for (int j = i; j < N; j++) {
            C += A[j];
            if (C > X) C = 0;    // reset when exceeding X
        }
        if (C != 0) count++;
    }

    cout << count << endl;
    return 0;
}

```
