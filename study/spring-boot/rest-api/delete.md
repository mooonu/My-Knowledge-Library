# DELETE

- 방법

```kotlin
    @DeleteMapping(path = ["/delete-mapping"])
    fun deleteMapping(
        @RequestParam name: String,
        @RequestParam age: Int,
    ): String {
        println(name)
        println(age)
        return "$name $age"
    }
```

