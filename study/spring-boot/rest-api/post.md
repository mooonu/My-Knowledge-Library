# POST

POST 는 body 에 내용을 넣어서 요청할 수 있다.

- 현재 사용하는 방법

```kotlin
		@PostMapping("/post-mapping")
    fun postMapping(): String {
        return "post-mapping" // request body 가 빈 상태로 요청이 되면 plain text 로 리턴
    }
```



- 예전에 사용하던 방법

```kotlin
    @RequestMapping(method = [RequestMethod.POST], path = ["/request-mapping"])
    fun requestMapping(): String {
        return "request-mapping"
    }
```



## 스프링의 object mapper

json -> object 
object -> json 으로 변환해주는 라이브러리

- 예제

```kotlin
    @PostMapping("post-mapping/object")
    fun postMappingObject(@RequestBody userRequest: UserRequest): UserRequest {
        // 요청이 들어올 때는 json -> object 로 변환
        println(userRequest)
        return userRequest // 리턴할 때는 object -> json 으로 변환
    }
```

> Postman 을 이용해 body 에 내용을 담아 요청하는 방법은
> Body - raw - JSON 선택 후 내용 작성



## 현업에서 일어날 수 있는 일

1. **Naming Convention 이 다르다**
   대부분의 REST API json 의 형태는 snake_case 지만 우리는 변수를 작성할 때 camelCase 로 작성하므로
   매칭이 되지 않아 데이터를 받을 수 없는 경우가 있음
   따라서 이를 해결하려면 object mapper 에게 규칙을 지정해줘야함

   - `@JsonProperty` 어노테이션

   ```kotlin
   data class UserRequest(
       var name: String? = null,
       var age: Int? = null,
       var email: String? = null,
       var address: String? = null,
     
     	@JsonProperty("phone_number")
     	var phoneNumber: String? = null,
   )
   ```



2. **API 를 다양한 곳에 연동한다**
   Request Response 에 대한 모델을 만들텐데 회사마다 규칙이 다름 ( **물론 회사들의 정책은 정해져 있음** snake or camel .. etc )
   따라서 post body 에는 여러가지가 들어가는데 그때 마다 변수위에 어노테이션을 작성하기엔 너무 힘드니까 해당 회사와 연동을 할 때 클래스에 타입을 지정할 수 있다.

   - `@JsonNaming(PropertyNamingStrategy.SnakeCaseStrategy::class)` 어노테이션
     해당 클래스는 snake_case 로 작동할 거야 라는 것을 알려줌

     ```kotlin
     이거 Deprecated 되버렸음 ..
     ```

     
