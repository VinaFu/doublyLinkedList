# doublyLinkedList

https://www.geeksforgeeks.org/reverse-a-doubly-linked-list/

class Node(object):
    def __init__(self, val=None):
        self.val = val
        self.next = None
        self.prev = None

class BilateralLinklist(object):
    def __init__(self):
        self.head = None
        self.next = None
        self.size = 0

    def display(self):
        cur = self.head
        if self.head == None:
            return
        while cur:
            print(cur.val)
            cur = cur.next
        # while cur:
        #     print(cur.val)
        #     cur = cur.next

    def addTail(self,val):
        newNode = Node(val)
        cur =self.head
        if self.head == None:
            self.head = newNode
        while cur.next:
            cur = cur.next
        newNode.prev = cur
        cur.next = newNode

        self.size +=1

    def addHead(self,val):
        newNode = Node(val)
        if self.head == None:
            self.head = newNode
        else:
            self.head.prev = newNode
            newNode.next = self.head
            self.head = newNode

        self.size +=1

    def reverse(self):
        temp = None
        cur = self.head
        while cur is not None:
            temp = cur.prev
            cur.prev = cur.next
            cur.next = temp
            cur = cur.prev
       
        if temp is not None:
            self.head = temp.prev        


    myList = BilateralLinklist()
    myList.addHead(2) 
    myList.addHead(1)
    myList.addTail(3)
    myList.display()  
    myList.reverse() 
    myList.display() 
