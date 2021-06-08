# 큐 3. 바이너리 트리의 계층별 합계 중에 최대 값을 구하라.

### 출제 의도

- 바이너리 트리를 이해하고 있는가?
- BFS 로직을 구현할 수 있는가?
- 큐를 활용할 수 있는가?

### 문제

```java
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

        TreeLayerSum treeLayerSum = new TreeLayerSum();
        System.out.println(treeLayerSum.maxSum2(root) == 15);
    }
```

### 풀이

1. **일반**

```java
// 시간복잡도 : O(N)
// 공간복잡도 : O(N)
private int maxSum2(Node root){
        if(root == null){
            return 0;
        }
        int result = root.value;

        Queue<Node> queue = new LinkedList<>();
        queue.offer(root);

        while(!queue.isEmpty()){
            int count = queue.size();
            int sum = 0;

            while(count>0){
                count--;
                Node node = queue.poll();
                sum += node.value;

                if(node.left != null){
                    queue.offer(node.left);
                }

                if(node.right != null){
                    queue.offer(node.right);
                }
                result = Math.max(result, sum);
            }
        }

        return result;
    }
```