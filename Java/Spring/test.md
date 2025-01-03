Container, Dependency, and IOC
• What is dependency injection and what are the advantages?
• What is an interface and what are the advantages of making use of them in Java?
• Why are they recommended for Spring beans?
• What is meant by “application-context?
• How are you going to create a new instance of an ApplicationContext?
• Can you describe the lifecycle of a Spring Bean in an ApplicationContext?
• How are you going to create an ApplicationContext in an integration test?
• What is the preferred way to close an application context? Does Spring Boot do this for
you?
• Can you describe:
• Dependency injection using Java configuration?
• Dependency injection using annotations (@Autowired)?
• Component scanning, Stereotypes?
• Scopes for Spring beans? What is the default scope?
• Are beans lazily or eagerly instantiated by default? How do you alter this behavior?
• What is a property source? How would you use @PropertySource?
• What is a BeanFactoryPostProcessor and what is it used for? When is it invoked?
• Why would you define a static @Bean method?
• What is a ProperySourcesPlaceholderConfigurer used for?
• What is a BeanPostProcessor and how is it different to a BeanFactoryPostProcessor?
What do they do? When are they called?
• What is an initialization method and how is it declared on a Spring bean?
• What is a destroy method, how is it declared and when is it called?
• Consider how you enable JSR-250 annotations like @PostConstruct and
@PreDestroy? When/how will they get called?
• How else can you define an initialization or destruction method for a Spring bean?
• What does component-scanning do?
• What is the behavior of the annotation @Autowired with regards to field injection,
constructor injection and method injection?
• What do you have to do, if you would like to inject something into a private field? How does
this impact testing?
• How does the @Qualifier annotation complement the use of @Autowired?
• What is a proxy object and what are the two different types of proxies Spring can create?
• What are the limitations of these proxies (per type)?
• What is the power of a proxy object and where are the disadvantages?
• What does the @Bean annotation do?
• What is the default bean id if you only use @Bean? How can you override this?
• Why are you not allowed to annotate a final class with @Configuration
• How do @Configuration annotated classes support singleton beans?
• Why can’t @Bean methods be final either?
• How do you configure profiles? What are possible use cases where they might be useful?
• Can you use @Bean together with @Profile?
• Can you use @Component together with @Profile?
• How many profiles can you have?
• How do you inject scalar/literal values into Spring beans?
• What is @Value used for?
• What is Spring Expression Language (SpEL for short)?
• What is the Environment abstraction in Spring?
• Where can properties in the environment come from – there are many sources for
properties – check the documentation if not sure. Spring Boot adds even more.
• What can you reference using SpEL?
• What is the difference between $ and # in @Value expressions?
Aspect oriented programming
• What is the concept of AOP? Which problem does it solve? What is a cross cutting
concern?
• Name three typical cross cutting concerns.
• What two problems arise if you don't solve a cross cutting concern via AOP?
• What is a pointcut, a join point, an advice, an aspect, weaving?
• How does Spring solve (implement) a cross cutting concern?
• Which are the limitations of the two proxy-types?
• What visibility must Spring bean methods have to be proxied using Spring AOP?
• How many advice types does Spring support. Can you name each one?
• What are they used for?
• Which two advices can you use if you would like to try and catch exceptions?
• What do you have to do to enable the detection of the @Aspect annotation?
• What does @EnableAspectJAutoProxy do?
• If shown pointcut expressions, would you understand them?
• For example, in the course we matched getter methods on Spring Beans, what would
be the correct pointcut expression to match both getter and setter methods?
• What is the JoinPoint argument used for?
• What is a ProceedingJoinPoint? When is it used?
Data Management: JDBC, Transactions
• What is the difference between checked and unchecked exceptions?
• Why does Spring prefer unchecked exceptions?
• What is the data access exception hierarchy?
• How do you configure a DataSource in Spring? Which bean is very useful for
development/test databases?
• What is the Template design pattern and what is the JDBC template?
• What is a callback? What are the three JdbcTemplate callback interfaces that can be used
with queries? What is each used for? (You would not have to remember the interface
names in the exam, but you should know what they do if you see them in a code sample).
• Can you execute a plain SQL statement with the JDBC template?
• When does the JDBC template acquire (and release) a connection, for every method
called or once per template? Why?
• How does the JdbcTemplate support generic queries? How does it return objects and
lists/maps of objects?
• What is a transaction? What is the difference between a local and a global transaction?
• Is a transaction a cross cutting concern? How is it implemented by Spring?
• How are you going to define a transaction in Spring?
• What does @Transactional do? What is the PlatformTransactionManager?
• Is the JDBC template able to participate in an existing transaction?
• What is a transaction isolation level? How many do we have and how are they ordered?
• What is @EnableTransactionManagement for?
• What does transaction propagation mean?
• What happens if one @Transactional annotated method is calling another
@Transactional annotated method on the same object instance?
• Where can the @Transactional annotation be used? What is a typical usage if you put it
at class level?
• What does declarative transaction management mean?
• What is the default rollback policy? How can you override it?
• What is the default rollback policy in a JUnit test, when you use the
@RunWith(SpringJUnit4ClassRunner.class) in JUnit 4 or
@ExtendWith(SpringExtension.class) in JUnit 5, and annotate your @Test annotated
method with @Transactional?
• Why is the term "unit of work" so important and why does JDBC AutoCommit violate this
pattern?
• What do you need to do in Spring if you would like to work with JPA?
• Are you able to participate in a given transaction in Spring while working with JPA?
• Which PlatformTransactionManager(s) can you use with JPA?
March 2019 © Copyright 2019 Pivotal Software, Inc. All rights reserved 8
• What do you have to configure to use JPA with Spring? How does Spring Boot make this
easier?
Spring Data JPA
• What is a Repository interface?
• How do you define a Repository interface? Why is it an interface not a class?
• What is the naming convention for finder methods in a Repository interface?
• How are Spring Data repositories implemented by Spring at runtime?
• What is @Query used for?
Spring MVC and the Web Layer
• MVC is an abbreviation for a design pattern. What does it stand for and what is the idea
behind it?
• What is the DispatcherServlet and what is it used for?
• What is a web application context? What extra scopes does it offer?
• What is the @Controller annotation used for?
• How is an incoming request mapped to a controller and mapped to a method?
• What is the difference between @RequestMapping and @GetMapping?
• What is @RequestParam used for?
• What are the differences between @RequestParam and @PathVariable?
• What are some of the parameter types for a controller method?
• What other annotations might you use on a controller method parameter? (You can
ignore form-handling annotations for this exam)
• What are some of the valid return types of a controller method?
Security
• What are authentication and authorization? Which must come first?
• Is security a cross cutting concern? How is it implemented internally?
• What is the delegating filter proxy?
• What is the security filter chain?
• What is a security context?
• What does the ** pattern in an antMatcher or mvcMatcher do?
• Why is the usage of mvcMatcher recommended over antMatcher?
• Does Spring Security support password hashing? What is salting?
• Why do you need method security? What type of object is typically secured at the method
level (think of its purpose not its Java type).
• What do @PreAuthorized and @RolesAllowed do? What is the difference between them?
• How are these annotations implemented?
• In which security annotation are you allowed to use SpEL?
REST
• What does REST stand for?
• What is a resource?
• What does CRUD mean?
• Is REST secure? What can you do to secure it?
• Is REST scalable and/or interoperable?
• Which HTTP methods does REST use?
• What is an HttpMessageConverter?
• Is REST normally stateless?
• What does @RequestMapping do?
• Is @Controller a stereotype? Is @RestController a stereotype?
• What is a stereotype annotation? What does that mean?
• What is the difference between @Controller and @RestController?
• When do you need @ResponseBody?
• What are the HTTP status return codes for a successful GET, POST, PUT or DELETE
operation?
• When do you need @ResponseStatus?
• Where do you need @ResponseBody? What about @RequestBody? Try not to get these
muddled up!
• If you saw example Controller code, would you understand what it is doing? Could you tell
if it was annotated correctly?
• Do you need Spring MVC in your classpath?
• What Spring Boot starter would you use for a Spring REST application?
• What are the advantages of the RestTemplate?
• If you saw an example using RestTemplate would you understand what it is doing?
Testing
• Do you use Spring in a unit test?
• What type of tests typically use Spring?
• How can you create a shared application context in a JUnit integration test?
• When and where do you use @Transactional in testing?
• How are mock frameworks such as Mockito or EasyMock used?
• How is @ContextConfiguration used?
• How does Spring Boot simplify writing tests?
• What does @SpringBootTest do? How does it interact with @SpringBootApplication
and @SpringBootConfiguration?
Spring Boot Intro
• What is Spring Boot?
• What are the advantages of using Spring Boot?
• Why is it “opinionated”?
• What things affect what Spring Boot sets up?
March 2019 © Copyright 2019 Pivotal Software, Inc. All rights reserved 10
• What is a Spring Boot starter POM? Why is it useful?
• Spring Boot supports both properties and YML files. Would you recognize and understand
them if you saw them?
• Can you control logging with Spring Boot? How?
• Where does Spring Boot look for property file by default?
• How do you define profile specific property files?
• How do you access the properties defined in the property files?
• What properties do you have to define in order to configure external MySQL?
• How do you configure default schema and initial data?
• What is a fat far? How is it different from the original jar?
• What is the difference between an embedded container and a WAR?
• What embedded containers does Spring Boot support?
Spring Boot Auto Configuration
• How does Spring Boot know what to configure?
• What does @EnableAutoConfiguration do?
• What does @SpringBootApplication do?
• Does Spring Boot do component scanning? Where does it look by default?
• How are DataSource and JdbcTemplate auto-configured?
• What is spring.factories file for?
• How do you customize Spring auto configuration?
• What are the examples of @Conditional annotations? How are they used?
Spring Boot Actuator
• What value does Spring Boot Actuator provide?
• What are the two protocols you can use to access actuator endpoints?
• What are the actuator endpoints that are provided out of the box?
• What is info endpoint for? How do you supply data?
• How do you change logging level of a package using loggers endpoint?
• How do you access an endpoint using a tag?
• What is metrics for?
• How do you create a custom metric with or without tags?
• What is Health Indicator?
• What are the Health Indicators that are provided out of the box?
• What is the Health Indicator status?
• What are the Health Indicator statuses that are provided out of the box
• How do you change the Health Indicator status severity order?
• Why do you want to leverage 3rd-party external monitoring system?
Spring Boot Testing
• When do you want to use @SpringBootTest annotation?
• What does @SpringBootTest auto-configure?
March 2019 © Copyright 2019 Pivotal Software, Inc. All rights reserved 11
• What dependencies does spring-boot-starter-test brings to the classpath?
• How do you perform integration testing with @SpringBootTest for a web application?
• When do you want to use @WebMvcTest? What does it auto-configure?
• What are the differences between @MockBean and @Mock?
• When do you want @DataJpaTest for? What does it auto-configure?