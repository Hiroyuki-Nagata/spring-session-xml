# spring-session-xml

## Build & Run

* Requirements
    * Maven3
    * Java8
    * Redis ( working with localhost:6789 )

```
$ cd spring-session-xml
$ mvn install
$ REDIS_HOST=localhost REDIS_PORT=6379 mvn install jetty:run
```

## XML setting & Tricks

* This project is following [HttpSession XML Guide](http://docs.spring.io/spring-session/docs/current-SNAPSHOT/reference/html5/guides/httpsession-xml.html)
* You can change `cookieName` or `domainNamePattern` from `DefaultCookieSerializer`

```
	<!-- activate annotations in the spring-session -->
	<context:annotation-config/>
	<!-- activate & configure Redis settings -->
	<bean class="org.springframework.session.data.redis.config.annotation.web.http.RedisHttpSessionConfiguration"/>
	<!-- bean for Redis client -->
	<bean class="org.springframework.data.redis.connection.lettuce.LettuceConnectionFactory"/>
	
	<!-- bean for Session & Cookie settings (simply override session name) -->
	<bean class="org.springframework.session.web.http.DefaultCookieSerializer">
		<property name="cookieName" value="JSESSIONID-XXX" />
		<property name="domainNamePattern" value="^.+?\\.(\\w+\\.[a-z]+)$" />		
	</bean>
```
