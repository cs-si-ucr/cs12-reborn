---
title: Lab
permalink: /docs/week3_lab/
---

Program 1
---
Given the following struct and its instances:

```c++
struct Weapon{
    int damage;
    int durabilty;
    string name;   
};

//weapon list
Weapon Hulk_Buster = {9000,50, "Hulk Buster"};
Weapon Mjolnir     = {5000,200,"Mjolnir"};
Weapon Pistol      = {10,  100,"Pistol"};
Weapon Lightsaber  = {50,  5,  "Lightsaber"};
Weapon Arrow       = {20,  10, "Arrow"};
Weapon Taser 	   = {60,  10, "Taser"};
Weapon Shield      = {100, INT_MAX,"Shield"};
Weapon Sling_Ring  = {1000,5,  "Sling Ring"};
Weapon Ants        = {100, 10, "Ants"};

//stones
Weapon Mind_Stone    = {10000,INT_MAX,"Mind Stone"};
Weapon Time_Stone    = {10000,INT_MAX,"Time Stone"};
Weapon Space_Stone   = {10000,INT_MAX,"Space Stone"};
Weapon Reality_Stone = {10000,INT_MAX,"Reality Stone"};
Weapon Power_Stone   = {10000,INT_MAX,"Power Stone"};
Weapon Soul_Stone    = {10000,INT_MAX,"Soul Stone"};
```
Create a class 'Avenger' which has the following attributes:

 * name
 * age
 * arsenal (a list of all usable weapons)

And can perform the following operations:

 * set name and corresponding getter
 * set age and corresponding getter
 * add weapon to arsenal
 * remove weapon from arsenal
 * display arsenal

And of course don't forget the default constructor and a constructor that accepts name and age.

Program 2
---
Given the following code:
```c++
int main(){
    vector<Avenger> avengers;
    Avenger Cap("Steve Rogers", 100);
    Avenger iMan("Anthony/Tony Stark", 52);
    Avenger bWidow("Nat", 33);
    Avenger Hulk("Bruce Banner", 50 );
    Avenger Thor("Thor Odinson", 34);
    Avenger Hawkeye("Clint Barton", 47);
    Avenger Vision("J.A.R.V.I.S",2 );
    Avenger sWitch("Wanda Maximoff", 28 );
    Avenger bPanther("T'Challa", 42 );
    Avenger antMan("Scott Lang", 48 );
    Avenger spiderMan("Peter Parker", 21); //The actor is one month older exactly than Andre!
    Avenger starLord("Peter Quill", 38 );
    Avenger omarvelous("Omar ", 20); 
    Avenger andreKhastro("Andre ", 21);   
    
    // push back the values to vector avengers.

    sort(avengers); //sorts in place
    print(avengers);
    
    return 0;
}
```
Expand on Exercise 1 by adding a sort function that sorts the above vector **in place**. </br>
If you do not know what is meant by "in place", then ask :). </br>
Lastly, print out the vector with each Avenger being printed out as `name, age`.


# Program 3

Create a class modeled after a car. Your class should include the following data members:

* Car brand
* Year
* Type
* Miles Driven

You will then create a program that allows a user to populate a list of the cars they own. After the user is done, your program will output the cars they own.

Here's a sample of how your program should function.

```
Hello! I'm a program that will help you keep track of your car inventory. Let's get started.

What's your car's brand?
"Hyundai" // words in "" is user input

When was your car made?
"2009"

What type of car is it?
"Coupe"

How many miles have you driven in it?
"321563"

That's a pretty cool car. Do you have any other cars? If so enter 'c' or to exit enter 'q'.
"c" // this will repeat the program
"q" // this will end the loop causing the program to output

Car Inventory:
1: Hyunday, 2009, Coupe, 321563
2: ...
...
```

You should use `private` and `public` properly along with creating the appropiate getters, setters, and methods.

# Program 4

Extend program 1 by allowing the user to export their car inventory to a file after they enter 'q'. It is in the same format as the output to standard output.

```
That's a pretty cool car. Do you have any other cars? If so enter 'c' or to exit enter 'q'.
"q" // this will end the loop causing the program to output

Do you want to export your inventory to a file? 'y' for yes and 'n' for no
"y"

Your inventory was exported to a file called "car-inventory.txt"
```
