---
title: Week 2 Discussion
permalink: /docs/week2/
---

###### Written by John Pham
###### Written / Modified by Josh Beto


## Lesson Plan

We will be covering new ways to access the input and output stream this week and going over problem solving


### Standard Input and Output (Using a keyboard)

* `#include <iostream>` to do standard input and output operations
* ```cout``` and ```cin``` are *variables* provided by ```iostream```

* Standard Output
  * `cout` is an **ostream** object that allows you to use `<<`, the **insertion operator**

    * `cout` will write words to the buffer. The buffer prints to the console when ```std::flush``` or ```std::endl``` is written.

        * ```cpp
            int x = 6;

            cout << x << endl;
            // user types in "hello world"
            // only "hello" is stored in userInput
            ```
    * **Important Note:** ```cout``` only prints to the console when the buffer is *flushed*. 

* Standard Input

  * `cin` is an **istream** object that allows you to use `>>`, the **extraction operation**

    * `cin` will only fetch "words" from the buffer. It will stop at whitespaces and newlines.

      * ```cpp
        string userInput;

        cin >> userInput;
        // user types in "hello world"
        // only "hello" is stored in userInput
        ```

  * `getline()` is a function that reads a "line of words" from the buffer

    * ```cpp
      string userInput;

      getline(cin, userInput);
      //user types in "hello world"
      // "hello world" gets stored in userInput
      ```

---

### File Input and Output

We can also use files as input for our programs and write to files rather than to the screen. We can accomplish this by using **file streams**.

* `#include<fstream>` to do file input and output operations
* File Input
  * You need to instanstiate a `ifstream` object
    * `ifstream inputFileStream;`
  * To open a file, you will use the `open()` method
    * `inputFileStream.open("myTextFile.txt")`
  * You can check if the file opened properly by using the `is_open()` method
    * ```cpp
      if (inputFileStream.is_open()) {
        cout << "File opened successfully!" << endl;
      }
      else {
        cout << "File failed to open" << endl;
      }
      ```
  * Once you have a file open, you can read from the from by using the **extraction operator**
    * `inputFileStream >> myVar`
  * When you're done reading from a file, it's good practice to close the stream by using the `close()` method
    * `inputFileStream.close()`
* File Output
  * You need to instanstiate a `ofstream` object
    * `ofstream outputFileStream`
  * You can then create a new file by using the `open()` method
    * `outputFileStream.open("output.txt");`
  * You can check if the file was created using the `is_open()` method
    * `outputFileStream.is_open() ? cout << "File opened" : "File failed to open";`
  * You can write to the file using the **insertion operator**
    * outputFileStream << "This text will be written to the file" << endl;

---

### Operators

* You can think of operators as a special kind of *function*
* Operators take in a set of arguments and may return a value
* Take the ```+``` operator as an example:
```cpp
int main() {
    int x = 3 + 2; // '+' operator takes in arguments '3' and '2', adds them, and returns '5'
    return 0;
}
```

* Like functions, operators can also be *overloaded*
```cpp
/*  In this example, the '<<' operator takes in multiple types. This is how
    you are able to use cout << *type* with many different types from 'int' to 'double'! 
*/
ostream& operator<< (bool val);
ostream& operator<< (int val);
ostream& operator<< (double val);
```

* *Challenge*: Why are you able to chain together multiple ```<<``` or ```>>``` respectively? 
  * *Hint*: Look back on what ```<<``` and ```>>``` return and the ```cin``` and ```cout``` types

---

### Problem Solving Tips
* If you get stuck on a part, skip to the parts you know and *abstract* the parts you do not know. *Abstract* means to understand what something does, but not think about how it is done. 
* Example: You have a function ```bool isAcceptable(int x)```
* You need to remove elements within a ```vector<int>``` *v* that are considered not acceptable. 
  * You can simply call ```isAcceptable(int x)``` to check for which elements to remove even if you do not know how to write ```bool isAcceptable(int x)```

### Mini Quiz
* Part 1: Write a function to calculate the digital root of a number. The definition of a digital root can be found here: https://en.wikipedia.org/wiki/Digital_root
* Part 2: Implement the following function: ```highestRoot(const vector<int> &v)```. This function returns the number within *v* with the highest digital root. Assume *v* is nonempty.
* Part 3: Write a main that generates 10 random integers from range 10-999 and prints the integer with the highest digital root among them.
