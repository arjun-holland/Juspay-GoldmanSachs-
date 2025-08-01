# Problem
<img width="671" height="756" alt="image" src="https://github.com/user-attachments/assets/89d07da0-f912-4699-981a-d84b42294b04" />
<img width="665" height="543" alt="image" src="https://github.com/user-attachments/assets/b173ac83-e11d-4487-936c-9cb7706f005c" />
<img width="674" height="737" alt="image" src="https://github.com/user-attachments/assets/71bf6840-ff2b-4ad1-a7d0-06a88bdd667a" />
<img width="660" height="544" alt="image" src="https://github.com/user-attachments/assets/d1f06c86-bb9c-4a9d-b673-ac214f76a20c" />


# code
```
#include <iostream>
#include <vector>
#include <string>
#include <unordered_map>
using namespace std;

string patternHelper(string pattern){
    unordered_map<char,int> mp;
    string pn = "";
    int n = 1;
    for(char c : pattern){
        if(mp.find(c) != mp.end()){
            pn += (mp[c]-'0');
        }else{
            mp[c] = n;
            pn += n-'0';
            n++;
        }
    }
    return pn;
}


pair<int, vector<string>> find_and_replace_pattern(vector<string>& words, const string& pattern) {
    // Write your logic here.
    string pn = patternHelper(pattern);
    int r = 0;
    vector<string> vt;
    for(auto w : words){
        string cn = patternHelper(w);
        if(cn == pn){
            vt.push_back(w);
            r++;
        }
    }
    return {r,vt};
}

int main() {
    int n;
    cin >> n;
    vector<string> words(n);
    for (int i = 0; i < n; ++i) {
        cin >> words[i];
    }
    string pattern;
    cin >> pattern;
    
    auto result = find_and_replace_pattern(words, pattern);
    int matched_count = result.first;
    vector<string> matched_words = result.second;
    
    cout << matched_count << endl;
    if (matched_count > 0) {
        for (const auto& word : matched_words) {
            cout << word << " ";
        }
        cout << endl;
    }
    return 0;
}
```
