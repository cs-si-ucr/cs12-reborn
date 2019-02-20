We are going to make a `Train` linked list today.

Cart Node
---

Below is the code for a Cart struct.
Each `Cart` object should *point* to the `Cart` before it and the `Cart` after it.
This makes the Train a doubly linked list.

```c++
struct Cart{
  int weight;
  Cart * prev;
  Cart * next;
  Cart(int weight): weight(weight), prev(0), next(0){};
};
```

Train List
---
The Train class is a linked list composed of Cart objects.
Below is the class definition

```c++
class Train{
    private:
      Cart * head;
      Cart * tail;
    
    public:
      //constructor
      Train(): head(nullptr),tail(0nullptr){}
      
      //add a cart to the end
      void addLastCart(int weight);
    
      //add a cart to the beginning
      void addFirstCart(int weight);
    
      //view the entire train starting from the head
      void viewTrainForwards();
    
      //view the train starting from the back
      void viewTrainBackwards();
    
      //count number of carts with given weight
      int cartsWithWeight(int weight);
    
      void printHead();
      
      void printTail();
};

Implement the functions of the class as listed above, ask if you need help :)
```
