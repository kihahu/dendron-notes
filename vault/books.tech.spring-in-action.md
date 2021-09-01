---
id: KYZS7dUMRSIagJiwlZl1X
title: Spring in Action
desc: ''
updated: 1630503806951
created: 1629858155875
---

## Chpt 2: Wiring beans

Auto configuration
- `@Autowired` works on both constructor and method (will create dependent beans, and throw error if can't find)
- `@Autowired` is spring specific, use `@Inject` from java, mostly interchangable 
- when using `@ComponentScan`, better to use `basePackageClasses` to be refactor proof

Manual wiring:
- `@bean` by default ID = method name. override it with `name=`
- by default, all beans in spring are singletons.
  
  ```
  @Bean
  public CompactDisc sgtPeppers(){
    return new SgtPappers();
  }
  ```
 
 if directly call the method that a bean annotation is on, e.g. `sgtPepeprs()` will return the singleton rather than creating another instance. 

 ## Chpt 3: Advanced wiring

- `@Profile("dev")` annotation for beans only created when active profiles include dev
- `@Conditional(MagicExistsCondition.class)` for custom conditions 
  -  Condition interface comes with 2 params: `matches(ConditionContext context, AnnotatedTypeMetadata metadata)`
  - [ConditionContext](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/context/annotation/ConditionContext.html)
    - bean registry: bean definitions
    - bean factory: presence of beans
    - environment: env varialbes
    - resource loader: resources loaded
    - class loader: class loaded 
- disambiguating beans
  - `@Primary`
  - `@Qualifier("cold)`
  - Use custom qualifier annotations to allow multiple qualifiers - `@Cold` 
    
    ```
    @Target({ElementType.FIELD, ElementType.PARAMETER, ElementType.TYPE})
    @Retention(RetentionPolicy.RUNTIME)
    @Qualifier
    public @interface Cold {
    }
    ```
- `@Scope`
  - singleton
  - prototype - created each time is injected 
  - session - in web app, one for each session. e.g. shopping cart 
  - request 
    - scope proxy 
   
    
## Chpt4: Aspect oriented Spring

- basic concepts:
  ![](/assets/images/2021-08-31-20-04-25.png)
- unlike AspectJ, spring is proxy based, and only supports **method interception**

 ![](/assets/images/2021-08-31-20-05-48.png)

- wrap method options:
  - `@After`
  - `@AfterReturning`
  - `@AfterThrowing`	
  - `@Around`	
  - `@Before`	
- also possible to add methods using **Introduction**

  ![](/assets/images/2021-09-01-09-26-38.png)

