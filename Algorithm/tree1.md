# 트리 용어

### 트리

Linked List와 비슷하지만 노드 한개가 다른 여러 노드를 가리킨다.

![%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5%20%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%8B%E1%85%A5%2088608e0625d4402f963965e3cfc9f7b7/Untitled.png](%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5%20%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%8B%E1%85%A5%2088608e0625d4402f963965e3cfc9f7b7/Untitled.png)

 

### 트리 용어

- 루트(root) : 부모 노드
- 리프 (leaf) : 자식이 없는 노드
- 엣지(edge) :  부모 자식을 잇는 선
- 형제(siblings) : 부모가 같은 노드들
- 레벨 : A는 0 / B C는 1레벨 / D E F 는 2레벨
- 노드의 깊이 : 부모로부터 해당 노드 까지의 길이 (ex. B의 깊이는  1  / G의 깊이는  3)
- 노드의 높이 : 해당노드에서 가장 깊은 리프까지의 길이 (ex. B의 높이는 2 / C의 높이는 1)
- 트리의 깊이 : 전체 깊이 최대값
- 트리의 높이 : 전체 높이 최대값
- 노드의 크기 : 자기 자신을 포함한 그노드가 가진 자손의 수  (ex. B의 크기는 4)

### 이진트리

- 각 노드는 자식이 없거나  , 1개 or 2개의 자식을 가진다.

### 이진 탐색 트리 (BST)

- 검색용 이진트리 (Binary Search Tree)
- 노드의 자식이 최대 두개씩 붙는 트리를 이진트리라 한다.
- 탐색의 시간복잡도는  $O(logn)$ 입력 , LinkedList보다 탐색이 빠르다.
- 정렬 된 배열은 삽입 , 삭제 작업이 비효율적이다.

**만족해야할 조건**

- 어떤 노드의 서브트리 왼쪽은 노드보다 작아야함  / 오른쪽은 커야한다
- 노드의 값이 모두 달라야 한다.

### 트리 순회 방법

트리에서 데이터를 가져 오는 방법 

 

```java
    (1)
    / \
  (2)  (3)
  / \
(4) (5)

```

- 중위탐색 Inorder    ( Left, Root, Right ) : 4 2 5 1 3
- 전위탐색 Preorder  ( Root, Left, Right ) : 1 2 4 5 3
- 후위탐색 Postorder ( Left, Root, Right ) : 4 5 2 3 1

### 트리 Code

- 먼저 테스트를 위한 노드를 만들어 준다.
- 전위, 후위, 중위 탐색 기능 구현

```java
/**
 *     (1)
 *     / \
 *   (2)  (3)
 *   / \
 * (4) (5)
 - 중위탐색 Inorder    ( Left, Root, Right ) : 4 2 5 1 3
 - 전위탐색 Preorder  ( Root, Left, Right ) : 1 2 4 5 3
 - 후위탐색 Postorder ( Left, Root, Right ) : 4 5 2 3 1
을 확인하는 코드를 만들어라. 
 **/
class Node {
    int data;
    Node left;
    Node right;
}

class Tree {
    public Node root;

    public void setRoot(Node node) {
        this.root = node;
    }

    public Node getRoot() {
        return root;
    }

    public Node makeNode(Node left, int data, Node right){
        Node node = new Node();
        node.data = data;
        node.left = left;
        node.right = right;
        return node;
    }

    // 중위탐색
    public void inorder(Node node){
        if(node != null){
            inorder(node.left);
            System.out.println(node.data);
            inorder(node.right);
        }
    }

    // 전위탐색
    public void preorder(Node node){
        if(node != null){
            System.out.println(node.data);
            preorder(node.left);
            preorder(node.right);
        }
    }

    // 후위탐색
    public void postorder(Node node){
        if(node != null){
            postorder(node.left);
            postorder(node.right);
            System.out.println(node.data);
        }
    }

}

/**
 *     (1)
 *     / \
 *   (2)  (3)
 *   / \
 * (4) (5)
 - 중위탐색 Inorder    ( Left, Root, Right ) : 4 2 5 1 3
 - 전위탐색 Preorder  ( Root, Left, Right ) : 1 2 4 5 3
 - 후위탐색 Postorder ( Left, Root, Right ) : 4 5 2 3 1
 **/
public class test {
    public static void main(String[] args) {
        Tree t= new Tree();
        Node n4 = t.makeNode(null, 4, null);
        Node n5 = t.makeNode(null,5,null);
        Node n2 = t.makeNode(n4,2,n5);
        Node n3 = t.makeNode(null,3,null);
        Node n1 = t.makeNode(n2,1,n3);

        t.setRoot(n1);
        // t.inorder(t.getRoot());
        // t.postorder(t.getRoot());
        t.preorder(t.getRoot());
    }
}
```