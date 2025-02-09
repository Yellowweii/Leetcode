### 题目描述：
给你一个链表，删除链表的倒数第 n 个结点，并且返回链表的头结点。

示例 1：<br>
输入：head = [1,2,3,4,5], n = 2<br>
输出：[1,2,3,5]

示例 2：<br>
输入：head = [1], n = 1<br>
输出：[]

示例 3：<br>
输入：head = [1,2], n = 1<br>
输出：[1]

提示：<br>
链表中结点的数目为 sz<br>
1 <= sz <= 30<br>
0 <= Node.val <= 100<br>
1 <= n <= sz

进阶：你能尝试使用一趟扫描实现吗？

### 题解：
#### 解法一：计算链表长度 空间复杂度 O(1)
```c++
class Solution {
public:
    int getLength(ListNode* head) {
        int length = 0;
        while(head){
            length++;
            head = head -> next;
        }
        return length;
    }

    ListNode* removeNthFromEnd(ListNode* head, int n) {
        int length = getLength(head);
        int index = 0;
        ListNode* dummy = new ListNode(0, head);
        ListNode* currentNode = dummy;
        while(index < length - n){
            currentNode = currentNode -> next;
            index++;
        }
        ListNode* toDeleteNode = currentNode -> next;
        currentNode -> next = currentNode -> next -> next;
        ListNode* ans = dummy -> next;
        delete toDeleteNode;
        delete dummy;
        return ans;
    }
};
```

#### 解法二：栈 空间复杂度 O(L)
```c++
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        stack<ListNode*> stk;
        ListNode* dummy = new ListNode(0, head);
        ListNode* currentNode = dummy;
        while(currentNode){
            stk.push(currentNode);
            currentNode = currentNode -> next;
        }
        for(int i = 0; i < n; i++){
            stk.pop();
        }
        ListNode* prev = stk.top();
        ListNode* toDeleteNode = prev -> next;
        prev -> next = prev -> next -> next;
        ListNode* ans = dummy -> next;
        delete dummy;
        delete toDeleteNode;
        return ans;
    }
};
```