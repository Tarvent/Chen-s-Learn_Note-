# Leetcode

---

# 2.Add Two Numbers

## 题目描述

难度 中等

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

## 题解

```java
/**

* Definition for singly-linked list.

* public class ListNode {

* int val;

* ListNode next;

* ListNode() {}

* ListNode(int val) { this.val = val; }

* ListNode(int val, ListNode next) { this.val = val; this.next = next; }

* }

*/

class Solution {

public ListNode addTwoNumbers(ListNode l1, ListNode l2) {

ListNode pre = new ListNode(0);

ListNode cur = pre;

int carry = 0;

while(l1 != null || l2 != null){

	int x = l1 == null ? 0 : l1.val;

	int y = l2 == null ? 0 : l2.val;

	int sum = x + y + carry;
	
	  
	
	carry = sum / 10 ;
	
	sum = sum % 10;
	
	cur.next = new ListNode(sum);
	
	  
	
	cur = cur.next;
	
	if(l1 != null)
	
	l1 = l1.next;
	
	if(l2 != null)
	
	l2 = l2.next;

}

if(carry == 1){

	cur.next = new ListNode(carry);

}

return pre.next;

  

}

}
```



# 6. Z字形变换

The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)
```
P   A   H   N
A P L S I I G
Y   I   R
```
And then read line by line: "PAHNAPLSIIGYIR"

Write the code that will take a string and make this conversion given a number of rows:

string convert(string s, int numRows);

```
Example 1:

Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"

Example 2:

Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"
Explanation:
P     I    N
A   L S  I G
Y A   H R
P     I


Example 3:

Input: s = "A", numRows = 1
Output: "A"

```

## 题解

```java

class Solution {

public String convert(String s, int numRows) {

if(numRows == 1)

return s;

  

int len = Math.min(s.length(),numRows);

String []rows = new String[len];

for(int i = 0; i < len; i++) rows[i] = "";

int loc = 0;

boolean down = false;

  

for(int i = 0; i < s.length();i++){

	rows[loc] += s.substring(i, i+1);

	if(loc == 0 || loc == numRows - 1){

		down = !down; //如果是0 就加1，到numrows-1 就减1 实现z字形模拟

	}

	loc += down ? 1 : -1;// if(down){loc=loc+1} else loc=loc-1;



}

String ans = "";

for(String row : rows){

	ans = ans + row;

}

return ans;

}



```

# 27 移除元素

给你一个数组 nums 和一个值 val，你需要 原地 移除所有数值等于 val 的元素，并返回移除后数组的新长度。

不要使用额外的数组空间，你必须仅使用 O(1) 额外空间并**原地**修改输入数组。

元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。

示例 1: 给定 nums = [3,2,2,3], val = 3, 函数应该返回新的长度 2, 并且 nums 中的前两个元素均为 2。 你不需要考虑数组中超出新长度后面的元素。

示例 2: 给定 nums = [0,1,2,2,3,0,4,2], val = 2, 函数应该返回新的长度 5, 并且 nums 中的前五个元素为 0, 1, 3, 0, 4。

**你不需要考虑数组中超出新长度后面的元素。**