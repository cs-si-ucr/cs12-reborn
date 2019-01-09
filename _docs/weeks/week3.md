---
title: Week 3 Discussion
permalink: /docs/week3/
---

###### Written by John Pham
###### Modified by Josh Beto

# Lesson Plan

This week we'll be covering creating our own custom classes with structs and classes.

## Structs

**Structs** allow us to create a new data type that groups together relevant data. If we wanted to keep track of a student say their name, age, and gender, normally we would have to create 3 separate variables to store that information.

```cpp
string name = "";
int age = 0;
string gender = "";
```

If we had tons of students we would have to rename the variables for each students.

```cpp
string name1 = "";
int age1 = 0;
string gender1 = "";

string name2 = "";
int age2 = 0;
string gender2 = "";
```

As you can see, this could get quite messy if we have to track a class worth of students. Structs allow us to group all 3 variables into a new data type.

```cpp
struct Student {
  string name;
  int age;
  string gender;
}

Student student1 = {"Bobo", 19, "Male"};
Student student2 = {"Lula", 19, "Female"};
```

Each variable inside a struct is referred to as a **data member** of the struct. If we wanted to access an individual data member, we would use the **dot operator**.

```cpp
struct Student {
  string name;
  int age;
  string gender;
}

Student student1 = {"Bobo", 19, "Male"};

// this will output: "Bobo19Male"
cout << student1.name << student1.age << student1.gender << endl;
```

We can also reassign the values after the data members were initialized, again using the dot operator.

```cpp
struct Student {
  string name;
  int age;
  string gender;
}

Student student1 = {"Bobo", 19, "Male"};

// this will output: "Bobo19Male"
cout << student1.name << student1.age << student1.gender << endl;

student1.age = 20;
// this will output: "Bobo20Male"
cout << student1.name << student1.age << student1.gender << endl;
```

Since structs are just new data types, we can use them in any situation that we use other types such as a return type for a function and the data type of a vector.

## Classes

Moving forward, we'll starting learning about **Object Oriented Programming**. This type of programming sets you to model your code's data as real life objects. Transactions, people, cars, basically anything can be modeled as an object in a program. You saw earlier that we were able to model a student in a struct. Structs however are quite limited on what they can do. Let's take a look at classes.

```cpp
class Student {
  public:
    void setName(string name);
    string getName();

    void setAge(int age);
    int getAge();

    void setGender(string gender);
    string getGender();
  private:
    string name;
    int age;
    string gender;
}
```

The above code shows our student struct rewritten as a class. This looks like a lot more work to accomplish the same thing but it allows us to define exactly what a Student can do.

Items under the `public:` keyword can be accessed outside of the class while items under `private:` can only be accessed within the class. This allows us to do error checking inside our public methods before reassigning the values of the private data members.

## Key Concepts

* Accessors (Getters)
* Mutators (Setters)
* Constructors
    * Default
    * Explicit
* The implicit parameter
    * `this->`

---

## Exercises
* Write a program that implements the following:
    * Define a custom *struct* `Animal` with the following parameters:
      * *name* - the name of the animal 
      * *species* - what kind of animal it is i.e. pig horse dog
      * *age* - how old the animal is

    * Write a function that takes in a `vector<Animal>` and prints that vector. The function should output the content of each animal as follows:
        * Name: actual_name
        * Species: actual_species
        * Age: actual_age

        * (Next Entry)

    * Write a main that fills a`vector<Animal>` with the following information:
    ```
       Name: Jessie
       Species: Dog
       Age: 3

       Name: Colbert
       Species: Pig
       Age: 5

       Name Violet
       Species: Horse
       Age: 7
    ```
      * Print out the `vector<Animal>` according to the function specified above.
