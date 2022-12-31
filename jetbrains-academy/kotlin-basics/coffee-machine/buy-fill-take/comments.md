# Comments

## End-of-line comments

컴파일러는 `//` 에서 줄 끝까지의 텍스트를 무시합니다.

```kotlin
fun main() {
    // The line below will be ignored
    // println("Hello, World")

    // This prints the string "Hello, Kotlin"
    println("Hello, Kotlin")  // Here can be any comment
    /// Valid multiline comment
}
```

> 혹시 알고 계신가요? 대부분의 에디터는 `Ctrl / or cmd /` 를 눌러서 줄을 주석 처리할 수 있습니다.



## Multi-line comments

컴파일러는 `/*` 와 `*/` 사이의 텍스트를 무시합니다. 한 줄이나 여러줄을 주석 처리할 수 있습니다:

```kotlin
fun main() {
    /* This is a single-line comment */
    /*  This is an example of
        a multi-line comment */

    /*** Valid multiline comment
        println("Hello")
        println("World")
    **/
}
```

다른 주석 안에 주석을 넣을 수도 있습니다. 중첩된 주석을 작성할 때는 `/*` 기호와 `*/` 가 쌍을 이루는지 확인해야합니다.

```kotlin
fun main() {
    /*
    System.out.println("Hello")  // print "Hello"
    System.out.println("Kotlin") /* print "Kotlin" */
    */
}
```

## Documentation comments (doc comments)

컴파일러는 multi-line 주석안의 모든 텍스트를 무시하는 것 처럼 `/**` 와 `*/` 사이의 텍스트를 무시합니다. 이건 **documentation comments**(doc comments) 라고 합니다. 문서는 다른 사람들이 당신의 코드가 어떤 일을 하는지 이해할 수 있도록 도와주는 텍스트입니다. 이 기능을 사용하여 당신의 소스 코드에 대한 문서를 자동으로 생성할 수 있습니다.

일반적으로 이러한 주석은 각 프로그램 요소의 위에 배치됩니다. 또한 이 경우  `@param`, `@return` 등과 같은 특수 레이블도 사용할 수 있습니다.

예시:

```kotlin
/**
 * The `main` function accepts string arguments from outside.
 *
 * @param args arguments from the command line.
 */
fun main(args: Array<String>) {
    // do nothing
}
```

![doc comments](https://user-images.githubusercontent.com/86511086/209951743-ffbe7b3f-f265-4edf-8e14-75e85f099fd2.png)



만약 documentation comments 를 이해하지 못했더라도 두려워하지마세요. 나중에 더 자세히 살펴볼 것입니다.
