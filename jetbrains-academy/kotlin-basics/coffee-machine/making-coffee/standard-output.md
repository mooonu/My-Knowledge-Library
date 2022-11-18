# Standard output

### Printing text

Kotlin has two functions that send data to the standard output: `println` and `print`.

The `println` function (**print line**) displays **a string** followed by **a new line** on the screen. For example, the code snippet below prints four lines:

```kotlin
println("I")
println("know")
println("Kotlin")
println("well.")
```

**Output:**

```java
I
know
Kotlin
well.
```

As you can see, all strings are printed without double quotes.

You can also print an empty line:

```kotlin
println("Kotlin is a modern programming language.")
println() // prints an empty line
println("It is used all over the world!")
```

**Output:**

```java
Kotlin is a modern programming language.

It is used all over the world!
```



The `print` function displays **a value** and places the cursor **after**. Let's look at the example below. This piece of code outputs all strings in a **single line**:

```kotlin
print("I ")
print("know ")
print("Kotlin ")
print("well.")
```

**Output:**

```java
I know Kotlin well.
```



