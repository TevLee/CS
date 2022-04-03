# 생성자 vs. Builder
> **요약**  
> 객체 생성은 1)점층적 생성자 방식 2) 자바빈즈 패턴 3)Builder 방식이 있다  
> 
> 1)은 인자가 많아지면 읽기 어렵고, 각 인자가 의미하는 바를 알기 어렵다  
> 
> 2)는 setter를 사용하므로, 객체가 완전히 생성되기 전까지는 일관성이 무너진 상태로 존재하며  
>   일관성이 깨진 객체가 존재할 경우, 버그의 원인이 될 수 있다  
> 
> 3)은 하나의 메서드로 객체를 생성하여 불변(Immutable)한 객체를 생성할 수 있고,  
>   가독성에도 유리하므로 사용된다  
>
>  다만, 상황에 따라 적절히 혼용된다(인자가 적은 경우 등)

## 생성자는 무엇인가요?
- 객체가 생성될 때 호출되는 객체 초기화 메서드입니다.
```
User user = new User();
```
## Builer 패턴이란 무엇인가요?
- 생성자와 동일하게 객체를 초기화합니다
- 다만, new 연산자가 대신 build() 메서드로 객체를 생성합니다
### 그렇다면, Builder 패턴은 왜 / 언제 사용해야하나요?
- 일반 생성자를 사용하면 param 수가 늘어났을 때 작성과 읽기가 어려워집니다
- 대안책으로 setter를 이용한 **자바빈패턴**을 사용할 수 있지만
```
// cocaCola을 영양 성분 정보를 setter메소드를 통해 초기화하는 자바빈 패턴
NutritionFacts cocaCola = new NutritionFacts();
cocaCola.setServingSize(240);
cocaCola.setServings(8);
cocaCola.setCalories(100);
cocaCola.setSodium(35);
cocaCola.setCarbohdydrate(27);
```
- 이 경우, Imuutable한 객체를 만들 수 없습니다.
- 따라서, **가독성**과 **Immutable**한 객체 생성을 위해 Builder 패턴을 사용합니다
### Builder 패턴을 적용한 경우
```
NutritionFacts cocaCola = new NutritionFacts.Builder(240, 8)
                                            .calories(100)
                                            .sodium(35)
                                            .carbohydrate(27)
                                            .build();
```
- (1) 각 param의 의미를 알기 쉽고(가독성)
- (2) 변경불가능한 Immutable 객체를 획득하며
- (3) build() 메서드로 잘못된 입력값을 검증할 수 있다
### 그렇다면, 왜 항상 Builder 패턴을 사용하지 않고 생성자 방식과 혼용할까요?
- 상황에 따라 적절하게 사용하면 됩니다
