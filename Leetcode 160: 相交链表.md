我们可以使用两次迭代来做到这一点。在第一个迭代中，我们将一个链表的指针重置到另一个链表的末尾后再指向其头。在第二个迭代中，我们将移动两个指针，直到它们指向同一节点。我们在第一次迭代中的操作将帮助我们抵消差异。因此，如果两个链表相交，则第二个迭代中的交点必须是交点。如果两个链接列表根本没有交集，则第二次迭代中的会议指针必须是两个列表的尾节点，为空。      
We can use two iterations to do that. In the first iteration, we will reset the pointer of one linkedlist to the head of another linkedlist after it reaches the tail node. In the second iteration, we will move two pointers until they points to the same node. Our operations in first iteration will help us counteract the difference. So if two linkedlist intersects, the meeting point in second iteration must be the intersection point. If the two linked lists have no intersection at all, then the meeting pointer in second iteration must be the tail node of both lists, which is null.
```java
public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
    //boundary check
    if(headA == null || headB == null) return null;
    
    ListNode a = headA;
    ListNode b = headB;
    
    //if a & b have different len, then we will stop the loop after second iteration
    while( a != b){
    	//for the end of first iteration, we just reset the pointer to the head of another linkedlist
        a = a == null? headB : a.next;
        b = b == null? headA : b.next;    
    }
    
    return a;
}

```
