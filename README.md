## [코드로 배우는 스프링 웹프로젝트] 책(이하 책으로 표기)<br> 스프링프레임웍(이하 스프링으로 표기)을 이용한 웹사이트 만들기
***
사용된 스프링 버전: 4.3.16.RELEASE
스프링 라이선스는 Apache 2.0 라이선스를 따릅니다.[웹사이트](https://spring.io/)<br>
부트스트랩/AdminLTE/기타등등<br>책 내에서 사용된 외부 오픈소스의 경우 원 오픈소스의 라이선스 정책을 유지합니다.
[라이센스 보기](https://github.com/spring-projects/spring-framework/blob/master/src/docs/dist/license.txt)
***
>작업일자(아래): 20200220
### 이클립스에서 UML Explorer 설치 및 게시판 메서드구조확인.
- [관련 작업정보 보기](http://blog.daum.net/web_design/682): http://blog.daum.net/web_design/682

>작업일자(아래): 20200219
### 책을 내용을 기반으로 스프링 시큐리티 및 회원관리 + admin(관리자)화면 추가.
- mysql, hsql 지원 코드 추가(기본은 hsql) src/main/webapp/WEB-INF/spring/root-context.xml 설정
```xml
    <jdbc:embedded-database id="dataSource" type="HSQL">
		<jdbc:script location= "classpath:/db/edu_hsql.sql"/>
	</jdbc:embedded-database>
	<bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
		<property name="driverClassName" 
				  value="net.sf.log4jdbc.sql.jdbcapi.DriverSpy"></property>
		<property name="url" 
				  value="jdbc:log4jdbc:mysql://127.0.0.1:3306/edu"></property>
		<property name="username" value="root"></property>
		<property name="password" value="apmsetup"></property>
	</bean>
	<cloud:data-source id="dataSource" service-name="wp-mysql-db">
		<cloud:connection properties="sessionVariables=sql_mode='ANSI';characterEncoding=UTF-8"/>
		<cloud:pool pool-size="5-30" max-wait-time="3000"/>
	</cloud:data-source>
```

### hsql메모리 Db 와 mysql Db 파일위치.
- hsql메모리 DB : src/main/resources/db/edu_hsql.sql 파일. [결과 보기](https://spring-edu.herokuapp.com/)
- mysql Db : /DATABASE/edu_mysql.sql 파일. [결과 보기](http://edu.paas-ta.org/)