# zuzeelik

[![Join the chat at https://gitter.im/Mr-Kumar-Abhishek/zuzeelik](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/Mr-Kumar-Abhishek/zuzeelik?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) [![Build Status](https://travis-ci.org/Mr-Kumar-Abhishek/zuzeelik.svg?branch=master)](https://travis-ci.org/Mr-Kumar-Abhishek/zuzeelik) [![Stories in Ready](https://badge.waffle.io/Mr-Kumar-Abhishek/zuzeelik.png?label=ready&title=Ready)](https://waffle.io/Mr-Kumar-Abhishek/zuzeelik)

A programming language similar to [Lisp](https://en.wikipedia.org/wiki/Lisp_%28programming_language%29). [LispStrawMen](http://c2.com/cgi/wiki?LispStrawMen), this is not exactly a Lisp Dialect. 

[![Throughput Graph](https://graphs.waffle.io/Mr-Kumar-Abhishek/zuzeelik/throughput.svg)](https://waffle.io/Mr-Kumar-Abhishek/zuzeelik/metrics)

#### Cloning:

Remember to get the submodules while cloning.
```
git clone --recursive <git repository url here>
```
Already have a copy of the repository locally without submodules ? Get them with:
```
git submodule update --init
```

#### Compilation:

* **For Linux:**
Compile using c99. Libraries that are needed to be linked while compilation are *math* library and *editline* library.

``` 
cc -std=c99 -Wall zuzeelik.c mpc/mpc.c -ledit -lm -o zuzeelik
```
Or this could be simply done by using make.

```
make
```

#### Syntax and operators:

Zuzeelik uses *sym-expressions*, which is similar to [s-expressions](https://en.wikipedia.org/wiki/S-expression), however internally a variable sized array is used to represent it. Use [polish notation](http://en.wikipedia.org/wiki/Polish_notation) with operators rather than [infix notation](https://en.wikipedia.org/wiki/Infix_notation), such as:

|     Infix Notation    |      Polish Notation     |
|:---------------------:|:------------------------:|
|     `1 + 4 + 9`       |       `+ 1 4 9`       
|   `8 - ( 5 * 6) `     |   `- 8 (* 5 6)`        
| `(10 / 5) * (10 / 2)` |  `* (/ 10 5) ( / 10 2)`   


Currently, it supports following symbolic and textual operators:


|     Operator Name     | Symbolic operator syntax | Textual operator syntax
|:---------------------:|:------------------------:|:----------------------:
|        Addition       |       `( + 1 4 9 )`      |     `( add 1 4 9 )`    
|      Subtraction      |       `( - 23 4 9 )`     |    `( sub  23 4 9 )`
|     Multiplication    |       `(* 23 12 9 )`     |    `( mul 23 12 9 )`     
|       Division        |       `( / 8 4 2  )`     |    `( div  8 4 2  )`  
|        Modulo         |       `( % 64 8 4 )`     |    `( mod  64 8 4 )`   
|         max           |                          |    `( max 23 34 55)`  
|         min           |                          |    `( min 23 34 55)` 
|         pow           |        `( ^ 4 3 )`       |      `( pow 4 3 )`  

##### Examples:
* input: 
 ```
zuzeelik> % 5.4 3
 ```
 
* output:
```
Abstract Syntax Tree:

> 
  regex 
  expression|symbol|char:1:1 '%'
  expression|number|regex:1:3 '5.4'
  expression|number|regex:1:7 '3'
  regex 


Total number of nodes: 6

Received input: (% 5.400000 3.000000)
Evaluated output: 2.400000


```
