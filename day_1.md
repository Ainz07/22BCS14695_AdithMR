# Adith M.R. - C++ Solutions to Assignment 1

UID: 22BCS14695  
LeetCode Profile Link: [Adith M.R.](https://leetcode.com/u/_eye_/)

# Arrays Problems

## 1. Remove duplicates from a sorted array  
**Link:** [Remove duplicates from a sorted array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)  
**Solution:**  
```cpp
int removeDuplicates(vector<int>& nums){
    int n=nums.size();
    if(n==0){
        return 0;
    }
    int sz=1;
    for(int i=0;i<n;i++){
        if(nums[i]!=nums[sz-1]){
            sz++;
            nums[sz-1]=nums[i];
        }
    }
    return sz;
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 2. Implementing insertion sort  
**Link:** [Insertion Sort](https://www.geeksforgeeks.org/problems/insertion-sort/1)  
**Solution:**  
```cpp
void insertionSort(vector<int>& arr) {
    for(int i=1;i<arr.size();i++){
        int key=arr[i];
        int j=i-1;
        while(j>=0 && arr[j]>key){
            arr[j+1]=arr[j];
            j--;
        }
        arr[j+1]=key;
    }
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 3. Contains duplicate  
**Link:** [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/description/)  
**Solution:**  
```cpp
bool containsDuplicate(vector<int>& nums) {
    sort(nums.begin(),nums.end());
    for(int i=1;i<nums.size();i++){
        if(nums[i]==nums[i-1]){
            return true;
        }
    }
    return false;
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 4. Two Sum
**Link:** [Two Sum](https://leetcode.com/problems/two-sum/description/)  
**Solution:**  
```cpp
vector<int> twoSum(vector<int>& arr, int target) {
    int n=arr.size();
    vector<int>ans;
    unordered_map<int,int>mp;
    for(int i=0;i<n;i++){
        int sum=target-arr[i];
        if(mp.find(sum)!=mp.end()){
            ans.push_back(mp[sum]);
            ans.push_back(i);
        }
        mp[arr[i]]=i;
    }
    return ans;
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 5. Jump Game
**Link:** [Jump Game](https://leetcode.com/problems/jump-game/description/)  
**Solution:**  
```cpp
bool canJump(vector<int>& nums) {
    int n=nums.size();
    int maxreach=0;
    for(int i=0;i<n;i++){
        if(i>maxreach){
            return false;
        }
        maxreach=max(maxreach,nums[i]+i);
    }
    return true;
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 6. Majority Element  
**Link:** [ Majority Element](https://leetcode.com/problems/majority-element/description/)  
**Solution:**  
```cpp
int majorityElement(vector<int>& nums) {
    unordered_map<int,int>mp;
    int count=nums.size()/2;
    for (int num:nums) {
        mp[num]++;
        if (mp[num]>count) {
            return num;
        }
    }
    return -1;
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 7. Valid Palindrome
**Link:** [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/description/)  
**Solution:**  
```cpp
bool isPalindrome(string s) {
    string res;
    for(int i = 0;i<s.length();i++){
        if(((int)s[i] > 64 && (int)s[i] < 91) || ((int)s[i] > 96 && (int)s[i] < 123) || ((int)s[i] > 47 && (int)s[i] < 58)){
            res+=tolower(s[i]);
        }
    }
    string check=res;
    reverse(res.begin(),res.end());
    cout<<res;
    if(res==check)
        return true;
    return false; 
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 8. Jump Game 2 
**Link:** [Jump Game II](https://leetcode.com/problems/jump-game-ii/description/)  
**Solution:**  
```cpp
int jump(vector<int>& nums) {
    int near = 0, far = 0,jumps = 0;
    while (far < nums.size() - 1) {
        int farthest = 0;
        for (int i = near; i <= far; i++) {
            farthest = max(farthest, i + nums[i]);
        }
        near = far + 1;
        far = farthest;
        jumps++;
    }
    return jumps;        
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 9. 3Sum 
**Link:** [3Sum](https://leetcode.com/problems/3sum/description/)  
**Solution:**  
```cpp
vector<vector<int>> threeSum(vector<int>& nums) {
    vector<vector<int>> res;
    sort(nums.begin(), nums.end());
    for (int i = 0; i < nums.size(); i++) {
        if (i > 0 && nums[i] == nums[i-1]) {
            continue;
        }
        int j = i + 1;
        int k = nums.size() - 1;
        while (j < k) {
            int total = nums[i] + nums[j] + nums[k];
            if (total > 0) {
                k--;
            } else if (total < 0) {
                j++;
            } else {
                res.push_back({nums[i], nums[j], nums[k]});
                j++;
                while (nums[j] == nums[j-1] && j < k) {
                    j++;
                }
            }
        }
    }
    return res;       
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 10. Set Matrix Zeroes  
**Link:** [ Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/description/)  
**Solution:**  
```cpp
void setZeroes(vector<vector<int>>& matrix) {
        int m=matrix.size();
        int n=matrix[0].size();
        vector<int>row(m,0);
        vector<int>col(n,0);
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(matrix[i][j]==0){
                    row[i]=1;
                    col[j]=1;
                }
            }
        }
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(row[i]==1 || col[j]==1){
                    matrix[i][j]=0;
                }
            }
        }
    }
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 11. Longest substring without repeating characters 
**Link:** [Longest substring without repeating characters ](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)  
**Solution:**  
```cpp
int lengthOfLongestSubstring(string s) {
    int left = 0;
    int maxLength = 0;
    unordered_set<char> charSet;
    for (int right = 0; right < s.length(); right++) {
        while (charSet.find(s[right]) != charSet.end()) {
            charSet.erase(s[left]);
            left++;
        }
        charSet.insert(s[right]);
        maxLength = max(maxLength, right - left + 1);
    }
    return maxLength; 
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 12. Find the Duplicate Number 
**Link:** [Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/description/)  
**Solution:**  
```cpp
int findDuplicate(vector<int>& nums) {
    unordered_map<int,int>mp;
    for(int i=0;i<nums.size();i++){
        if(mp[nums[i]]==1){
            return nums[i];
        }
        else{
            mp[nums[i]]++;
        }
    }
    return -1;
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

# Linked List Problems

## 1. Print Linked List  
**Question:** Print all elements of a linked list.  
**Link:** [Print Linked List Elements](https://www.geeksforgeeks.org/problems/print-linked-list-elements/0)  
**Solution:**  
```cpp
void printList(Node *head) {
    Node *temp = head;
    while (temp != nullptr) {
        cout << temp->data << " ";
        temp = temp->next;
    }
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 2. Remove Duplicates from a Sorted List  
**Link:** [Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list)  
**Solution:**  
```cpp
void removeDuplicates(Node* head) {
    if (head == nullptr) return;
    Node* current = head;

    while (current->next != nullptr) {
        if (current->data == current->next->data) {
            Node* temp = current->next;
            current->next = current->next->next;
            delete temp;
        } else {
            current = current->next;
        }
    }
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 3. Reverse a Linked List  
**Link:** [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)  
**Solution:**  
```cpp
ListNode* reverseList(ListNode* head) {
    if (!head) return nullptr;

    vector<int> stack;
    ListNode* temp = head;

    while (temp) {
        stack.push_back(temp->val);
        temp = temp->next;
    }

    ListNode* newHead = new ListNode(stack.back());
    ListNode* curr = newHead;
    
    for (int i = stack.size() - 2; i >= 0; --i) {
        curr->next = new ListNode(stack[i]);
        curr = curr->next;
    }

    return newHead;
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 4. Delete the Middle Node of a List  
**Link:** [Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)  
**Solution:**  
```cpp
ListNode* deleteMiddle(ListNode* head) {
    int middle = 0;
    ListNode *temp = head;

    if (head->next == nullptr) {
        return nullptr;
    }
    while (temp != nullptr) {
        temp = temp->next;
        middle++;
    }
    middle = middle / 2 - 1;
    ListNode *current = head;
    while (middle != 0) {
        current = current->next;
        middle--;
    }

    ListNode *tempNode = current->next;
    current->next = tempNode->next;
    delete tempNode;

    return head;
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 5. Merge Two Sorted Linked Lists  
**Link:** [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)  
**Solution:**  
```cpp
ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
    if (!l1) return l2;
    if (!l2) return l1;
    if (l1->val < l2->val) {
        l1->next = mergeTwoLists(l1->next, l2);
        return l1;
    } else {
        l2->next = mergeTwoLists(l1, l2->next);
        return l2;
    }
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 6. Remove Duplicates from Sorted Lists II  
**Link:** [Remove Duplicates from Sorted List II](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/)  
**Solution:**  
```cpp
ListNode* deleteDuplicates(ListNode* head) {
    ListNode dummy(0, head);
    ListNode* prev = &dummy;
    while (head) {
        if (head->next && head->val == head->next->val) {
            while (head->next && head->val == head->next->val) 
                head = head->next;
            prev->next = head->next;
        } else {
            prev = prev->next;
        }
        head = head->next;
    }
    return dummy.next;
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 7. Detect Cycle in a Linked List  
**Link:** [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)  
**Solution:**  
```cpp
bool hasCycle(ListNode* head) {
    ListNode *slow = head, *fast = head;
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
        if (slow == fast) return true;
    }
    return false;
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 8. Reverse Linked List II  
**Link:** [Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii/)  
**Solution:**  
```cpp
ListNode* reverseBetween(ListNode* head, int left, int right) {
    ListNode dummy(0, head);
    ListNode* prev = &dummy;
    for (int i = 0; i < left - 1; ++i) prev = prev->next;
    ListNode* curr = prev->next;
    for (int i = 0; i < right - left; ++i) {
        ListNode* temp = curr->next;
        curr->next = temp->next;
        temp->next = prev->next;
        prev->next = temp;
    }
    return dummy.next;
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 9. Rotate Linked List  
**Link:** [Rotate List](https://leetcode.com/problems/rotate-list/)  
**Solution:**  
```cpp
ListNode* rotateRight(ListNode* head, int k) {
    if (!head || !head->next || k == 0) return head;
    int len = 1;
    ListNode* tail = head;
    while (tail->next) {
        tail = tail->next;
        len++;
    }
    k %= len;
    if (k == 0) return head;
    tail->next = head;
    for (int i = 0; i < len - k; i++) tail = tail->next;
    head = tail->next;
    tail->next = nullptr;
    return head;
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 10. Merge k Sorted Lists  
**Link:** [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)  
**Solution:**  
```cpp
ListNode* mergeKLists(vector<ListNode*>& lists) {
    auto cmp = [](ListNode* a, ListNode* b) { return a->val > b->val; };
    priority_queue<ListNode*, vector<ListNode*>, decltype(cmp)> pq(cmp);
    for (auto l : lists) if (l) pq.push(l);
    ListNode dummy(0);
    ListNode* tail = &dummy;
    while (!pq.empty()) {
        tail->next = pq.top();
        pq.pop();
        tail = tail->next;
        if (tail->next) pq.push(tail->next);
    }
    return dummy.next;
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  

## 11. Sort a Linked List  
**Link:** [Sort List](https://leetcode.com/problems/sort-list/)  
**Solution:**  
```cpp
ListNode* merge(ListNode* l1, ListNode* l2) {
    ListNode dummy(0);
    ListNode* tail = &dummy;
    while (l1 && l2) {
        if (l1->val < l2->val) {
            tail->next = l1;
            l1 = l1->next;
        } else {
            tail->next = l2;
            l2 = l2->next;
        }
        tail = tail->next;
    }
    tail->next = l1 ? l1 : l2;
    return dummy.next;
}

ListNode* sortList(ListNode* head) {
    if (!head || !head->next) return head;
    ListNode *slow = head, *fast = head, *prev = nullptr;
    while (fast && fast->next) {
        prev = slow;
        slow = slow->next;
        fast = fast->next->next;
    }
    prev->next = nullptr;
    return merge(sortList(head), sortList(slow));
}
```
**Screenshot:**  
*(Add your screenshot here if available)*  
