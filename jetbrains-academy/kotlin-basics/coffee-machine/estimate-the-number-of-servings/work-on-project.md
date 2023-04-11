# Work on project

**Description**

A real coffee machine doesn't have an infinite supply of water, milk, or coffee beans. And if you input a really big number, it's almost certain that a real coffee machine wouldn't have the supplies needed to make all that coffee for you.

In this stage, you need to improve the previous program. Now you will check amounts of water, milk, and coffee beans available in your coffee machine at the moment.

**Objectives**

Write a program that does the following:

1. It requests the amounts of water, milk, and coffee beans available at the moment, and then asks for the number of cups a user needs.
2. If the coffee machine has enough supplies to make the specified amount of coffee, the program should print `"Yes, I can make that amount of coffee"`.
3. If the coffee machine can make more than that, the program should output `"Yes, I can make that amount of coffee (and even N more than that)"`, where _N_ is the number of additional cups of coffee that the coffee machine can make.
4. If the amount of given resources is not enough to make the specified amount of coffee, the program should output `"No, I can make only N cups of coffee"`.

Like in the previous stage, the coffee machine needs _200 ml_ of water, _50 ml_ of milk, and _15 g_ of coffee beans to make one cup of coffee.

**Examples**

The greater-than symbol followed by a space (`>` ) represents the user input. Note that it's not part of the input.

**Example 1:**

```
Write how many ml of water the coffee machine has:
> 300
Write how many ml of milk the coffee machine has:
> 65
Write how many grams of coffee beans the coffee machine has:
> 100
Write how many cups of coffee you will need:
> 1
Yes, I can make that amount of coffee
```

**Example 2:**

```
Write how many ml of water the coffee machine has:
> 500
Write how many ml of milk the coffee machine has:
> 250
Write how many grams of coffee beans the coffee machine has:
> 200
Write how many cups of coffee you will need:
> 10
No, I can make only 2 cups of coffee
```

**Example 3:**

```
Write how many ml of water the coffee machine has:
> 1550
Write how many ml of milk the coffee machine has:
> 299
Write how many grams of coffee beans the coffee machine has:
> 300
Write how many cups of coffee you will need:
> 3
Yes, I can make that amount of coffee (and even 2 more than that)
```

**Example 4:**

```
Write how many ml of water the coffee machine has:
> 0
Write how many ml of milk the coffee machine has:
> 0
Write how many grams of coffee beans the coffee machine has:
> 0
Write how many cups of coffee you will need:
> 1
No, I can make only 0 cups of coffee
```

**Example 5:**

```
Write how many ml of water the coffee machine has:
> 0
Write how many ml of milk the coffee machine has:
> 0
Write how many grams of coffee beans the coffee machine has:
> 0
Write how many cups of coffee you will need:
> 0
Yes, I can make that amount of coffee 
```

**Example 6:**

```
Write how many ml of water the coffee machine has:
> 200
Write how many ml of milk the coffee machine has:
> 50
Write how many grams of coffee beans the coffee machine has:
> 15
Write how many cups of coffee you will need:
> 0
Yes, I can make that amount of coffee (and even 1 more than that)
```

해당 섹션과 이전 섹션에서 배운 내용을 기반으로 작성함 따라서 함수나 클래스가 존재하지 않음

My code:

```kotlin
package machine

/** 커피 한 잔에는 water 200, milk 50, beans 15 */
fun main() {

    println("Write how many ml of water the coffee machine has:")
    val hasWater: Int = readln().toInt()

    println("Write how many ml of milk the coffee machine has:")
    val hasMilk: Int = readln().toInt()

    println("Write how many grams of coffee beans the coffee machine has:")
    val hasBeans: Int = readln().toInt()

    println("Write how many cups of coffee you will need:")
    val userWantCoffee: Int = readln().toInt()

    val needWater = 200 * userWantCoffee
    val needMilk = 50 * userWantCoffee
    val needBeans = 15 * userWantCoffee

    val calcWater: Int = hasWater / needWater
    val calcMilk: Int = hasMilk / needMilk
    val calcBeans: Int = hasBeans / needBeans

    // 커피 머신이 보유한 재료를 토대로 만들 수 있는 커피의 개수
    val minWater = hasWater / 200
    val minMilk = hasMilk / 50
    val minBeans = hasBeans / 15

    val minMakeCoffee = if (minWater < minBeans) {
        if (minWater < minMilk) minWater else minMilk
    } else {
        if (minMilk < minBeans) minMilk else minBeans
    }

    // 손님의 요구사항을 들어줄 수 있는지 체크
    val successMakeCoffee = hasWater >= needWater && hasMilk >= needMilk && hasBeans >= needBeans

    // 만들 수 있다면 몇개나 더?
    val moreCoffee = if (calcWater < calcBeans) {
        if (calcWater < calcMilk) calcWater else calcMilk
    } else {
        if (calcMilk < calcBeans) calcMilk else calcBeans
    }

    val result = if (successMakeCoffee) {
        if (moreCoffee == 1) "Yes, I can make that amount of coffee" else "Yes, I can make that amount of coffee (and even ${moreCoffee-1} more than that)"
    } else {
        if (userWantCoffee == 0) "Yes, I can make that amount of coffee" else "No, I can make only $minMakeCoffee cups of coffee"
    }

    println(result)
}
```
