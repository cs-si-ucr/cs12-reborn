---
title: Program 1
permalink: /docs/program1/
---

###### Written by Josh Beto 
###### Testing Section from John Pham


### Definitions

* In this program, you will implement these functions with the following descriptions:

```cpp
/*
passes in the name of a file and two vectors (double) and stores in the first vector the flight-path angles (first column) 
and in the second vector the corresponding coefficients of lift (2nd column). 
If the file does not open properly, this function should output an error message and then call the exit function passing it an exit value of 1
*/
void readData(const string &, vector<double> &, vector<double> &);

/*
passes in the requested flight-path angle along with the 2 vectors of data (flight-path angles and 
corresponding coefficients of lift) and returns the corresponding coefficient of lift.
*/
double interpolation(double, const vector<double> &, const vector<double> &);

/*
passes in the vector of flight-path angles and returns true if it stores the angles are in ascending order, otherwise returns false. 
*/
bool isOrdered(const vector<double> &);

/*
passes in both vectors of data and then reorders the data so that the flight-path angles are in ascending 
order while maintaining the correspondence between the flight-path angles and their corresponding coefficients of lift.
*/
void reorder(vector<double> &, vector<double> &);
```

---

### Understanding Your Input
* The terminology of this program's description may seem confusing, but is actually very simple!
* Instead of thinking of *flight-path* angles and *lift coefficients*, think instead in terms of *x* and *y* coordinates like math
* i.e. Your input file:
  * 0.0 1.0
  * 3.4 2.9
  * 1.5 1.9
  * 5.0 5.6

    The first column of the input file can be thought of as your *x-coordinate* and the second column as the *corresponding y-coordinate*.
    Notice how in this description, the *x* and *y* are considered together as a pair that describes a point, **NOT** as separate entities. 
    This will prove important when it comes to *reordering* the data points later on!


### `readData` function
* The first issue you may see is *parsing* the input from the file
  * Tips:
    * If you are struggling with reading in each number alternatively into two different `vectors`, think about the most basic case when there is only *one* data      point i.e. 0.1 0.3. After you have read in this single data point into both the `vector<double> angles` and `vector<double> coeff` respectively, try 
      generalizing this to a loop that can read multiple data points.



### `interpolation` function
* Linear interpolation is the process of *estimating* the value of some y-coordinate as a *linear* relationship given the x-coordinate and a set of data points
* To visualize this next example, I recommend graphing each data point by hand in paper to follow along:
  * i.e. Your input file:
    * 0.0 0.0
    * 1.0 1.0
    * 2.0 4.0
    * 3.0 9.0

      * Now, let's say I wanted you to give me the estimated y-coordinate of an x-coordinate of 2.0. That would be really easy given our data; the x-coordinate of
        2.0 is already included, so we would just output 4.0 as our answer. There is *no need to estimate if we already have the data point asked for*. 
      * However, if I wanted the y-coordinate of an x-coordinate of 1.5, we would need to estimate the y-coordinate via linear interpolation. In this case, we 
        would find the *closest point above and below our x-coordinate*. In our example, the closest point above our x-coordinate of 1.5 is (2.0, 4.0) and the closes point below is (1.0, 1.0). Since our x-coordinate is halfway between these two coordinates, we know our estimated value of y is 2.5, giving us a coordinate of (1.5, 2.5). 
      * This can be easily seen visually if you draw a line between the points (1.0, 1.0) and (2.0, 4.0). In a more complex linear interpolation, we would just use    the formula: 
          * f(b) = f(a) + ((b - a)/(c - a))(f(c) - f(a)).
            *    b = given x-coordinate
            * f(b) = estimated y-coordinated
            * f(a) = y-coordinate of point below our given x
            * f(c) = y-coordinate of point above our given x
            *    a = x-coordinate of point below our given x
            *    c = x-coordinate of point above our given x


### `reorder` function
* To implement this function, think back to your days in CS010 where you had to implement Bubble Sort!
* As a reminder, you can look at this page and the following pseudo-code: https://en.wikipedia.org/wiki/Bubble_sort
  * **Tip**: Make sure you sort both `vectors` together instead of individually! Think of the flight-path(x-coord) and lift coefficient(y-coord) as a *single* point
    * i.e. Your input file
      * 3.0 9.0
      * 1.0 6.0
      * 2.0 4.0
      * 4.0 7.0

        These points would get sorted as follows:

      * 1.0 6.0
      * 2.0 4.0
      * 3.0 9.0
      * 4.0 7.0

         * Notice how the first column (flight-path angles) are sorted in *ascending* order and keep their matching respective lift coefficient in the other vector index-wise.

---

### Common Pitfalls
* Not performing **ALL** the proper file procedures
  * open 
  * check **IF** the file opens successfully
  * read / write
  * close

* Comparing `doubles` with `==` or `<=` / `>=`. Remember that although `doubles` are *precise*, they do not perform well in equality tests since even the
  same double values might be different by a *very very small factor such as e^-7*. Make sure to test the absolute difference of `doubles` against some small
  epsilon value of e^-7 instead of doing equality. 

* Not parsing the input correctly. A common mistake is testing the end-of-file with the function `eof` or `good` / `bad` function in the `while` condition, but        **NOT** checking the extracted input. If you choose to do so, **check** whether the input got read in correctly after `>>`. An alternative approach to               checking end-of-file is simply using the `>>` operator in the `while` loop.
    * i.e. `while(cin >> num)`// this will terminate properly on invalid input!

* Not checking each element of a `vector`

* Going out of bounds on a `vector`. To check this, simply go over where you access the vector with `at()` and the boolean condition of your loop. Chances are you 
  are using `at(i+1)` but your loop condition is set at `i < v.size()`, meaning you are going one index over your max.

* Sorting both `vectors` separately instead of together in `reorder`

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