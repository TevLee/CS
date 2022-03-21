### PUT
- method requests that the state of the target resource be created or replaced with the state defined by the representation enclosed in the request message payload
- 공통점은 부분수정이라는 점.
- PUT은 요청시 요청의 일부분만 보낸 경우 나머지는 default 값으로 수정되는 것이 원칙
- 예를 들어, Gildong 유저의 age만 변경하고자 할 때, age만 보내면 name은 default(null)로 초기화
```
PUT /users/1 
{
  "age": 15 
} 

HTTP/1.1 200 OK 
{ 
  "name": null, // name은 null값으로 초기화
  "age": 15 
}

```
### PATCH
- which is used to apply partial modifications to a resource
- PATCH는 수정할 부분만 보낼 경우, 나머지는 변화 없음
- 위 예시에서 age만 보내서 변경가능
```
PUT /users/1 
{
  "name": "gildong" 
  "age": 15 
} 
HTTP/1.1 200 OK 
{ 
  "name": "gildong", //name 그대로 유지
  "age": 15 
}
```
