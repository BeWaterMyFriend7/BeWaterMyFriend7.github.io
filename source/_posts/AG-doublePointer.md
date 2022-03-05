---
title: 双指针&链表
top: false
cover: false
toc: true
mathjax: true
tags:
  - 算法
  - 找工作
categories: 刷题笔记
typora-root-url: AG-doublePointer
abbrlink: 552
date: 2022-03-02 16:33:49
password:
summary:
---

## [206. 反转链表](https://leetcode-cn.com/problems/reverse-linked-list/)

![img](1645971484076-c26dec60-ae41-4a8d-a968-accbb4563304.png)



### 基本思路

反转链表，仅仅需要扭转链表的指向顺序即可，如果用双指针实现的话，一个快指针，一个慢指针指向相邻的两个结点，并将结点的指向顺序改变即可。



思考一些细节问题，在扭转之前，我们需要一个空指针作为扭转后的尾部。



好，看代码



```cpp
    ListNode* reverseList(ListNode* head) {
		ListNode* p0 = nullptr;
        ListNode* p1 = head;
        while(p1 != nullptr){
        	ListNode* p2 = p1->next;  
            p1->next = p0;
            p0 = p1;
            p1 = p2;
        }
        
        return p0;
    }
```

有几个点需要注意：

- p0 作为 左指针， p1作为右指针
- line6 首先要记录下p1的下一个指针，因为反转之后就变了

- line8 一定要在line9之前

### 完整代码

```cpp
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
		ListNode* p0 = nullptr;
        ListNode* p1 = head;
        while(p1 != nullptr){
        	ListNode* p2 = p1->next;  
            p1->next = p0;
            p0 = p1;
            p1 = p2;
        }
        
        return p0;
    }
};
```

## [19. 删除链表的倒数第 N 个结点](https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/)



![img](1645954811592-dbacf012-5d2b-48ba-838d-064cc1b87c71.png)



### 基本思路：

常规思路是先求出链表的长度，然后找到删去的结点删除，但要进行两次遍历。



如何才能够通过一次遍历实现呢？双指针中的快慢指针，让两个指针差n个单位，就可以找出要删除的结点进行删除。



那很容易想到应该写如下代码

```cpp
ListNode* ptr1 = head;
for(int i = 0;i<n;i++){
 	ptr1 = ptr1->next;
}

ListNode* ptr2 = head;
while(ptr1 != nullptr){
    ptr1 = ptr1->next;
    ptr2 = ptr2->next;
}
```

我们思考上述代码会出现怎样的问题，我们只思考指针ptr2的起始位置即可。

以官方第一个例子为例



**输入：**head = [1,2,3,4,5], n = 2 

**输出：**[1,2,3,5]



ptr2指向第一个结点的时候，ptr1指向第三个结点，那么当ptr1指向nullptr时，ptr2 刚好指向倒数第2个结点。



这样我们就无法删除该结点，因此我们需要ptr2指向倒数第3个结点，那很好解决，直接让ptr1多走一个即可。



但还会出现问题，如果链表只有一个结点，并且n=1，那么代码2-4行就会报错。那么怎么解决呢？既然ptr1不能多往后移动，那么我们可以让ptr2多往前移动。（注：当然可以将特殊情况摘出，但算法追求的更是一种通用解法）那么我们就需要在head前添加一个哑结点。



即

```cpp
ListNode* ptr1 = head;
for(int i = 0;i<n;i++){
 	ptr1 = ptr1->next;
}

ListNode* dummy = new ListNode(0,head);
ListNode* ptr2 = dummy;
while(ptr1 != nullptr){
    ptr1 = ptr1->next;
    ptr2 = ptr2->next;
}
```



### 完整代码



```cpp
class Solution {
public:
    ListNode* deleteNodenList(ListNode* head, int n) {
		ListNode* ptr1 = head;
        for(int i = 0;i<n;i++){
            ptr1 = ptr1->next;
        }

        ListNode* dummy = new ListNode(0,head);
        ListNode* ptr2 = dummy;
        while(ptr1 != nullptr){
            ptr1 = ptr1->next;
            ptr2 = ptr2->next;
        }

        ptr2->next = ptr2->next->next;
        return dummy->next;
    }
};
```
