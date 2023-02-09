# PUT

- 방법1

```kotlin
@PutMapping("/put-mapping")
    fun putMapping(): String {
        return "put-mapping"
    }
```



- 방법2

```kotlin
@RequestMapping(method = [RequestMethod.PUT], path = ["/request-mapping"])
fun requestMapping(): String {
    return "request-mapping - put mathod"
}
```



- **복잡한 request body 를 파싱하는 방법**

특징 1. `phoneNumber` 는 snake_case 가 아님
특징 2. 객체 안 배열

```json
{
    "result" : {
        "result_code" : "OK",
        "result_message" : "성공"
    },

    "description" : "~~~~~",

    "user" : [
        {
            "name" : "moonu",
            "age" : 24,
            "email" : "",
            "phoneNumber" : ""
        },
        {
            "name" : "a",
            "age" : 30,
            "email" : "",
            "phoneNumber" : ""
        },
        {
            "name" : "b",
            "age" : 10,
            "email" : "",
            "phoneNumber" : ""
        }
    ]
}
```

- 위의 응답 json 을 모델링

```kotlin
data class UserResponse(
    var result: com.example.mvc.model.http.Result? = null,
    var description: String? = null,

    // user 이름으로 요청이 올 때 UserRequest 에 해당하는 값을 배열로 들어가도록함
    @JsonProperty("user")
    var userRequest: MutableList<UserRequest>? = null,
)

// snake_case 로 동작하도록함
@JsonNaming(PropertyNamingStrategies.SnakeCaseStrategy::class)
data class Result(
    var resultCode: String? = null, // result_code
    var resultMessage: String? = null, // result_message
)
```

- 응답 만들기

```kotlin
class PutApiController {

    @PutMapping(path = ["/put-mapping/object"]) // 컨벤션에 따라 작성하면 된다 위와 동일
    fun putMappingObject(@RequestBody userRequest: UserRequest): UserResponse {

        // 0. Response
        return UserResponse().apply {

            // 1. result
            this.result = com.example.mvc.model.http.Result().apply {
                this.resultCode = "OK"
                this.resultMessage = "성공"
            }
        }.apply {
            // 2. description
            this.description = "~~~~~"
        }.apply {
            // 3. user mutable list
            val userList = mutableListOf<UserRequest>()

          	// user request-body 가 들어오면 add
            userList.add(userRequest)

            userList.add(UserRequest().apply {
                this.name = "a"
                this.age = 10
                this.email = "a@gmail.com"
                this.address = "a address"
                this.phoneNumber = "010-1111-aaaa"
            })

            userList.add(UserRequest().apply {
                this.name = "b"
                this.age = 20
                this.email = "b@gmail.com"
                this.address = "b address"
                this.phoneNumber = "010-1111-bbbb"
            })

            this.userRequest = userList
        }
        // put 과 post 는 같은 body 를 사용할 수 있다 단지 용도가 다를 뿐
        // put 은 request 요청이 올 때 내용이 없다면 생성을, 있다면 수정을 한다.
    }

}
```

- 응답 요청과 결과

  - 요청 body

    ```json
    {
        "name" : "moonu",
        "age" : 24,
        "email" : "lookshdev",
        "address" : "seoul",
        "phoneNumber" : "010-5484-7975"
    }

    - 결과

      ```json
      {
          "result": {
              "result_code": "OK",
              "result_message": "성공"
          },
          "description": "~~~~~",
          "user": [
              {
                  "name": "moonu",
                  "age": 24,
                  "email": "lookshdev",
                  "address": "seoul",
                  "phoneNumber": "010-5484-7975"
              },
              {
                  "name": "a",
                  "age": 10,
                  "email": "a@gmail.com",
                  "address": "a address",
                  "phoneNumber": "010-1111-aaaa"
              },
              {
                  "name": "b",
                  "age": 20,
                  "email": "b@gmail.com",
                  "address": "b address",
                  "phoneNumber": "010-1111-bbbb"
              }
          ]
      }
      ```

      
