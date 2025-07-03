<details>
<summary>Table of Contents</summary>
<ol>
  <li>
    <a href='#structure-variables'>Structure Variables</a>
  </li>    
  <li>
    <a href='#structure-types'>Structure Types</a>
  </li>    
  <li>
    <a href='#nested-arrays-and-structures'>Nested Arrays and Structures</a>
  </li>  
  <li>
    <a href='#programming-projects'>Programming Projects</a>
  </li>    
</ol>
</details>

## Structure Variables
<ul>
  <li>
    <a>The elements of a structure do not have to be of the same type</a>
  </li>
</ul>    

### Declaring Structure Variables
<ul>
  <li>
    <a>Here is the syntax for declaring a structure variable</a>

```c
struct variableName
{
    char variableOne;
    int variableTwo = 2;
    char name[12];
};
```
  </li>
  <li>
    <a>The structure can contain any type of variable within it, such as chars, bools, ints, arrays, strings, ect.</a>
  </li>  
</ul>  

### Initializing Structure Variables
<ul>
  <li>
    <a>Similar to an array, a structure variable can be initialized at the same time that it is declared</a>
  </li>
  <li>
    <a>Here is the syntax for initializing a structure variable:</a>

```c
struct variableName
{
    char variableOne;
    int variableTwo;
    char name[12];
} Garrett = {'A', 21, "Garrett"},
  Evan = {'A', 22, "Evan"};
```
  </li>    
</ul>    

### Operations on Structures
<ul>
  <li>
    <a>Rather than structures being accessed by position like arrays, structures are accessed by names</a>
  </li>
  <li>
    <a>To access a member of a structure, the dot operator is used. Here is the syntax for accessing a structure's members:</a>

```c
structName.memberName;
```
  </li>
  <li>
    <a>The assignment operator can be used on different variables of the same structure. By assigning one structure variable to another, the contents of the right-hand variable are copied to the contents of the left-hand variable</a>
    <ul>
      <li>
        <a>Here is an example of assigning one struct instance to another:</a>

```c
struct part {
    int number;
    char name[LENGTH + 1];
};

struct part part1 = {528, "Garrett"};
struct part part2;
part2 = part1;
```
  </li>
  </ul>
  </li>  
</ul>    

## Structure Types
### Declaring a Structure Tag
<ul>
  <li>
    <a>A <em>structure tag</em> is a name used to identify a structure</a>
  </li>
  <li>
    <a>Here is the syntax for a structure tag:</a>

```c
struct part
{
    int number;
    char name[nameLength + 1];
    int onHand;
}; 
```
  <ul>
    <li>
      <a>Remember that there is a semicolon at the end of the braces is a semicolon</a>
    </li>  
  </ul>
  </li>  
</ul>  

### Structures as Arguments and Return Values
<ul>
  <li>
    <a>Functions can have structures as arguments and functions can return structure instances</a>
  </li>
  <li>
    <a>Here is the syntax for passing a structure instance in a function call:</a>

```c
void functionName(struct strucName instanceName)k
{
    ...
}
```
  </li>
  <li>
    <a>Here is the syntax for defining a function with a structure instance return type</a>

```c
struct structName functionName(int variableName, char charVar)
{
    struct structName instanceName;

    return instanceName;
}
```
  </li>
</ul>  

## Nested Arrays and Structures
### Nested Structures
<ul>
  <li>
    <a>Arrays can be used to store elements that are instances of struct variables</a>
  </li>
  <li>
    <a>Structures can even be nested within each other. For instance, an instance of structName can have a variable type of structName2</a>
    <ul>
      <li>
        <a>Here is the syntax of a nested structure:</a>

```c 
struct Person {
    char first[FIRST + 1];
    char middle;
    char last[LAST + 1];
};

struct student {
    struct Person name;
    int id, age;
};
```
  </li>
  </ul>
  </li>
</ul>    

### Arrays of Structures
<ul>
  <li>
    <a>Oftentimes, an array can be of type struct variable which means that the declared array contains instances of the struct</a>
  </li>
  <li>
    <a>Here is the syntax for creating an array of type struct variables:</a>

```c
struct structVariable arrayName[arraySize];
```
  </li>
  <details>
    <summary>Write a structure called Students with the following fields: name, age, grade, and roll_number. Write a program to input details for five students, then display them in a formatted way</summary>

```c
//Complete the search function that loops up the part in inv (an array of struct part). The function prompts the user to enter a part number. If the part exists, print the name and quantity on hand; if not, print a "part not found" message. Parameter np contains the number of parts in the array

//Assume the structure part is defined as:
struct part {
    int number;
    char name[31];
    int on_hand;
};

void search(struct part inv[], int np)
{
    int number;
    printf("Enter part number: ");
    scanf("%d", &number);
}
```
<ul>
  <details>
    <summary>Output</summary>

```c 
void search(struct part inv[], int np)
{
    int number, found = 0;

    printf("Enter part number: ");
    scanf("%d", &number);

    for (int i = 0; i < np; i++)
        if (inv[i].number == number) {
            printf("%s", inv[i].name);
            printf("%d", inv[i].on_hand);
        }

    if (!found)
        printf("part not found");
}
```
  </details>
    </ul>  
  </details>
</ul>    

## Programming Projects
<details>
    <summary>Write a structure called Students with the following fields: name, age, grade, and roll_number. Write a program to input details for five students, then display them in a formatted way</summary>

```c
#include <stdio.h>

//macro definition for the maximum number of students allowed in the class
#define MAX_STUDENTS 5

//structure to store student information
struct Student
{
    char name[50];
    int age;
    float grade;
    int rollNum;
};

//getInfo function to get student information from the user
void getInfo(struct Student *);

//printInfo function to print student information
void printInfo(struct Student *);

int main()
{
    //array of student structures to store the information of all students in the class
    struct Student students[MAX_STUDENTS];

    //get student information from the user and store it in the array
    getInfo(students);
    //print the information
    printInfo(students);

}

//getInfo function to get student information from the user
void getInfo(struct Student *student)
{
    //loop to get information for each student in the class
    for (int i = 0; i < MAX_STUDENTS; i++)
    {
        printf("Enter name: ");
        scanf("%s", student[i].name);

        printf("Enter age: ");
        scanf("%d", &student[i].age);

        printf("Enter grade: ");
        scanf("%f", &student[i].grade);

        printf("Enter roll number: ");
        scanf("%d", &student[i].rollNum);

        printf("\n");
    }
}

//printInfo function to print student information
void printInfo(struct Student *student)
{
    printf("Name\tAge\tGrade\tRoll Number\n");

    //loop to print information for each student in the class
    for (int i = 0; i < MAX_STUDENTS; i++)
        printf("%s\t%d\t%.2f\t%d\n", student[i].name, student[i].age, student[i].grade, student[i].rollNum);
}
```
<ul>
  <details>
    <summary>Output</summary>
      <pre>
        <code>
Enter name: Garrett
Enter age: 21
Enter grade: 12
Enter roll number: 3113

Enter name: Evan
Enter age: 17
Enter grade: 99
Enter roll number: 999

Enter name: Marissa
Enter age: 15
Enter grade: 97
Enter roll number: 83473

Enter name: David
Enter age: 60
Enter grade: 93
Enter roll number: 39434

Enter name: Michelle
Enter age: 57
Enter grade: 87
Enter roll number: 324892

Name    Age     Grade   Roll Number
Garrett 21      12.00   3113
Evan    17      99.00   999
Marissa 15      97.00   83473
David   60      93.00   39434
Michelle        57      87.00   324892
        </code>
        </pre>  
      </details>
    </ul>  
  </details>
