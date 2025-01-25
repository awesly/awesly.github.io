---
layout: project
type: project
image: img/micromouse/micromouse-square.jpg
title: "C / C++ Records Database Application"
date: 2024
published: true
labels:
  - C
  - C++
  - Vim
  - Unix
summary: "A functional database of bank records written in C, and later rewritten in C++, for ICS 212."
---
The main project in ICS 212 at the [University of Hawaii at Manoa Information and Computer Science Dept](https://www.ics.hawaii.edu/) was creating a database of records of names, addresses, and account numbers. It features a text based user interface with options to add, delete, find, and print a record, and the backend also implements cleanup of the data and the ability to store the database in a file to be used to restore it the next time the program is run. The project was done in two main parts, which were the front end, the user interface, and the back end, the database itself. The records were each a struct in C and C++, and were made into a database as a linked list. Pointers were used in the C version, and passing by reference was also used in the C++ version. Implememting the C++ version neccessitated a full redesign of the structure and approach to the database, to make it Object Oriented instead of Procedural. 

Here is some code that illustrates an example of one of the database functions in C:

```cpp
void printAllRecords(struct record * start)
{

    /* variable for traversing */
    struct record * currentRecord = NULL;

    if (debugmode == 1)
    {
        printf("\nThe function printAllRecords was successfully called!\n");
        printf("There are no parameters to be printed.\n");
    }

     /* if list is empty, print so */
    if (start == NULL)
    {
        printf("There are no records.\n");
    }
    else
    {
         currentRecord = start;

        /* traverse the list, printing each element */
        while (currentRecord != NULL)
        {
            int i = 0;
            /* print eatch field */
            printf("\n%d\n", currentRecord->accountno);
            printf("%s\n", currentRecord->name);

            /* print the address not including the ! */
            while(currentRecord->address[i] != '!' && currentRecord->address[i] != '\0')
            {
                putchar(currentRecord->address[i]);
                i++;
            }

            printf("\n");

            /* iterate */
            currentRecord = currentRecord->next;
        }
    }
}
```

And some code illustrating the database as a linked list class in C++:

```cpp

/* include guard */
#ifndef LLIST_H
#define LLIST_H

    #include "record.h"
    #include <iostream>
    using namespace std;
    extern int debugmode;

    class llist
    {
        private:
            /* pointer to start of linked list */
            record * start;
            /* variables and functions */
            char filename[20];
            int readfile();
            int writefile();
            void cleanup();

        public:
            /* constructor for new list */
            llist();
            /* constructor for list from file (uses readFile) */
            llist(char[]);
            /* destructor (uses writeFile and cleanup) */
            ~llist();

            /* extra credits */
            llist(const llist&);
            llist& operator=(const llist&);
            friend std::ostream& operator<<(std::ostream&, const llist&);

            /* functions */
            int addRecord(int, char[], char[]);
            int findRecord(int);
            void printAllRecords();
            int deleteRecord(int);
    };
#endif

```
