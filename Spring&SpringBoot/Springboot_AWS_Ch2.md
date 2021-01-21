## Ch1. 인텔레제이로 스프링 부트 시작하기
1. 인텔리제이 소개
######장점
- 강력한 추천기능
- 다양한 리팩토링과 디버깅 기능
- 이클립스의 깃에 비해 높은 자유도
- 프로젝트 시작할때 인덱싱을 하여 파일을 비롯한 자원들에 대한빠른 검색속도

설치- 젯브레인을 통해 intelliJ IDEA Community(무료) 다운

1.2이클립스의 워크페이스 개념이 없고프로젝트와 모듈 개념만있음
그래서 모든 프로젝트를 한번에 불러올수 없음. 한화면에서 하나의 프로젝트만 열림

2.인텔리제이설치 및 설정

설치 후 -그레이들 프로젝트를 스프링 부트 프로젝트로 변경하기-
build.gradle파일 열기

```gradle
// 플러그인 의존성 관리 설정
buildscript {
    ext {// build.gradle에서 사용하는 전역변수를 설정하겠다는 의미
        springBootVersion = '2.1.7.RELEASE'
    }
    repositories {//각종 의존성(라이브러리)들을 어떤 원격 저장소에서 받을지 정함
        mavenCentral()
        jcenter()//라이브러리 업로드를 간단하게 하여 요즘 많이씀
    }
    dependencies {//위 변수 버전을 따라가게됨
        classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}")//큰따음표로 써야됨
    }
}

// 앞서 선언한 플러그인 의존성들을 적용할 것인지를 결정하는 코드
apply plugin: 'java'
apply plugin: 'eclipse'
apply plugin: 'org.springframework.boot'// 위 3개 -> 자바와 스프링 부트를 사용하기 위한 필수 플러그인
apply plugin: 'io.spring.dependency-management' // 스프링 부트의 의존성을 관리해 주는 플러그인으로 반드시 추가해야 한다.

group 'org.example'
version '1.0-SNAPSHOT'

repositories {
    mavenCentral()
}

dependencies {//개발에 필요한 의존성들을 선언하는 곳
    compile('org.springframework.boot:spring-boot-starter-web')
    testCompile ('org.springframework.boot:spring-boot-starter-test')
}
```
>위처럼 변경되면 gradle탭에서 의존성들이 잘 받아졌는지 확인가능

3. 깃과 깃허브사용

- share project on github로 가입하되 
'invalid authentication data. 404 not found'가 뜨게 되면 아래 링크처럼 토큰 로그인하기
<https://devmg.tistory.com/167>/<https://velog.io/@janeljs/IntelliJ-initial-setup>
- .idea는 프로젝트 실행시 자동으로 생성되는 파일으로 gitignore파일을 사용하여 커밋 대상에서 죄외되도록 설정
.gitignore파일에 자동으로 생성되는 파일들을 이그노어 처리하여 커밋함
