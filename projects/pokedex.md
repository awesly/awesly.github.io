---
layout: project
type: project
image: img/poke2.png
title: "Pokedex Application"
date: Fall 2024
published: true
labels:
  - C++
  - Vim
  - Unix
summary: "A functional Pokedex written in C++ for ICS 212."
---

Another project I completed on my own in ICS 212 at the [University of Hawaii at Manoa Information and Computer Science Dept](https://www.ics.hawaii.edu/) was creating a pokedex application. It was written in C++, using parent and child classes and a main function that accessed the Pokemon's information using maps and vectors. Pokemon is the parent class, and there are currently multiple child pokemon classes. Information about each Pokemon's name, type, and weight can be accessed with the function printData. The code could be expanded to be more robust, with more information on each type of Pokemon, and a detailed user interface to accesss Pokemon by various fields, for example all Pokemon of water type or Pokemon under a certain weight.

Here is some code that illustrates an example of the parent Pokemon class header in C++:

```cpp
#ifndef POKEMON_H
#define POKEMON_H

    #include <string>
    using namespace std;

    /* class definition */
    class Pokemon
    {
        protected:
            string type;
            float weight;
        public:
            Pokemon();
            virtual ~Pokemon();
            virtual void printData()=0; /* pure virtual */
    };

#endif

```

And some code illustrating the implememntation of child Sunflora Pokemon class in C++:

```cpp
#include "Pokemon.h"
#include "Sunflora.h"
#include <string>
#include <iostream>
using namespace std;

/* implement constructor and virtual destructor */
Sunflora::Sunflora()
{
    /* initialize variables */
    type = "grass";
    weight = 18.7;

    cout << "Sunflora Constructor" << endl;
}

Sunflora::~Sunflora()
{
    cout << "Sunflora Destructor" << endl;
}

/* implement printData */
void Sunflora::printData()
{
    cout << "The name of the Pokemon is: Sunflora" << endl;
    cout << "The Pokemon's type is: " << type << endl;
    cout << "The Pokemon's weight is: " << weight << endl;
}
```
And some code illustrating the main function, that defines the ability to check the Pokedex and impliments a use of it:
```cpp
#include "Pokemon.h"
#include "Lotad.h"
#include "Audino.h"
#include "Sunflora.h"
#include <iostream>
#include <vector>
#include <string>
#include <map>
using namespace std;

/* define checkPokedex - calls printData (like toString and println) */
void checkPokedex(Pokemon *pokemon)
{
    /* additional prints for explaining what is going on */
    cout << "checkPokedex was called, and it outputs: " << endl;

    /* print the Pokemon info */
    pokemon->printData();
}

int main()
{
    cout << "\nCreating instances of each Pokemon: ";
    /* create instances stored in pointers */
    Pokemon* lotadP = new Lotad();
    Pokemon* audinoP = new Audino();
    Pokemon* sunfloraP = new Sunflora();

    /* create vector container storing nicknames - lotty, auddy, and sunny */
    vector<string> nicknameVector;
    nicknameVector.push_back("lotty");
    nicknameVector.push_back("auddy");
    nicknameVector.push_back("sunny");

    /* create map container storing pointer by nickname as key */
    map<string, Pokemon*> pokeMap;
    pokeMap["lotty"] = lotadP;
    pokeMap["auddy"] = audinoP;
    pokeMap["sunny"] = sunfloraP;

    /* for loop with iterator, start and end of vector, iterate it */
    for(vector<string>::iterator iter = nicknameVector.begin(); iter != nicknameVector.end(); ++iter)
    {
        /* print line explaining what is going on, call checkPokedex */
        cout << "\nKey used for map is: " << *iter << endl;
        checkPokedex(pokeMap[*iter]);
    }

    cout << "\nDeleting the Pokemon: ";
    /* clean up heap memory */
    delete lotadP;
    delete audinoP;
    delete sunfloraP;
    return 0;
}
```
