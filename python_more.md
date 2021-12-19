1. Python Common **Data Structure** for leet code:

https://www.evernote.com/shard/s721/client/snv?noteGuid=9497c08a-5ab5-43d8-a5ff-0d59288756bd&noteKey=45b5ca532c9bdcfcbe3dcbadb8339022&sn=https%3A%2F%2Fwww.evernote.com%2Fshard%2Fs721%2Fsh%2F9497c08a-5ab5-43d8-a5ff-0d59288756bd%2F45b5ca532c9bdcfcbe3dcbadb8339022&title=Python%2BCommon%2BData%2BStructure





2. **Linked List:**

**Dummy Node**
 
Dummy node 是链表问题中一个重要的技巧，中文翻译叫“哑节点”或者“假人头结点”。

Dummy node 是一个虚拟节点，也可以认为是标杆节点。Dummy node 就是在链表表头 head 前加一个节点指向 head，即 dummy -> head。Dummy node 的使用多针对单链表没有前向指针的问题，保证链表的 head 不会在删除操作中丢失。除此之外，还有一种用法比较少见，就是使用 dummy node 来进行head的删除操作，比如 Remove Duplicates From Sorted List II，一般的方法current = current.next 是无法删除 head 元素的，所以这个时候如果有一个dummy node在head的前面。

所以，当链表的 head 有可能变化（被修改或者被删除）时，使用 dummy node 可以很好的简化代码，最终返回 dummy.next 即新的链表。

**快慢指针**
 
快慢指针也是一个可以用于很多问题的技巧。所谓快慢指针中的快慢指的是指针向前移动的步长，每次移动的步长较大即为快，步长较小即为慢，常用的快慢指针一般是在单链表中让快指针每次向前移动2，慢指针则每次向前移动1。快慢两个指针都从链表头开始遍历，于是快指针到达链表末尾的时候慢指针刚好到达中间位置，于是可以得到中间元素的值。快慢指针在链表相关问题中主要有两个应用：

快速找出未知长度单链表的中间节点 设置两个指针 *fast、*slow 都指向单链表的头节点，其中*fast的移动速度是*slow的2倍，当*fast指向末尾节点的时候，slow正好就在中间了。
判断单链表是否有环 利用快慢指针的原理，同样设置两个指针 *fast、*slow 都指向单链表的头节点，其中 *fast的移动速度是*slow的2倍。如果 *fast = NULL，说明该单链表 以 NULL结尾，不是循环链表；如果 *fast = *slow，则快指针追上慢指针，说明该链表是循环链表。
