## 题意
#### 给定一个字符串字典列表dict和字符串s，判定字符串s能否在只改变一个字符的情况下，在字典列表dict中找到
---
## 题解
#### 按照要求模拟遍历整个列表，然后计算一个每个字符串和要求字符串s之间字符不同个数。
#### c++代码
```c++
class MagicDictionary {
public:
    MagicDictionary() {

    }

    void buildDict(vector<string> dictionary) {
        words = dictionary;
    }

    bool search(string searchWord) {
        for (auto word: words) {
            if (searchWord.size() != word.size()) continue;
            int cnt = 0;
            for (int i = 0; i < word.size(); i++) {
                if (searchWord[i] != word[i]) cnt++;
                if (cnt > 1) break;
            }
            if (cnt == 1) return true;
        }
        return false;
    }
private:
    vector<string> words;
};
```