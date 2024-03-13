# Building Linked List from Scratch

## Code
```java 
public class LL{

    Node head;
    private int size;

    LL(){
        this.size = 0;
    }

    class Node{
        String data;
        Node next; 

        Node(String data){
            this.data = data;
            this.next = null;
        }
    }

    //add - first, last 
    public void addFirst(String data){
        Node node = new Node(data);
        if(head == null){
            head = node;
            size ++;
            return; //due to this return keyword, the contro exits the entire method
        }// => the statements below the return keyword wont be executed if return is encountered during execution.
        node.next = head;
        head = node;
        size ++;
    }
    // add Last
    public void addLast(String data){
        Node node = new Node(data);
        if (head == null){
            head = node;
            size ++;
            return;
        }
        // traversal
        Node currNode = head;
        while(currNode.next != null){
            currNode = currNode.next;
        }
        currNode.next = node;
        size ++;
    }
    //printlist
    public void printList(){
        Node currNode = head;
        if (head == null){
            System.out.println("Empty List");
        }
        //traversal
        while(currNode != null){
            System.out.print(currNode.data + " -> ");
            currNode = currNode.next;
        }
        System.out.print("End");
        System.out.println();
    }
    //delete first
    public void deleteFirst(){
        if (head==null){
            System.out.println("The list is empty");
            return;
        }
        head = head.next;
        size --;
    }
    //delete last
    public void deleteLast(){
        if(head == null){ //corner case for 0 nodes
            System.out.println("The list is Empty");
            return;
        }
        size --;
        if(head.next == null){
            head = null; //deleting the only node present
        }
        Node secondLast = head;
        Node lastNode = head.next;//if head.next = null,
        while(lastNode.next != null){//if we ask for null.next, we get error
            lastNode = lastNode.next;
            secondLast = secondLast.next;
        } // after traversal, secondLast -> last 2nd elem.
        secondLast.next = null; //breaking off the link b/w last & 2nd last
        // second last element becomes last element,
        // since its next node is null now
        //the nodes left out / deleted from the LinkedList are collected
        //by the garbage collector
    }
    //get size
    public int getSize(){
        return size;
    }

    public void reverseIterate(){
        if(head == null || head.next == null){ return;}
        Node prevNode = head;
        Node currNode = head.next;
        while(currNode != null){
            Node nextNode = currNode.next;
            currNode.next = prevNode;
            //Updation
            prevNode = currNode;
            currNode = nextNode;
        }
        head.next = null;
        head = prevNode;
    }
    public Node reverseRecursive(Node head){
        if(head == null || head.next == null){
            return head;
        }
        Node newHead = reverseRecursive(head.next);
        head.next.next = head;
        head.next = null;
        return newHead;
    }

    public static void main(String args[]){
        LL list = new LL();
        list.addFirst("a");
        list.printList();
        System.out.println(list.getSize());

        list.addFirst("is");
        list.printList();
        System.out.println(list.getSize());

        list.addLast("List");
        list.printList();
        System.out.println(list.getSize());

        list.addFirst("This");
        list.printList();
        System.out.println(list.getSize());

        list.reverseIterate();
        list.printList();

        list.deleteFirst();
        list.printList();
        System.out.println(list.getSize());

        list.deleteLast();
        list.printList();
        
        System.out.println(list.getSize());
    }
}
```
