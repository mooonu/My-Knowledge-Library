# Values and variables

### What is a variable?

A variable is a storage for a value, which can be a string, a number, or something else. Every variable has a **name** (or an **identifier**) to distinguish it from other variables. You can access a value by the name of the variable.

> 변수는 문자열, 숫자, 기타 항목이 될 수 있는 값의 저장소입니다.\
> 모든 변수는 다른 변수와 구별하기 위한 **이름(식별자)**이 있습니다.\
> 변수 이름으로 값에 접근할 수 있습니다.

### Declaring variables

Before you can start using a variable, you must declare it. To declare a variable, Kotlin provides two keywords:

* `val` (for _value_) declares an **immutable variable** (just a **named value** or a **constant**), which cannot be changed after it has been initialized (this is actually not entirely true, we will discuss this issue in more detail later);
* `var` (for _variable_) declares a **mutable variable**, which can be changed (as many times as needed).

\# Both `val` and `var` keywords provide you a variable!

> 변수를 사용하기 이전에 먼저 변수 선언을 해줘야 합니다. Kotlin은 변수를 선언할 때  두 가지 키워드를 제공하는데요.
>
> * **val** (for value) 는 초기화된 후에는 변경할 수 없는 **불변 변수( constant )일 때 선언**합니다. (실제로는 사실이 아닙니다, 나중에 이 문제에 대해 자세히 설명하겠습니다. (...?)
> * **var** (for variable) 는 변경할 수 있는 **가변 변수를 선언**합니다.
>
> \# val 와 var 모두 변수를 제공합니다!



When you declare a variable, you must add its name after one of these two keywords. Be careful: the name of a variable cannot start with a digit. Usually, it starts with a letter. You should choose meaningful and readable names for variables to make your code easy to understand.

To assign a certain value to a variable, we should use the assignment operator `=`.

Let's declare an immutable variable named `language` and initialize it with the string `"Kotlin"`.

```kotlin
val language = "Kotlin" 
println(language) // Kotlin
```

> 변수를 선언할 때, 이 키워드 중 하나 뒤에 이름을 추가해야 합니다.\
> 조심하세요: 변수 명의 시작은 숫자가 될 수 없습니다. 보통은 문자로 시작합니다.\
> 당신의 코드를 쉽게 이해할 수 있도록 **읽기 쉽고 의미 있는 변수 명을 지어야 합니다.**
>
> 변수에 특정 값을 할당하려면 `=` 을 사용하면 됩니다.
>
> 이제 변하지 않는 변수 `language` 를 선언하고 그 값을 문자열 `"Kotlin"` 으로 초기화 해봅시다.



This variable cannot be modified after it has been initialized because it was declared as `val`.

Names are case-sensitive: `language` is not the same as `Language`.

> 이 변수는 `val` 으로 선언되었기 때문에 초기화 후 더 이상 수정할 수 없습니다.
>
> 추가로 `language` 와 `Language` 는 전혀 다릅니다 대소문자를 구분하거든요.&#x20;



Now, let's declare a mutable variable named `dayOfWeek` and print its value before and after changing it.

In the example above, we declared a variable named `dayOfWeek` and initialized it with the value `"Monday"`. Then we accessed the value by the variable name and printed it. After that, we changed the variable's value to `"Tuesday"` and printed this new value.

```kotlin
var dayOfWeek = "Monday"
println(dayOfWeek) // prints Monday

dayOfWeek = "Tuesday"
println(dayOfWeek) // prints Tuesday
```

You do not need to declare a variable again to change its value. Just assign a new value to it using the `=` operator.

> 이제 변경할 수 있는 변수인 `dayOfWeek` 를 선언하고 값 변경 전과 변경 후를 출력해봅시다.
>
> 위 예시를 보면, 우리는 `dayOfWeek` 이름을 가진 변수를 선언했고 `"Monday"` 로 값을 초기화 했습니다. 그다음 변수 이름으로 값에 접근하여 출력했습니다. 이후에는 값을 `"Tuesday"` 로 변경했고 이 새로운 값을 출력했습니다.
>
> 변수의 값을 바꿀 때 다시 선언할 필요 없이 `=` 을 사용하여 새로운  값을 할당하면 됩니다.



It is also possible to declare and initialize a variable with the value of another variable:

```kotlin
val cost = 3
val costOfCoffee = cost
println(costOfCoffee) // prints 3
```

> 다른 변수의 값을 사용하여 변수를 선언하고 초기화할 수도 있습니다.

### Storing different types of values

We've already mentioned that variables can store different types of values: strings, numbers, characters, and other data types, which we will encounter later.

Let's declare three immutable variables to store a number, a string, and a character and then print their values.

```kotlin
val ten = 10
val greeting = "Hello"
val firstLetter = 'A'

println(ten) // prints 10
println(greeting) // prints Hello
println(firstLetter) // prints A
```

> 변수는 문자열, 숫자, 문자 및 기타 데이터 유형과 같은 다양한 유형의 값을 저장할 수 있음을 이미 언급했습니다.
>
> 이제 불변 변수 세 가지에 각각 숫자, 문자열, 문자를 저장하고 그 값들을 출력해봅시다.



There is one restriction for mutable variables (the ones declared with the keyword `var`), though. When reassigning their values, you can only use new values of the **same type** as the initial one. So, the piece of code below is not correct:

```kotlin
var number = 10
number = 11 // ok
number = "twelve" // an error here!
```

Please remember this restriction!

> 가변 변수에는 한 가지 제약이 걸려있는데요, 다시 값을 할당할 때 **초기값과 같은 타입의 값만** 사용이 가능합니다. 따라서 아래 코드는 틀렸습니다: ( "twelve" )
>
> **이 제약을 꼭 기억하세요!**







