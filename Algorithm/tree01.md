# 트리 1. 후위탐색 N번째 값을 구하라

### 출제 의도

- 큐를 알고 있는가?
- 재귀로도 생각할 수 있는가?

### 문제. 
주어진 이진 트리에서 후위탐색시 n번째 해당하는 값을 구하라.

```java
// 출력을 위한 main 메서드
public static void main(String[] args) {
        Node root = new Node(1);
        root.left = new Node(2);
        root.right = new Node(3);
        root.left.left = new Node(4);
        root.left.right = new Node(5);
        root.right.left = new Node(6);
        root.right.right = new Node(7);

        PostOrder postOrder = new PostOrder();
        postOrder.print(root, 4);
    }
```

### 풀이

```java
// 시간복잡도 : O(N)
// 공간복잡도 : O(LogN)
public class PostOrder {

    private static class Node {
        int value;
        Node left, right;

        public Node(int value) {
            this.value = value;
        }
    }

    public static void main(String[] args) {
        Node root = new Node(1);
        root.left = new Node(2);
        root.right = new Node(3);
        root.left.left = new Node(4);
        root.left.right = new Node(5);
        root.right.left = new Node(6);
        root.right.right = new Node(7);

        PostOrder postOrder = new PostOrder();
        postOrder.print(root, 4);
    }

    private int count = 0;

    private void print(Node root, int index) {
        if (root != null) {
            print(root.left, index);
            print(root.right, index);

            if (count++ == index - 1) {
                System.out.println(root.value);
            }
        }
    }
}
```