---
title: Program 2
permalink: /docs/program2/
---

###### Written by Josh Beto 
###### Testing Section from John Pham


### Definitions

* In this program, you will implement the following class:

```cpp
class Date {
 private:
   unsigned day;
   unsigned month;
   string monthName;
   unsigned year;

 public:
   // creates the date January 1st, 2000.
   Date();


   /* parameterized constructor: month number, day, year 
       - e.g. (3, 1, 2010) will construct the date March 1st, 2010

       If any of the arguments are invalid (e.g. 15 for month or 32 for day)
       then the constructor will construct instead a valid Date as close
       as possible to the arguments provided - e.g. in above example,
       Date(15, 32, 2010), the Date would be corrected to Dec 31st, 2010.
       In case of such invalid input, the constructor will issue a console error message: 

       Invalid date values: Date corrected to 12/31/2010.
       (with a newline at the end).
   */
   Date(unsigned m, unsigned d, unsigned y);


   /* parameterized constructor: month name, day, year
 ­      - e.g. (December, 15, 2012) will construct the date December 15th, 2012

       If the constructor is unable to recognize the string argument as a valid month name,
       then it will issue a console error message: 

       Invalid month name: the Date was set to 1/1/2000.
       (with a newline at the end).

       If the day argument is invalid for the given month (but the month name was valid),
       then the constructor will handle this error in the same manner as the other
       parameterized constructor. 

       This constructor will recognize both "december" and "December"
       as month name.
   */
   Date(const string &mn, unsigned d, unsigned y);


   /* Outputs to the console (cout) a Date exactly in the format "3/1/2012". 
      Does not output a newline at the end.
   */
   void printNumeric() const;


   /* Outputs to the console (cout) a Date exactly in the format "March 1, 2012".
      The first letter of the month name is upper case, and the month name is
      printed in full - January, not Jan, jan, or january. 
      Does not output a newline at the end.
   */
   void printAlpha() const;

 private:

   /* Returns true if the year passed in is a leap year, otherwise returns false.
   */
   bool isLeap(unsigned y) const;


   /* Returns number of days allowed in a given month
      -  e.g. daysPerMonth(9, 2000) returns 30.
      Calculates February's days for leap and non-­leap years,
      thus, the reason year is also a parameter.
   */
   unsigned daysPerMonth(unsigned m, unsigned y) const;

   /* Returns the name of a given month
      - e.g. name(12) returns the string "December"
   */
   string name(unsigned m) const;

   /* Returns the number of a given named month
      - e.g. number("March") returns 3
   */
   unsigned number(const string &mn) const;
};
```

---

### `unsigned` data type
* The `unsigned` date type represents integers that are >= 0. 
* Common Pitfalls:
  * Subtraction with `unsigned` - Be careful when using any subtraction with the `unsigned` data type, specifically `--`.
  ```cpp
  int example(const vector<int> &v) {
    for (unsigned i = v.size() - 1; i >= 0; i--) { // Throws an out of bounds error at the last loop iteration or of v.size() is 0!
      cout << v.at(i) " ";
    }
  }
  * Type Conversions:
    * The `vector<T>` function, `size()` returns an `unsigned` data type. zyBooks may throw an error if you try to cast
      this `unsigned` data type to `int` implicitly or vice-versa.


### Implement the helper functions first
* The helper functions offer helpful functionality to complete the public functions and the Constructor!
* Make sure these helper functions return/throw an error on any unexpected input i.e. month = 14


### The Constructors
* The constructors are *special* functions that do two things:
  * Create the object
  * Initialization
* A constructor returns the newly created object i.e. `vector<int> b` // calls default constructor for vector
* The *default* constructor (No arguments) is called when there is no explicit call to any other constructor

---

### Testing

As programmers, we need to strive to writing correct code. This means our code should work properly for any set of inputs.

* Asserts
  * `#include <cassert>`
    * Need to include `cassert` to use the `assert` function
  * `assert(func(a, b) == c)`
    * This will test whether the output of `func(a, b)` equals `c`.

```cpp
#include <iostream>
#include <math>
using namespace std;

int pow(int a, int b) {
  return pow(a, b);
}
int main() {
  assert(pow(2, 2) == 4);
  assert(pow(2, 3) == 8);
  assert(pow(3, 3) == 10); // this will throw an error

  return 0;
}
```