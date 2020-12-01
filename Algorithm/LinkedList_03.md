# 양뱡향 연결리스트 


## Node의 구조 확장 
~~~python
class Node:
    def __init__(self,item):
        self.data = item
        # 양방향에서는 prev가 추가된다. 
        self.prev = None
        self.next = None

~~~

## 양방향 연결리스트 
### 편의를 위한 dummy node를 맨 앞, 맨 끝에 두자. 
~~~python
    class DoublyLinkedList:
        def __init__(self,item):
            self.nodeCount =0
            # 양쪽에 더미노드를 적용한 코드 
            self.head = Node
            self.tail = Node
            self.head.prev = None
            self.head.next =self.tail
            self.tail.prev = self.head
            self.tail.next = None
~~~

### 연산 

### 1. 리스트 순회 
~~~python
def traverse(self):
    result = []
    curr = self.head
    while curr.next.next:
        curr = curr.next
        result.append(curr.data)
    return sesult
~~~

### 리스트 역순회 
~~~python(self):
    def reverse(self):
        result =[]
        curr = self.tail
        while curr.prev.prev:
            curr =curr.prev
            result.append(curr.data)
        return result
~~~

### 2. 삽입 
~~~python
    def insertAfter(self,prev,newNode):
        next = prev.next 
        newNode.prev = prev
        newNode.tail = next
        prev.next = newNode
        next.prev = newNode
        self.nodeCount += 1
        return True


     def insertBefore(self, next, newNode):
        prev = next.prev
        next.prev = newNode
        prev.next = newNode
        newNode.next = next
        newNode.prev = prev
        self.nodeCount += 1
        return True
~~~

### 3. 특정 원소 얻어내기 
~~~python
    def getAt(self pos):
        if pos < 0 or pos > self.nodeCount:
            return None
        if pos > self.nodeCount //2:
            i = 0
            curr = self.tail
            while i<self.nodeCount - pos +1 :
                curr = curr.prev
                i +=1
        else:
            i =0 
            curr = self.headd
            while i<pos:
                curr = curr.next
                i += 1
        return curr
~~~


### 4. 삭제 

~~~ python 
 def popAfter(self, prev):
        curr = prev.next
        data = curr.data
        prev.next = curr.next
        curr.next.prev = prev
        curr = None
        self.nodeCount -= 1
        return data



    def popBefore(self, next):
        curr = next.prev
        data = curr.data
        next.prev = curr.prev
        curr.prev.next = next

        curr = None
        self.nodeCount -= 1
        return data
   
    def popAt(self, pos):
        if pos < 0 or pos > self.nodeCount:
            raise IndexError

        pos = self.getAt(pos - 1)
        return self.popAfter(pos)

~~~