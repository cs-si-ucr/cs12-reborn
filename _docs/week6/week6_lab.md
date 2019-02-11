---
title: Lab
permalink: /docs/week6_lab/
---

Exercise 1
---
Implement the following functions listed below, this lab serves as an mini-intro to linked lists.

```c++
#include <iostream>

using namespace std;

struct Block {
  public:
    int val;
    Block * next;
    Block(int val): val(val), next(0) {};
};

void addBlock(Block * start, int val) {
    
}

void printBlockChain(Block* b) {
    
}

//remove last
void removeLastBlock(Block* b) {
    
}

int main() {
    Block* genesis = new Block(3);
    addBlock(genesis,5);
    addBlock(genesis,8);
    addBlock(genesis,10);
    addBlock(genesis,3);
    printBlockChain(genesis);
    
    // do more testing here
    
    return 0;
}
```

