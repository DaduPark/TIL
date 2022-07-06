
### DL (의존성 lookup)
- 스프링컨테이너에 빈을 등록하여 new 객체로 생성하지 않고 스프링컨테이너에 등록된 빈을 호출하여 객체 호출
- 저장소에 저장되어 있는 빈에 접근하기 위해 컨테이너가 제공하는 api를 이용하여 빈을 lookup 하는것

### DI (의존성주입)
- 생성자 주입/ setter 주입 / 필드 주입 세가지 인데 생성자 주입, setter 주입을 많이 사용
- 각 클래스간의 의존관계를 빈 설정 정보를 바탕으로 컨테이너가 자동으로 연결해주는것
#### setter주입	
- java :  생성하고자하는 객체를 해당 클래스에 "set객체이름"이라는 셋터를 만들어 메소드에 객체를 넣어준 형태로 만듦 
- 스프링컨테이너 :  스프링컨테이너(빈팩토리)에 빈테그의 하의 테그인 properties 테그를 만들어 name속성에는 set메소드의 set을 뺀 이름을 넣어주고 ref속성에는 의존성을 주입할 been 아이디를 넣어줌
```
<bean id="testService" class="경로">
    <property name="testDao" ref="testDao"></property>
</bean>
<bean id="testDao" class="경로"/>
```

```
private TestDao testDao

pubilc void setTestDao(TestDao dao){
	this.testDao = dao;
}
```

#### 생성자 주입 
- java : 생성하고자하는 객체를 해당 클래스의 생성자로 만들어  메소드에 객체를 넣어준 형태로 만듦  
- 스프링컨테이너 : 스프링컨테이너(빈팩토리스)에 빈테그의 하의 테그인 constructor-arg 테그를 만들어 ref속성에는 의존성을 주입할 been 아이디를 넣어줌

```
<bean id="testService" class="경로">
    <constructor-arg ref="testDao"/>
</bean>
<bean id="testDao" class="경로"/>
```

```
private TestDao testDao

pubilc void TestService(TestDao dao){
	this.testDao = dao;
}
```
