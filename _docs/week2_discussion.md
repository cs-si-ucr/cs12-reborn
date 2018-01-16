---
title: Week 2 Discussion
permalink: /docs/discussion2/
---

###### Written by John Pham

## Lesson Plan

We will be covering new ways to access the input and output stream this week

### Standard Input and Output (Using a keyboard)

* `#include <iostream>` to do standard input and output operations
* Standard Output
  * `cout` is an **ostream** object that allows you to use `<<`, the **insertion operator**
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

## Exercises

1. Write a function that swaps the values in 2 variables
2. Write a function that reverses a string
3. Write a function that reverses a vector
