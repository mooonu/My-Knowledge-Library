# Repeating blocks

## Theory

Sometimes, you need to repeat a group of statements several times. You can just copypaste the expression. What if you want to repeat it one hundred thousand times? Copypaste is clumsy in this case.

Fortunately for us, Kotlin provides several special statements to repeat blocks of code multiple times. These statements are known as **loops**. They are useful when it comes to repeating multiple statements.

##### Repeat loop

To use the simplest loop, write `repeat(n)` and a sequence of statements in curly braces `{...}`. `n` is an integer that determines how many times these statements are going to be repeated.

```kotlin
repeat(n) {
    // statements
}
```

For example, the program below prints `Hello` three times:

```kotlin
fun main() {
    repeat(3) {
        println("Hello")
    }
}
```

Output:

```kotlin
Hello
Hello
Hello
```

Hint

Kotlin has the opportunity to control the current iteration with the `it` name:

```kotlin
fun main() {
    repeat(3) {
        println(it)
    }
}
```

Output:

```kotlin
0
1
2
```



The code in parentheses is commonly called a "lambda expression". It's a function that doesn't have name and is passed immediately as an expression. You can find more information about lambdas [here](https://hyperskill.org/learn/step/6154).



##### Reading and processing data in a loop

You can read data from the standard input, declare variables and even perform calculations inside the `repeat` statement.

Take a look at this example. The program below reads numbers from the standard input and calculates their sum. The first number is not a part of the sum, it determines the length of the input sequence.

```kotlin
fun main() {    
    val n = readln().toInt()
    var sum = 0
    
    repeat(n) {
        val next = readln().toInt()
        sum += next
    }
    
    println(sum)
}
```

This code reads a length of a number sequence and assigns it to the `n` variable. After that, it creates a variable to store the total sum. The code reads the next number and adds it to the sum exactly `n` times. Then, the loop stops, and the program prints the total sum.

Here is an example of input numbers:

```kotlin
5
40
15
30
25
50
```

Output:

```kotlin
160
```
