# Work on project

**Description**

Let's simulate an actual coffee machine! What do we need for that? This coffee machine will have a limited supply of water, milk, coffee beans, and disposable cups. Also, it will calculate how much money it gets for selling coffee.

There are several options for the coffee machine we want you to implement: first, it should sell coffee. It can make different types of coffee: espresso, latte, and cappuccino. Of course, each variety requires a different amount of supplies, however, in any case, you will need only one disposable cup for a drink. Second, the coffee machine must get replenished by a special worker. Third, another special worker should be able to take out money from the coffee machine.

**Objectives**

Write a program that offers to buy one cup of coffee or to fill the supplies or to take its money out. Note that the program is supposed to do one of the mentioned actions at a time. It should also calculate the amounts of remaining ingredients and how much money is left. Display the quantity of supplies before and after purchase.

1. First, your program reads one option from the standard input, which can be `"buy"`, `"fill"`, `"take"`. If a user wants to buy some coffee, the input is `"buy"`. If a special worker thinks that it is time to fill out all the supplies for the coffee machine, the input line will be `"fill"`. If another special worker decides that it is time to take out the money from the coffee machine, you'll get the input `"take"`.
2.  If the user writes

    ```
    "buy"
    ```

    then they must choose one of three types of coffee that the coffee machine can make: espresso, latte, or cappuccino.

    * For one espresso, the coffee machine needs _250 ml_ of water and _16 g_ of coffee beans. It costs _$4_.
    * For a latte, the coffee machine needs _350 ml_ of water, _75 ml_ of milk, and _20 g_ of coffee beans. It costs _$7_.
    * And for a cappuccino, the coffee machine needs _200 ml_ of water, _100 ml_ of milk, and _12 g_ of coffee beans. It costs _$6_.
3. If the user writes `"fill"`, the program should ask them how much water, milk, coffee and how many disposable cups they want to add into the coffee machine.
4. If the user writes `"take"` the program should give all the money that it earned from selling coffee.

At the moment, the coffee machine has _$550_, _400 ml_ of water, _540 ml_ of milk, _120 g_ of coffee beans, and _9_ disposable cups.

To sum up, your program should print the coffee machine's state, process one query from the user, as well as print the coffee machine's state after that. Try to use functions for implementing every action that the coffee machine can do.

**Examples**

An espresso should be number _1_ in the list, a latte number _2_, and a cappuccino number _3_. Options are named as `"buy"`, `"fill"`, `"take"`.

The greater-than symbol followed by a space (`>` ) represents the user input. Note that it's not part of the input.

**Example 1:**

```
The coffee machine has:
400 ml of water
540 ml of milk
120 g of coffee beans
9 disposable cups
$550 of money

Write action (buy, fill, take): 
> buy
What do you want to buy? 1 - espresso, 2 - latte, 3 - cappuccino: 
> 3

The coffee machine has:
200 ml of water
440 ml of milk
108 g of coffee beans
8 disposable cups
$556 of money
```

**Example 2:**

```
The coffee machine has:
400 ml of water
540 ml of milk
120 g of coffee beans
9 disposable cups
$550 of money

Write action (buy, fill, take): 
> fill
Write how many ml of water you want to add: 
> 2000
Write how many ml of milk you want to add: 
> 500
Write how many grams of coffee beans you want to add: 
> 100
Write how many disposable cups you want to add: 
> 10

The coffee machine has:
2400 ml of water
1040 ml of milk
220 g of coffee beans
19 disposable cups
$550 of money
```

**Example 3:**

```
The coffee machine has:
400 ml of water
540 ml of milk
120 g of coffee beans
9 disposable cups
$550 of money

Write action (buy, fill, take): 
> take
I gave you $550

The coffee machine has:
400 ml of water
540 ml of milk
120 g of coffee beans
9 disposable cups
$0 of money
```

mycode:

```kotlin
package machine

fun main() {
    welcomeMessage()
    println()
    println("Write action (buy, fill, take):")

    when (readln()) {
        "buy" -> {
            println("what do you want to buy? 1 - espresso, 2 - latte, 3 - cappuccino:")
            val coffee = readln().toInt()
            println()
            buyCoffee(coffee)
        }
        "fill" -> {
            println("Write how many ml of water you want to add:")
            val fillWater = readln().toInt()
            println("Write how many ml of milk you want to add:")
            val fillMilk = readln().toInt()
            println("Write how many grams of coffee beans you want to add:")
            val fillBeans = readln().toInt()
            println("Write how many disposable cups you want to add:")
            val fillCups = readln().toInt()
            println()
            fillCoffee(fillWater, fillMilk, fillBeans, fillCups)
        }
        "take" -> {
            println()
            takeCoffee()
        }
    }

}

fun welcomeMessage() {
    val hasWater: Int = 400
    val hasMilk: Int = 540
    val hasBeans: Int = 120
    val hasCups: Int = 9
    val hasMoney: Int = 550

    val welcomeString = """
        The coffee machine has:
        $hasWater ml of water
        $hasMilk ml of milk
        $hasBeans g of coffee beans
        $hasCups disposable cups
        $$hasMoney of money
    """.trimIndent()

    println(welcomeString)
}
fun buyCoffee(coffee: Int) {
    val hasWater: Int = 400
    val hasMilk: Int = 540
    val hasBeans: Int = 120
    val hasCups: Int = 9
    val hasMoney: Int = 550

    val result = when (coffee) {
        1 -> {
            """
                The coffee machine has:
                ${hasWater-250} ml of water
                $hasMilk ml of milk
                ${hasBeans-16} g of coffee beans
                ${hasCups-1} disposable cups
                $${hasMoney+4} of money
            """.trimIndent()
        }
        2 -> {
            """
                The coffee machine has:
                ${hasWater-350} ml of water
                ${hasMilk-75} ml of milk
                ${hasBeans-20} g of coffee beans
                ${hasCups-1} disposable cups
                $${hasMoney+7} of money
            """.trimIndent()
        }
        3 -> {
            """
                The coffee machine has:
                ${hasWater-200} ml of water
                ${hasMilk-100} ml of milk
                ${hasBeans-12} g of coffee beans
                ${hasCups-1} disposable cups
                $${hasMoney+6} of money
            """.trimIndent()
        }
        else -> "Out of Scope"
    }
    println(result)
}
fun fillCoffee(water: Int, milk: Int, beans: Int, cups: Int) {
    val hasWater: Int = 400
    val hasMilk: Int = 540
    val hasBeans: Int = 120
    val hasCups: Int = 9
    val hasMoney: Int = 550

    val fillString = """
                The coffee machine has:
                ${hasWater + water} ml of water
                ${hasMilk + milk} ml of milk
                ${hasBeans + beans} g of coffee beans
                ${hasCups + cups} disposable cups
                $${hasMoney} of money
            """.trimIndent()

    println(fillString)
}
fun takeCoffee() {
    val hasWater: Int = 400
    val hasMilk: Int = 540
    val hasBeans: Int = 120
    val hasCups: Int = 9
    val hasMoney: Int = 550

    println("I gave you $hasMoney")

    val fillString = """
                The coffee machine has:
                ${hasWater} ml of water
                ${hasMilk} ml of milk
                ${hasBeans} g of coffee beans
                ${hasCups} disposable cups
                $${hasMoney - hasMoney} of money
            """.trimIndent()

    println(fillString)
}
```
