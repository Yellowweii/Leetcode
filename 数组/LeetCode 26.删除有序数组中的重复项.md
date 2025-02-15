### 题目描述：
给你一个非严格递增排列的数组 nums ，请你原地删除重复出现的元素，使每个元素只出现一次 ，返回删除后数组的新长度。元素的相对顺序 应该保持一致。然后返回 nums 中唯一元素的个数。<br>
考虑 nums 的唯一元素的数量为 k ，你需要做以下事情确保你的题解可以被通过：<br>
更改数组 nums ，使 nums 的前 k 个元素包含唯一元素，并按照它们最初在 nums 中出现的顺序排列。nums 的其余元素与 nums 的大小不重要。<br>
返回 k。<br>
判题标准:<br>
系统会用下面的代码来测试你的题解:

```c++
int[] nums = [...]; // 输入数组
int[] expectedNums = [...]; // 长度正确的期望答案
int k = removeDuplicates(nums); // 调用
assert k == expectedNums.length;
for (int i = 0; i < k; i++) {
    assert nums[i] == expectedNums[i];
}
```
如果所有断言都通过，那么您的题解将被通过。

示例 1：<br>
输入：nums = [1,1,2]<br>
输出：2, nums = [1,2,_]<br>
解释：函数应该返回新的长度 2 ，并且原数组 nums 的前两个元素被修改为 1, 2 。不需要考虑数组中超出新长度后面的元素。

示例 2：<br>
输入：nums = [0,0,1,1,1,2,2,3,3,4]<br>
输出：5, nums = [0,1,2,3,4]<br>
解释：函数应该返回新的长度 5，并且原数组 nums 的前五个元素被修改为 0, 1, 2, 3, 4 。不需要考虑数组中超出新长度后面的元素。

提示：<br>
1 <= nums.length <= 3 \* 104<br>
-10^4 <= nums[i] <= 10^4<br>
nums 已按非严格递增排列

### 题解：
```c++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
       int n = nums.size();
       int fast = 1;
       int slow = 1;
       while(fast < n){
        if(nums[fast] != nums[fast - 1]){
            nums[slow] = nums[fast];
            slow++;
        }
        fast++;
       }
       return slow;
    }
};
```
