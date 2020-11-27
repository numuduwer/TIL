# 연결리스트 

### 추상적 자료구조 
자료구조의 내부구조를 숨겨두고(추상적) 두가지(데이터,연산)를 밖에서 보여주는 자료구조를 말한다.  
1. Data (정수, 문자열 ...)
2. A set of opertations (삽입,삭제,정렬,탐색 ...)




## 연결리스트 
앞에 있는 노드들이 뒤에았는 노드를 가리키고 있는 자료구조를 연결리스트라 한다. 

### 노드
노드는 LinkedList에서 사용하는 item의 자료구조이며 2가지로 이루어져 있다. 
1. data
2. 다음노드를 가리키는 Link(next)

~~~python
    class Node:
        def __init__(self, item):
                self.data = item
                self.next = None
~~~


### LinkedList 
Linkedlist의 구조는 3가지로 이루어져 있다.    
1. 첫 노드를 가리키는 head 
2. 마지막 노드를 가리키는 tail
3. 노드의 수를 가리키는 nodeCount

~~~python
    class LinkedList:
        def __init__(self):
            self.nodeCount = 0
            self.head = None
            self.tail = None 
~~~

### Linked List의 연산들 6가지 
1. 특정 원소를 참조 (k번째)
2. 리스트 순회 
3. 길이 얻어내기 
4. 노드 삽입
5. 노드 삭제 
6. 리스트 합치기 


#### 1. 특정 원소 참조 (k번째)
~~~python
    class LinkedList:
        def getAt(self, pos):
            if pos <1 or pos > self.nodeCount:
                return None
            i = 1
            curr = self.head
            while i < pos:
                curr = curr.next
                i += 1
            return curr
~~~

#### 2. 리스트 순회 
~~~python
    class LinkedList:
        def traverse(self):
            if self.nodeCount == 0:
                return []
            answer = [] 
            curr = self.head

            while curr != None:
                answer.append(curr.data)
                curr = curr.next
            return answer
~~~

#### 3. 리스트 길이얻어내기 
~~~python
    class LinkedList:
        def length(self):
            return self.nodeCount
~~~

#### 4. 노드의 삽입 
이 순서로 만들자. 
- pos가 가리키는 위치에 (1 <== pos <= nodeCount +1)
- newNode를 삽입하고 
    - (pos-1)번째 노드를 prev라 부르고 
    - newNode의 next는 prev.next를 가리키게 
    - prev의 next는 newNode를 가리키게 
    - nodeCount += 1
- 성공/실패에 따라 True/False 리턴 

주의할 점.
- pos(몇번째인지 가리키는 놈)이 linked 리스트 범위를 벗어날 때
- 삽입하려는 노드가 맨 앞일 때
- 삽입하려는 노드가 맨 뒤일 떄
~~~python
    class LinkedList:
        def insertAt(self, pos, newNode):
            if pos < 1 or pos > self.nodeCount +1:
                return False
            # 삽입하려는 위치가 리스트 맨 앞일 때
            if pos == 1:
                # -> prev 없음 , Head 조정 필요
                newNode.next = self.head
                self.head = newNode
            else:
                #삽입하려는 위치가 리스트 맨 끝일 때 
                
                if pos == self.nodeCount +1:
                    prev = self.tail
                else:
                    prev = self.getAt(pos-1)
                    newNode.next = prev.next
                    prev.next = newNode
            if pos == self.nodeCount +1:
                self.tail = newNode

            self.nodeCount += 1 
            return True
~~~


#### 5. 노드의 삭제
이 순서로 만들자. 
- pos가 가리키는 위치의 (1<=pos <= nodeCount) 
- 노드를 삭제하고  
    - prev.next는 curr.next를 가리키게
    - nodeCount -= 1
- 그 노드의 데이터를 리턴

주의할 점 
- pos가 올바른 범위의 값을 가지지 않는 경우
- 삭제하는 노드가 맨 앞일 때
    - nodeCount가 1개인 LinkedList일 때
    - 2개이상의 노드를 가진 LinkedLust일 때
- 삭제하는 노드가 맨 뒤일 때
- 삭제하려는 노드가 중간일 때 

~~~python
    def popAt(self, pos):
        if pos < 1 or pos > self.nodeCount:  # pos 가 올바른 범위의 값을 가지지 않는 경우
            raise IndexError

        curr = self.getAt(pos)

        if pos == 1:  # 삭제하려는 노드가 맨 앞일 때
            if self.nodeCount == 1:  # 유일한 노드를 삭제할 때
                self.head = None
                self.tail = None
            else:
                self.head = self.getAt(pos + 1)
        elif pos == self.nodeCount:  # 삭제하려는 노드가 맨 뒤의 것일 때
            prev = self.getAt(pos - 1)
            prev.next = None
            self.tail = prev
        else:  # 삭제하려는 노드가 중간일때
            prev = self.getAt(pos - 1)
            prev.next = curr.next


        self.nodeCount -= 1
        return curr.data
~~~

#### 6. 두 리스트의 연결 

주의할 점 
- 뒤에 붙일 리스트(L)이 빈거라면?? 



생각할 점 
- pos(몇번째인지 가리키는 놈)이 linked 리스트 범위를 벗어날 때
- 삭제하려는 노드가 맨 앞일 때
    - prev 없음, head조정 필요
- 삭제하려는 노드가 맨 뒤일 떄

~~~python
    def count(self,L):
        self.tail.next = L.head
        if L.tail:
            self.tail = L.tail
        self.nodeCount += L.nodeCount
~~~
### 장점 
- 삽입과 삭제를 유연하게 할 수있다. 
- 리스트 간 병합하는 문제도 쉽게 할 수 있다. 


### 단점 
- 

### 배열 vs Linked List
|       | Array   |Linked List              |
|---    |------   |-------------------------|
|저장 공간| 연속한 위치| 임의의 위치                |
|특정 원소를 지칭할 때 | 매우 간편| 선형탐색과 유사하다.|
|       | O(1)    | O(n)                    |

