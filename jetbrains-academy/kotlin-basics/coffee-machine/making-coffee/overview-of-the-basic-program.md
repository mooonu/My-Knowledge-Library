# Overview of the basic program

### ****

### **Hello, World**

```kotlin
fun main() {
    println("Hello, Kotlin!")
}
// Hello, Kotlin!
```

### **Basic terminology**

After you have seen the result, let's learn the basic terminology and then try to understand our program.

* A **program** is **** a sequence of instructions (called statements), which are executed one after another in a predictable manner. Sequential flow is the most common and straightforward situation when statements are executed in the order they are written, i.e., from top to bottom, one after another;
* A **statement** (or a **programming statement**) is a single command to be executed (like printing a text);
* An **expression** is a piece of code that produces a single value (for example, 2\*2 is an expression);
* A **block** is a group of zero or more statements enclosed in a pair of curly braces `{...}`; our program consists of a single block;
* A **keyword** is a word that has a special meaning in the programming language. Names of keywords can't be changed;
* An **identifier** (or a **name**) is a word written by the programmer to identify something;
* A **comment** is a piece of text that is ignored when executing the program – it just explains a part of the code. Comments start with `//`;
* **Whitespace** is a blank area, a tab, or a newline; it is used to separate words in the program and to improve readability.

### **The Hello World program under a microscope**

The **Hello World** program illustrates the use of the basic elements of any Kotlin program. Right now, we will consider only the most important ones.

**The entry point.** The keyword `fun` defines a function that contains a piece of code to execute. This function has a special name `main`. It indicates the entry point of a Kotlin program. The function has a body enclosed in braces `{...}`.

```kotlin
fun main() { 
    // ...
}
```

We will discuss the functions later. The name of this function should always be the same: `main`. If you name it `Main` or `MAIN` or something else, the program will not start.

****

The body of this function consists of programming statements that define what the program is to do. Our program prints the string **"Hello, World!"** using the following statement:

```java
println("Hello, World!")
```

### Programs with multiple statements

As a rule, a program contains multiple statements. You should start a new line to write each statement. For example, the program below has two statements:

```kotlin
fun main() {
    println("Hello")
    println("World")
}
```

If you run the program, you will see that it displays this:

```kotlin
Hello
World
```

****

****

****

****

****
