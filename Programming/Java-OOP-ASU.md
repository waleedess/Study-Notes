
# Properties of Java

- Object-oriented: like C#, not like C++ which i can run anything thats in the main function
- Interpreted: Java is compiled line by line 
- Portable: Any device that has JVM - Java VM, can use Java
- Secure & robust: No memory leaks -*theortically*- due to garbage collector
- Multi-threaded: Can run multiple proccess
- Garbage collected: Like C# & unlike C++ & C; no need to delete the pointer manually as memory is allocated dynamically
- **No** support for multiple inheritance
  
---
# Object Oriented Thinking

- Each object contains data, in the form of fields often known as attributes; and actions to work on that data, in the form of procedures, often known as methods
- Objects constitute the building blocks of the program
- Objects interact with each other and exchange data
- Classes can form a hierarchy

---

# Principles of OOP

1. Encapsulation
2. Abstraction 
3. Inheritance
4. Polymorphism

---
##### 1. Encapsulation

The process of **combining data and methods** into a single unit called a **class**
- Keeps data safe as it exposes only necessary data
- Can be controlled via **access modifiers**; `private`, `protected` and `public`
  
---
##### 2. Abstraction

Hides unnecessary details from the user to decrease complexity
- Achieved by using classes
  
---
##### 3. Inheritance 

Creates hierarchy of related classes and allows code re-usability

---
##### 4. Polymorphism

Means having many forms of the same concept with different meanings in different context

Has 2 forms
- **Overloading**: same method name with different parameters (number or datatype)
- **Overriding**: overrides an inherited method by creating new own method that must match the one in super class in terms of (name, parameters and return type)
 
---
# Syntax wise

### Basic Info

- Statements are terminated by `;` 
- Java **filename must match the class name** 
- Can be **compiled** using `javac CLASSNAME.java` and **run** using `java CLASSNAME` and those are not needed while using and IDE
- **Packages:**
	- A group of related classes used to guarantee the uniqueness of class names in the package 
	- Packages can be nested
	- Sandard Java packages are `java.*` & `javax.*`
	- 


---
### Arrays
 
- Array size decalaration
		1. `<datatype>[] <arrname> = new <datatype>[5];` => **Non**-initialized
		2. `<datatype>[] <arrname> = new <datatype>[]{1,2,3,4,5};` => **Intialized** 
- Holds references only, **no actual values**
- Array **unassigned** elements set as **Null**
- Arrays have `arrname.length` to be used as a call to array size or the size hardcoded

---
### Loops

- Basic for loop is just the same as C++
- **foreach** loop:
	- `for(<datatype> <item> : <arrname>){.
		  `System.out.println(<item>)`
	  `.}`
	- Think of `item` as `i` in basic for loops
- `break` -> Ends the whole loop
- `continue` -> Ends the current iteration and start a new one keeping the loop going

---

### Classes & Objects 

1. Class 
	- Constitutes the blueprint of a specific type
		- **Do not reserve memory**
	- Contains data members/fields and methods to work on them
		- Have various levels of hiding to protect its own fields and methods
	- Can contain inner classes and used to create hierarchy
2. Object
	- An instance of a specific class
	- **Reserves memory** in the system
	- Can be instantiated using the keyword: `new`
		- If created but not instantiated => **Null**
3. UML - Unified Modeling Language
	- Visualises classes, objects and relationships among system classes 
	- **Class Diagram**: is a rectangular UML divided into 3 sections:![[Pasted image 20260924030457.png|238]]
		1. Class Name
		2. Attribures/Fields
		3. Operations/Methods
	- UML diagrams mentions access modifiers as shown represented in
		1. `+` => **Public**
		2. `#` => **Protected**
		3. `-` => **Private**
	- UML Relationships can be inheritance(hierarchial) or association
		- Represented by arrowheads ![[Pasted image 20260924030850.png|393]]

###### Class Syntax

`AMod NAMod DATATYPE CLASSNAME{`
`AMod NAMod DATATYPE FIELD1;` -> **Fields**: variables that represent data that each obj hold
`AMod NAMod DATATYPE FIELDn;`
`AMod CLASSNAME(PARList){}` -> **Constructors**: special method that runs **automatically** and only when you create a new object with `new`. Its job is to **initialize the object's fields** and **only accepts access modifiers**. Can make more than one object but should be different, But each class should has at least one, If not the compiler will make a default one. Constructors **do not have a return type**
`AMod NAMod RETURNTYPE METHOD1(PARList){}` -> Basic method
`AMod NAMod RETURNTYPE METHODn(PARList){}`


###### New Object Instantiation

1. **Lone Objects**
	`CLASSNAME OBJName = new CLASSNAME(PARList)`;
2. **Array of Objects**
	`DATATYPE[] VARName = new DATATYPE[SIZE];` => Declares the array, 10 empty (Null) slots
	`for (int i=0; i<SIZE; i++) {` => Instantiates each array member
	`VARName[i] = new DATATYPE();`
	`}`

### Access Modifiers & Non-Access Modifiers

###### Access Modififers 

- Control who can **see/use**
- Options:
	1. `Public`: accessible form anywhere
	2. `Private`: accessible only within the same 
	3. `Protected`: accessible within the same package + subclasses
	4. Default/NoKeyword: accessible only within the same package (Package-local)

###### Non-Access Modifiers

- Control **behaviour**, **Not visibility**
- Options:
	1. `static`: belongs to the class itself, not individual objects
	2. `final`: can not be changed/overriden/extended
	3. `abstract`: no full implementation; must be completed by a subclass
