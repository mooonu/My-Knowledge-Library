# GET



## 주소 노출

- 스프링에서 REST API 를 만들기 위해서 해당 클래스는 REST API 로 동작한다는 것을 알려주는 어노테이션을 작성해야한다.

```kotlin
import org.springframework.web.bind.annotation.RestController

@RestController
class GetApiController {
}
```



- `@RequestMapping()` 특정 주소 노출을 위한 어노테이션 

```kotlin
import org.springframework.web.bind.annotation.RequestMapping
import org.springframework.web.bind.annotation.RestController

@RestController
@RequestMapping("/api") // http://localhost:8080/api
class GetApiController {
}
```



- `@GetMapping()` GET 방식 주소 노출을 위한 어노테이션 (현재 트렌드인 방법)

```kotlin
import org.springframework.web.bind.annotation.GetMapping
import org.springframework.web.bind.annotation.RequestMapping
import org.springframework.web.bind.annotation.RestController

@RestController
@RequestMapping("/api") // http://localhost:8080/api
class GetApiController {
  
    @GetMapping("/hello") // http://localhost:8080/api/hello
    fun hello(): String {
        return "Hello Kotlin"
    }
  
}
```



- `@GetMapping(path = [])` 여러가지 주소를 갖는 방법

```kotlin
import org.springframework.web.bind.annotation.GetMapping
import org.springframework.web.bind.annotation.RequestMapping
import org.springframework.web.bind.annotation.RestController

@RestController
@RequestMapping("/api") // http://localhost:8080/api
class GetApiController {
  
  	// http://localhost:8080/api/both, http://localhost:8080/api/same
    @GetMapping(path = ["/both", "/same"]) 
    fun both(): String {
        return "path 를 사용하면 여러가지 주소를 가질 수 있다"
    }
  
}
```



- `RequestMapping(method = [RequestMethod.GET], path = [])` GET 방식 주소 노출을 위한 어노테이션 (예전에 쓰이던 방법)

HTTP 메소드의 제한 없이 GET, PUT, DELETE, POST 등으로 동작할 수 있기에 제한을 두기 위해서 `method =[]` 을 사용함

```kotlin
import org.springframework.web.bind.annotation.GetMapping
import org.springframework.web.bind.annotation.RequestMapping
import org.springframework.web.bind.annotation.RestController

@RestController
@RequestMapping("/api") // http://localhost:8080/api
class GetApiController {
  
    @RequestMapping(method = [RequestMethod.GET], path = ["/request-mapping"])
    fun requestMapping(): String {
        return "request-mapping"
    }
  
}
```



## PathVariable

- `@PathVariable` 을 활용한 주소 노출

```kotlin
@RestController
@RequestMapping("/api") // http://localhost:8080/api
class GetApiController {

  	// http://localhost:8080/api/get-mapping/path-variable/moonu
    @GetMapping("/get-mapping/path-variable/{name}") 
    fun pathVariable(@PathVariable name: String): String {
        println(name)
        return name
    }
}
```



- `@PathVariable`  을 여러개 받는 방법

```kotlin
@RestController
@RequestMapping("/api") // http://localhost:8080/api
class GetApiController {

  	// http://localhost:8080/api/get-mapping/path-variable/moonu/24
    @GetMapping("/get-mapping/path-variable/{name}/{age}") 
    fun pathVariable(@PathVariable name: String, @PathVariable age: Int): String {
        println("$name , $age")
        return name + " " + age 
    }
}
```



- 코딩하다  `@PathVariable` 의 변수와 함수의 지역 변수가 겹치는 경우

 `@PathVariable` 의 변수의 이름이 같지 않을 때 또는 맞출 수 없을 때 `value = ` 또는 `name = ` 속성을 사용하여 path 를 맞춰준다.

```kotlin
@RestController
@RequestMapping("/api") // http://localhost:8080/api
class GetApiController {

    @GetMapping("/get-mapping/path-variable/{name}/{age}") 
    fun pathVariable(@PathVariable(value = "name") _name: String, @PathVariable age: Int): String {
      	val name = "kotlin" 
      
        println("$_name , $age")
        return _name + " " + age 
    }
}
```



## Query Parameter

- `@RequestParam` 어노테이션

마찬가지로 변수의 이름이 같거나 또는 맞출 수 없을 때 `value = ` 또는 `name = ` 속성을 사용하여 맞춰준다.

```kotlin
@RestController
@RequestMapping("/api")
class GetApiController {

  	// http://localhost:8080/api/get-mapping/query-param?name=moonu&age=24
    @GetMapping("/get-mapping/query-param") 
    fun queryParam(
        @RequestParam name: String,
        @RequestParam age: Int,
    ): String {
        println("$name , $age")
        return name + " " + age
    }
}
```



- 여러 값을 받아야 할 때 한번에 받아서 처리하는 방법

일일이 `@RequestParam` 을 추가하기 번거롭기에 **객체**로 받아 처리한다

1. 클래스 디자인

```kotlin
data class UserRequest(
    var name: String? = null,
    var age: Int? = null,
    var email: String? = null,
    var address: String? = null,
)
```



2. 클래스 객체 사용 ( class 의 속성에 매칭됨 )

```kotlin
@RestController
@RequestMapping("/api") // http://localhost:8080/api
class GetApiController {

		@GetMapping("/get-mapping/query-param/object")
    fun queryParamObject(userRequest: UserRequest ): UserRequest {
        println(userRequest)
        return userRequest
    }
}
```
