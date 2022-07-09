## 题意
#### 给定n个筹码的位置，筹码位置往前或往后移动2个位置，代价为0；往前或往后移动1个位置，代价为1。现求将所有筹码移到同一个位置，所需的最小代价。
---
## 题解
#### 本质就是一个筹码位置到另一个筹码位置距离如果是奇数，代价为1，否则代价为0。

#### c++代码
```c++
class Solution {
public:
    int minCostToMoveChips(vector<int>& position) {
        int cost = 100;
        for (int i = 0; i < position.size(); i++) {
            int sum = 0;
            for (int j = 0; j < position.size(); j++) {
                if (abs(position[i] - position[j]) % 2) sum++;
            }
            cost = min(cost, sum);
        }
        return cost;
    }
};
```
#### java代码
```java
class Solution {
    public int minCostToMoveChips(int[] position) {
        int cost = 100;
        for (int i = 0; i < position.length; i++) {
            int sum = 0;
            for (int j = 0; j < position.length; j++) {
                if (Math.abs(position[i] - position[j]) % 2 == 1) sum++;
            }
            cost = Math.min(cost, sum);
        }
        return cost;
    }
}
```
#### python3代码
```python
class Solution:
    def minCostToMoveChips(self, position: List[int]) -> int:
        cost = 100
        for x in position:
            sum = 0
            for y in position:
                if abs(x - y) % 2: sum = sum + 1
            cost = min(cost, sum)
        return cost
```