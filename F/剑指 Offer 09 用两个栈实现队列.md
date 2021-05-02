# 剑指 Offer 09 用两个栈实现队列

```markdown
Label：栈

用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )
```

- 双栈   appendTail

```java
class CQueue {

    Stack<Integer> stack1;  // 存储
    Stack<Integer> stack2;
    
    public CQueue() {
        stack1 = new Stack<>();
        stack2 = new Stack<>();
    }
    
    public void appendTail(int value) {
        
        while (!stack1.isEmpty()) {
            stack2.add(stack1.pop());
        }
        stack2.add(value);
        // 颠倒
        while (!stack2.isEmpty()) {
            stack1.add(stack2.pop());
        }
    }
    
    public int deleteHead() {
        return stack1.isEmpty()? -1 : stack1.pop();
    }
}
```



























- 双栈    deleteHead

```java
class CQueue {
    Stack<Integer> stack1;
    Stack<Integer> stack2;
    
    public CQueue() {
        stack1 = new Stack<Integer>();
        stack2 = new Stack<Integer>();
    }
    
    public void appendTail(int value) {
        stack1.push(value);
    }
    
    public int deleteHead() {
        if (stack2.isEmpty()) {   // stack无了的时候才需要切换到已经排序为队列的值
            while (!stack1.isEmpty()) {
                stack2.push(stack1.pop());
            }
        }  
        return stack2.isEmpty()? -1 : stack2.pop();
    }
}
```

