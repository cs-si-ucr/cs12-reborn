---
title: Midterms
permalink: /docs/midterm/
---

###### Written by Josh Beto


**Problem 1:**

Define a class called `Parser` that represents a parsed sentence. Each word in the sentence is **whitespace character separated** like `'\n'` and `' '`

  * You should store a `vector<string> words` that represents each parsed word in a given sentence

  * You need to implement *functions* that do the following:
    * Constructor that parses a given string
    ```cpp
    Parser p("This is a sentence");
    // p should store a vector<string> words as follows:
    // ["This", "is", "a", "sentence"]
    ```
    * Prints out each word in the sentence on each line
    ```cpp
    Parser p("This is a sentence");
    p.print();
    /*
    This
    is
    a
    sentence
    */
    ```
    * Returns a word at a given index. Does not change any private variables.
    ```cpp
    Parser p("This is a sentence");
    string s = p.getWord(1);
    cout << s << endl; // prints out 'is'
    ```
    * Changes a word at a given index. Does not return anything.
    ```cpp
    Parser p("This is a sentence");
    p.changeWord(3, "string"); // Changes the `vector<string>` words to ["This", "is", "a", "string"]
    ```
    * Filters out parsed words based on a given word
    ```cpp
    Parser p("This is not a sentence"); // Changes the `vector<string>` words to ["This", "is", "a", "sentence"]
    p.filter("not");
    p.print();
    ```

  * **Note:** Don't worry about any out of bounds error checking

**Problem 2:**

Define a class called `Wallet` that stores money

  * You should store money as `unsigned dollars` and `unsigned cents`

  * You need to implement the following functions:
    * Constructor that uses an *initialization list* to take in `unsigned dollars` and `unsigned cents`.
    If the cents >= 100, convert the extra cents to dollar amounts
    ```cpp
    Wallet w(5, 70); // 5 dollars and 70 cents
    Wallet w2(10, 230) // 12 dollars and 30 cents
    ```
    * Constructor that takes in no arguments and initializes dollars and cents to 0
    ```cpp
    Wallet w(); // 0 dollars and 0 cents
    ```
    * Overload operator+ to take in another `Wallet` object and return the sum `Wallet` object
    ```cpp
    Wallet w1(5, 70);
    Wallet w2(30, 80);
    w3 = w1 + w2; // w3, dollars = 36, cents = 50
    ```
    * Setter and getter for `unsigned dollars`
    * Setter and getter for `unsigned cents`
    * Print function that prints out the dollars & cents as follows:
    ```cpp
    Wallet w(5, 70);
    w.print(); // prints out $5.70
    ```

**Problem 3:**

Create a class called `AttendanceSheet`.
  * Define any neccessary structs or classes
  * Specifications:
    * Constructor that takes in an integer, which is the number of students *enrolled* in the class, and
      a string date, the current date of attendance
    * Stores a list of students that have signed in to class today
      * Students have an integer ID and a name
    * Has a function that adds students to the attendance sheet. Each student enrolled **must be unique**, no duplicate sign-ins!
    * Has a function that evaluates if the class is cancelled. A class is cancelled when the number of signed in is less
      than 20% of the total number of students enrolled.
    * Has a function that clears the attendance sheet for the next session
    * Has a function that outputs the list of students to a file called `'attendance-<date>.txt'` i.e. attendance-October-1st-2018
      * The students will be printed out each on a new line, with their `<name>` followed by `<SID>`
      * i.e.
      ```
        Alice 1203
        Bob 7820
        ...
      ```


**Problem 4:**

Come up with a definition for a `University` class

  * You do **not** need to implement any of the functions, just declare them

  * Specifications:
    * A list of enrolled students. Students have an SID, major, name, and year. In this university, a student immediately graduates
      after completing their 4th year.
    * A list of professors. Professors have a name and research specialty
    * The ability to sort the students in alphabetical order based on their name
    * Get a list of students that are graduating at the end of the year
    * The ability to add students by passing in the name of a file. Assume all new students are freshman. The file is ordered as follows:
      * Each line of the file denotes a different student.
      * Lines are ordered as follows:
        * `<SID> <major> <name>`
    * The ability to remove students that are graduating at the end of the year.
    * The ability to add a professor by passing in a name and research specialty.

**Conceptual Questions**

* Why are you allowed to chain together the `<<` and `>>` operator? i.e. `cout << "1" << "2" << "3" << endl;`
* `const int add(const string &s) const` - What does each of the 3 `const` mean?
* Pass by reference vs. pass by value
* What happens to the left hand side of the + operator when you overload it in a class?
  * i.e.
  ```cpp
  class IntExample {
    private:
      int i;
    public:
      IntExample(int);
      IntExample operator+(IntExample);
  };

  /*
  ...
  */

  int main() {
    IntExample i(6);
    IntExample j(9);
    i = i + j; // What happens to the left side, 'i', when you call the + operator.
  }
  ```