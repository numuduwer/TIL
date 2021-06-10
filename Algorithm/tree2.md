# Binary Heap  / Graph

# Heap

### Heap이란?

완전 이진트리를  기본으로한 자료구조 

최대값과 최소값을 빠르게 찾기 위한 자료 구조 

### Heap에 노드 삽입 하기

작업

1. 마지막 레벨의 왼쪽부터 삽입한다.
2. 자신의 부모노드와 비교해서 정렬한다. (root도착할때까지)
3. 시간복잡도는 O(logN)

### Heap에 노드 값 가져오기

작업

1. Root의 값을 가져오기 
2. 마지막 노드를 가져와서 Root에 넣기
3. 자신의 자식노드와 비교해서 정렬한다. 
4. 복잡도는 O(logN)

### 최대인지 최소인지는  정렬작업 반대로 하면 된다.

# Graph

Tree의 상위호환

선의 방향이 자유로운 트리라고 생각하자. 

### Geapth를 검색하는 방법

**종류**

1. Depth - First - Search(DFS)
2. Breadth- First - Search(BFS)

### DFS 와 BFS 검색 순서의 차이점
![Untitled](https://user-images.githubusercontent.com/33523029/121485257-fbec8e80-ca0a-11eb-8837-34214f6d5276.png)
### DFS

- Inorder , preorder , postorder 순회방식이 이 DFS 방식이다.
- Stack을 이용해서 만들 수 있다.
- 재귀로도 만들 수 있어용

### BFS

- level단위로 담색하는 방법이다
- Queue를 이용해서 만들 수 있다.

### 코드

1. DFS , BFS , DFS (Recursive)
2. BFS에 사용하는 Queue는 직접 구현하였다. 

```java
package me.whiteship.interview._00_intro;

import java.util.LinkedList;
import java.util.NoSuchElementException;
import java.util.Stack;

class Queue<T>{
    class Node<T> {
        private T data;
        private Node<T> next;

        public Node(T data){
            this.data = data;
        }
    }
    private Node<T> first;
    private Node<T> last;

    public void add(T item){
        Node<T> t = new Node<T>(item);

        if(last != null){
            last.next = t;
        }
        last =t;
        if(first == null){
            first = last;
        }
    }

    public  T remove(){
        if(first == null){
            throw new NoSuchElementException();
        }
        T data = first.data;
        first = first.next;

        if(first == null){
            last = null;
        }

        return data;
    }

    public T peek(){
        if(first == null){
            throw new NoSuchElementException();
        }
        return first.data;
    }

    public boolean isEmpty(){
        return first ==null;
    }

}

class Graph {
    class Node{
        int data;
        LinkedList<Node> adjacent;
        boolean marked;

        Node(int data){
            this.data =data;
            this.marked = false;
            adjacent = new LinkedList<Node>();
        }
    }

    // 2. 그래프에는 노드들을 저장할 배열이 필요하다.
    Node[] nodes;

    // 3. size를 받아서 배열 방을 만들어 준다.(편의를 위해 값은 그냥 index)
    Graph(int size){
        nodes = new Node[size];
        for (int i = 0; i < size; i++) {
            nodes[i] = new Node(i);
        }
    }
    // 4. 두 노드의 관계를 저장하는 함수 addEdge
    void addEdge(int i1, int i2){
        Node n1 = nodes[i1];
        Node n2 = nodes[i2];

        // 서로 인접한 곳에 있는지 확인하고 없으면 넣어준다.
        if(!n1.adjacent.contains(n2)){
            n1.adjacent.add(n2);
        }

        if(!n2.adjacent.contains(n1)){
            n2.adjacent.add(n1);
        }
    }
    // 5. DFS 호출하면 0번부터 호출하게 세팅
    void dfs(){
        dfs(0);
    }

    void dfs(int index){
        // 해당 index로 node를 가져오고
        Node root = nodes[index];

        // stack을 만들어 node를 넣는다.
        Stack<Node> stack = new Stack<Node>();
        stack.push(root);
        root.marked = true;

        while(!stack.isEmpty()){
            Node r = stack.pop();
            for (Node n : r.adjacent) {
                if(n.marked == false){
                    n.marked = true;
                    stack.push(n);
                }
            }
            visit(r);
        }
    }
    // 6. BFS 호출하면 0번부터 호출하게 세팅
    void bfs(){
        bfs(0);
    }

    void bfs(int index){
        // 해당 index로 node를 가져오고
        Node root = nodes[index];

        // Queue를 만들어 node를 넣는다.
        Queue<Node> queue = new Queue<Node>();
        queue.add(root);
        root.marked = true;

        while(!queue.isEmpty()){
            Node r = queue.remove();
            for(Node n : r.adjacent){
                if(n.marked == false){
                    n.marked = true;
                    queue.add(n);
                }
            }
            visit(r);
        }
    }

    //7. 재귀 호출 DFS
    void dfsR(Node r){
        if(r == null) return;
        r.marked = true;
        visit(r);
        for(Node n : r.adjacent){
            if(n.marked == false){
                dfsR(n);
            }
        }
    }

    // 8.시작노드를 다양하게 해보기 위한  재귀 DFS 세팅
    void dfsR(int index){
        Node r = nodes[index];
        dfsR(r);
    }
    // 9. 아무것도 넣지 않으면 0부터 시작
    void dfsR(){
        dfsR(0);
    }

    void visit(Node n){
        System.out.println(n.data + " ");
    }
}

/*
*  ------------ 출력 예상
* DFS(0)
* 0 1 3 5 7 6 8 4 2
* BFS(0)
* 0 1 2 3 4 5 6 7 8
* DFS(0) Recursive
* 0 1 2 4 3 5 6 8 7
*
* DFS(3)
* 3 5 7 6 8 4 2 1 0
* BFS(3)
* 3 1 2 4 5 0 6 7 8
* DFS(3) Recursive
* 3 1 0 2 4 5 6 8 7
*
*/
public class test2 {
    public static void main(String[] args) {
        Graph g = new Graph(9);
        g.addEdge(0,1);
        g.addEdge(1,2);
        g.addEdge(1,3);
        g.addEdge(2,4);
        g.addEdge(2,3);
        g.addEdge(3,4);
        g.addEdge(3,5);
        g.addEdge(5,6);
        g.addEdge(5,7);
        g.addEdge(6,8);

        g.dfs();

    }
}
```
