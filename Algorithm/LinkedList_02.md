# 연결리스트 02 

# 목차. 
- Linked List를 사용한 예시
- 새로운 Linked List을 만들자. 

# Linked List를 사용한 예시
- 아이폰에서 실행중인 앱 리스트 볼 때

#  새로운 Linked List을 만들자. 

1. 두가지 기능을 추가하자. 
- insertAfter(prev, newNode)
- popAfter(prev)

어떤 포지션을 순회하고 실행하는것이 아니라 어떤 노드를 주고 진행하라. 

2. 맨 앞에 dummy node를 추가한 형태로 두자. 


## 바뀐 부분 
### linkedList 자료구조 
~~~python
    class LinkedList:
        def __init__(self):
            self.nodeCount = 0
            #원래는 None, dummy node 추가한 모습.
            self.head = Node 
            self.tail = None
            # 새로 추가 
            self.head.next = self.tail
~~~
### 연산 (6가지 연산)
(1.길이얻기, 2.순회, 3.특정원소 참조, 4.삽입, 5.삭제, 6.리스트 합치기 )

- 순회 
    ~~~python
    def traverse(self):
        result = []
        curr = self.head
        # 이 while부분 바뀜 사실, 안바뀜;; 
        while curr.next:
            curr = curr.next
            result.append(curr.data)
        return result
    ~~~

- 특정 원소 참조(k번 째)
    ~~~python
     def getAt(self, pos):
            if pos<0 or pos > self.nodeCount:
                return None
            # 이전에는 i= 0 dummy를 둬서 바뀜 
            i = 0  
            curr = self.head
            while i <pos:
                currr = curr.next
                i += 1
            return curr
    ~~~


- 삽입   
insertAt에서 prev를 찾는 것으로 고치고 
prev값을 통해 삽입하는 insertAfter()를 리턴 시키게 변경
    
    ~~~python
        def insertAfter(self, prev, newNode):
            newNode.next = prev.next
            # 맨 끝에 삽입할 때 
            if prev.next is None:
                self.tail = newNode
            prev.next =newNode
            self.nodeCount += 1
            return True
    ~~~
    insertAfter()를 이용한 insertAt()    
    1. pos 범위 조건 확인
    2. pos == 1 인 경우 head뒤에 새 node 삽입
    3. pos == nodeCount +1인 경우는 prev <- tail
    4. 그렇지 않은 경우 prev <- getAt(..) 

    ~~~python
        def insertAt(self,pos, newNode):
            if pos<1 or pos> self.nodeCount +1:
                return False
            if pos != 1 and pos == self.nodeCount +1 :
                prev = self.tail
            else:
                prev = self.getAt(pos-1)
            return self.insertAfter(prev,newNode)
    ~~~
- 삭제   
L.popAfter()만들 떄 고려할 점 
1. prev가 마지막 node일 때 (prev.next == None)
    - 삭제할 node 없음 
    - return None
2. 리스트 맨 끝에 node를 삭제할 때 (curr.next ==None)
    - Tail 조정 필요

~~~python
# 삭제 처리하는 기능
    def popAfter(self, prev):
         
        curr = prev.next
        answer = curr.data
        # 1. prev()가 마지막 node일 때 (prev.next == None)
        # - 삭제할 node 없음
        # -return None
        if prev.next == None:
            return None
        # 리스트 맨 끝에 node를 삭제할 때 (curr.next == None) 
        # - Tail 조정  필요 
        if curr.next == None:
            prev.next = None
            self.tail = prev
        prev.next = curr.next
        self.nodeCount -= 1
        return answer


    def popAt(self, pos):
        if pos < 1 or pos > self.nodeCount:
            raise IndexError

        if self.nodeCount == 1:
            prev = self.head
        else:
            prev = self.getAt(pos - 1)

        return self.popAfter(prev)


~~~

- 두 리스트의 연결 

~~~python
    def concat(self,L):
        self.tail.next = L2.head.next
        if L.tail:
            self.tail = L.tail
        self.nodeCount += L.nodeCount
~~~