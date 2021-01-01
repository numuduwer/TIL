## 과제 3. Stack을 구현하세요. 
- int 배열을 사용해서 정수를 저장하는 Stack을 구현하세요. 
- void push(int data)를 구현하세요.
- int pop()을 구현하세요 

## Stack
- 나중에 저장한 data가 먼저 나오는 구조 (Last In First out)
- Last In Firsh Out(LIFO) 특징을 가지고 있다. 



## Stack 4가지 기능 
- pop()  :  마지막 데이터를 가져오면서 지움 
- push() :  새로운 데이터를 쌓는것
- peek() :  맨 마지막 데이터를 보는 것
- isEmpty() : 데이터가 있는지 없는지 보는것 

## 코드 2 (배열을 사용)
~~~java 
    
~~~

## 코드 1 (Linked List)

~~~java 
import java.util.EmptyStackException;

class Stack<T>{
    class Node<T>{
        private T data;
        private Node<T> next;
        
        public Node(T data){
            this.data = data;
        }
    }
    
    private Node<T> top;
    
    public T pop() {
        if(top == null){
            throw new EmptyStackException();
        }
        T item = top.data;
        top = top.next;
        return item;
    }
    
    public void push(T item){
        Node<T> t = new Node<T>(item);
        t.next = top;
        top = t;
    }
    
    public T peek(){
        if (top == null){
            throw new EmptyStackException();
        }
        return top.data;
    }
    
    public boolean isEmpty(){
        return top == null;
    }
}


class Main {  
  public static void main(String args[]) { 
    
    Stack<Integer> s = new Stack <Integer>();
    s.push(1);
    s.push(2);
    s.push(3);
    s.push(4);
    
    System.out.println(s.pop());
    System.out.println(s.pop());
    System.out.println(s.peek());
    System.out.println(s.pop());
    System.out.println(s.isEmpty());
  } 
}
~~~