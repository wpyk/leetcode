# 82.Remove Duplicates from Sorted List II       
## Description    
   Given a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list.  
   输入为一个单向链表，要求删除其中所有出现超过一次的数字，将其余数字用单向列表的方式输出。
## Example   
  Input: 1->2->3->3->4->4->5             
  Output: 1->2->5

### Note/思路/考え方    
   One thing should be noted here is that "duplicate" here only means value of node next to each other. For example, if the input is 1->2->2->3->2, the output will be 1->3->2, only the two 2 in sequence will be deleted, not the last one.    
   新建一个ListNode current，使其指向head。当current.next 和 current.next.next 值相等的时候，记录下这个值i，并使current.next 指向current.next.next。直到 current.next 的值不再等于i, 将current后移一位。 在这个过程中， 由于current 一直在移动，并且head可能出现会被删除的可能，需要在一开始的时候建立一个ListNode，使其指向head，作为最终返回的结果。

```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if (head == null || head.next == null){
            return head;
        }
        
        ListNode current = new ListNode(0);
        current.next = head;
        ListNode result = current;
        
        while(current.next != null && current.next.next != null){
            if(current.next.val == current.next.next.val){
                int i = current.next.val;
                while(current.next != null && current.next.val == i){
                current.next = current.next.next;
                }
            }else{
                current = current.next;
            }  
        }
        
        return result.next;
    }
}
```
