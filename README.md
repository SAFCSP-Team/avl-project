# AVL project

   
   
### Objective

In this project, our objective is to understand how to create an AVL tree by developing an insert method that checks the balance factor in each insert operation, and rebalance the tree when its not.    
   
   
### Problem
   
   
Create the below `AVL` tree:   

Figure 1   
<img width="910" alt="AVL" src="https://github.com/SAFCSP-Team/avl-project/blob/main/images/55%404x.png">
   
   
### Implementation   


In AVL class  
- Complete the insert method.

In Main method
- Create an AVL object.
- Insert the below numbers to the AVL tree, in the order from left to right:   
15, 55, 32, 105, 220.   
   
<br/>
<br/>


Node class

```java

public class Node {
    int data;
    Node left, right;
    int height;

    Node(int data) {
        this.data = data;
        this.left = null;
        this.right = null;
        this.height = 0;
    }
}

```




AVL class
``` java

public class AVL {

    public Node root;

    AVL(Node root) {
        this.root = root;
    }

    public void insert(int key) {
        root = insert(root, key);
    }

    private Node insert(Node node, int key) {
        /* Add your code here */
    }

    private int height(Node node) {
        if (node == null) {
            return 0;
        }
        return node.height;
    }

    private int getBalance(Node node) {
        if (node == null) {
            return 0;
        }

        int leftHeight = 0;
        int rightHeight = 0;

        if (node.left == null){
            leftHeight = -1;
        } else {
            leftHeight = height(node.left);
        }

        
        if (node.right == null){
            rightHeight = -1;
        }
        else {
            rightHeight = height(node.right);
        }

        return leftHeight - rightHeight;

    }

    private Node rightRotate(Node y) {
        Node x = y.left;
        Node T2 = x.right;

        x.right = y;
        y.left = T2;

        y.height = Math.max(height(y.left), height(y.right)) + 1;
        x.height = Math.max(height(x.left), height(x.right)) + 1;

        return x;
    }

    private Node leftRotate(Node x) {
        Node y = x.right;
        Node T2 = y.left;

        y.left = x;
        x.right = T2;

        x.height = Math.max(height(x.left), height(x.right)) + 1;
        y.height = Math.max(height(y.left), height(y.right)) + 1;

        return y;
    }

    public void printPreOrder() {
        printPreOrder(root);
    }
    
    private void printPreOrder(Node node) {
        if (node == null) {
            return;
        }
    
        System.out.print(" " + node.data);
        printPreOrder(node.left);
        printPreOrder(node.right);
    }

    public Node search(int key) {
        return search(this.root, key);
    }
    
    private Node search(Node node, int key) {
        if (node == null || node.data == key) {
            return node;
        }
    
        if (key < node.data) {
            return search(node.left, key);
        } else {
            return search(node.right, key);
        }
    }

    public static void main(String[] args) {
        
 AVL tree = new AVL(new Node(15));
        tree.insert(55);
        tree.insert(32);
        tree.insert(105);
        tree.insert(220);

        tree.printPreOrder();
    }

}


```
