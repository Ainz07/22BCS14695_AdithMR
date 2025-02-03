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

---

## 2. Remove Duplicates from a Sorted List  
**Question:** Remove duplicates from a sorted linked list.  
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

---

## 3. Reverse a Linked List  
**Question:** Reverse a linked list.  
**Link:** [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)  
**Solution:**  
```cpp
ListNode* reverseList(ListNode* head) {
    if (!head) return nullptr;

    vector<int> stack;
    ListNode* temp = head;

    // Push all values to stack
    while (temp) {
        stack.push_back(temp->val);
        temp = temp->next;
    }

    // Create a new linked list
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

---

## 4. Delete the Middle Node of a List  
**Question:** Delete the middle node of a linked list.  
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

---

## 5. Merge Two Sorted Linked Lists  
**Question:** Merge two sorted linked lists into one sorted list.  
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

---

## 6. Remove Duplicates from Sorted Lists II  
**Question:** Remove all duplicates from a sorted linked list, including the duplicates themselves.  
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

---

## 7. Detect Cycle in a Linked List  
**Question:** Detect if a linked list has a cycle.  
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

---

## 8. Reverse Linked List II  
**Question:** Reverse a portion of a linked list between two indices.  
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

---

## 9. Rotate Linked List  
**Question:** Rotate a linked list to the right by k places.  
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

---

## 10. Merge k Sorted Lists  
**Question:** Merge k sorted linked lists into one sorted list.  
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

---

## 11. Sort a Linked List  
**Question:** Sort a linked list in ascending order.  
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
```
```
