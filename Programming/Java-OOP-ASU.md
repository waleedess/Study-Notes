
# Principles of OOP

1. Encapsulation
2. Abstraction 
3. Inheritance
4. Polymorphism
---
##### 1. Encapsulation

The process of ==combining data and methods== into a single unit called a ==class==
- Keeps data safe as it exposes only necessary data
- Can be controlled via ==access modifiers==; `private`, `protected` and `public`
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

- Terminated by `;` 

 **Arrays**:
- Array size decalaration
		1. `<datatype>[] <arrname> = new <datatype>[5];`
		2. `<datatype>[] <arrname> = new <datatype>[]{1,2,3,4,5};`
- Array unassigned elements set as zeros
- Arrays have `arrname.length` to be used as a call to array size or the size hardcoded

**Loops**
- Basic for loop is just the same as C++
- ==foreach== loop:
	- `for(<datatype> num : <arrname>){...}`
	- `num` Catches every element in the array and do for each 