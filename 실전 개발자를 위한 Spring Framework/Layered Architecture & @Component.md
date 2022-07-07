### Layered Architecture 특징
#### 계층화 아키텍처
- 효율적인 개발과 유지보수를 위한 계층화하여 개발
- 각레이어는 독릭적인 R&R을 가지며 근접한 계층끼리만 통신가능

##### 프레젠테이션 영역
- 사용자와 상호작용을 담당
##### 비지니스 영역
- 기능, 트랜젝션 수형
##### 데이터영역
- 데이터 저장, 조회등 데이터베이스와 연동

### MVC 패턴
- Layered Architecture의 프레젠테이션 영역쪽 세분화한곳
##### model : 사용자화면의 데이터를 바인딩하여 표현하는데 바인딩하기전 데이터를 가지고있는쪽(데이터 저장, 처리)
##### controller : 뷰와 모델을 바인딩해주고 제어해주는곳 (화면_user  interface)
##### view : 실질적 프레젠테이션(사용자 요청을 처리)

### 컴포넌트 자동등록

#### 어노테이션 사용
##### @Component
- @Controller
- @Service
- @Repository

##### <content:component-scan base-package="패키지명 />
- 패키지명 하위 패키지를 검색해 @Componet 어노테이션을 포함한 모든 클래스를 빈으로 자동등록
- bean이 될수있는 모든 componet들을 자동으로 찾아 bean container에 등록
- 의존 관계 등록은 따로 하지 않음(DI까지 되지않음) (@Autowired로 사용하여 di수행)

##### @Autowired
- Component 간의 의존관계를 연결
- component-scan과 수동(setter, 생성자)DI는 혼용해서 사용가능


