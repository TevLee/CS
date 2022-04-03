# MockMVC 코드를 이용한 테스트 코드 작성
> *Mock : 모조품(가짜)*
> **요약**
> WAS 역할 중 테스트에 필요한 기능만 하는 가짜(Mock)객체를 만들어서 
> 스프링 MVC 동작을 재현할 수 잇는 클래스 -> MockMvc
## (1)JUnit을 사용하는 방식과 (2)MockMVC를 사용하는 방식이 있다
> 지금까지 테스트코드를 작성할 때는 JUnit으로 assertThat()을 주로 이용해왔다
> 차이점은 다음번에 작성하고
> MockMVC 를 사용하는 방법을 알아보자
### MockMVC를 사용하는 이유는 무엇인가요?
- 웹 API를 테스트 하기위해서는 WAS가 있어야 합니다
- 즉, 클라이언트가 응답을 보내고 받을 존재가 필요한 것입니다
- MockMVC는 WAS의 역할을 수행합니다
- MockMVC를 이용하면 아래 그림과 같은 테스트를 수행할 수 있습니다
  - HTTP Servlet 관련, Spring MVC 관련, Content Data 관련 테스트
> ![image](https://user-images.githubusercontent.com/48271665/161434377-ef6f87c0-1ce8-4d62-a846-3b20bc9d429e.png)
### 예시
- CommentApiController를 단위 테스트한다는 것은,
- Controller가 사용하는 Service는 함께 테스트하지 않는다는 것을 말합니다
- 이를 위핸 Service에 대한 Mock 객체를 사용할 것이고,
- Mokito를 이용해 Mock 객체를 생성합니다
- 그리고나서 Controller를 테스트하기 위해 MockMVC를 사용합니다
```
private MockMvc mockMvc; 

@Mock
CommentService commentService; // @Mock이 붙었기 때문에 Mockito에 의해 Mock객체로 생성

@InjectMocks // @InjectMocks가 붙었기 때문에 Mock객체를 사용합니다
public CommentApiController commentapicontroller; # 즉, Spring에 의해 Injection된 객체가 아닌 Mock객체를 주입받습니다

@Before
public void createController(){
  MockitoAnnotations.initMocks(this); // 현재 객체에서 @Mock이 붙은 필드(CommentService 내부의 변수,메서드 등)를 Mock객체로 초기화합니다
  mockMvc = MockMvcBuilders.standaloneSetup(commentApiController).build(); // commentApiController를 테스트하기위한 MockMVC 객체를 생성합니다
}
  
@Test
public void testmethod() throws Exception{}
```
- 위 코드가 잘 이해가 되지 않아서 직접 사용한 코드를 가져왔다
```
// then
mockMvc.perform(patch("/api/v1/products/"+testProduct.getId()+"/comments/"+comment.getId())
        .contentType(MediaType.APPLICATION_JSON)
        .content(objectMapper.writeValueAsString(reqBody)))
        .andExpect(status().isOk())
        .andDo(print());
```
- mockMvc로 생성한 객체에 url를 넣고,
- 어떤 type을 넣을 것인지 알려준다음(contentType)
- JSON형태(HashMap)로 생성한 데이터(reqBody)를
- String 형태로 변경해 보내준다 objectMapper로 매핑시켜서..
- HTTP 응답코드가 200인지 확인. 끝.
