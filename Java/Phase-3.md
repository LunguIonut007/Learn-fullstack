# Dependency injection

[The mechanism that is used by *@Autowired* is called *dependency injection*](https://www.javaworld.com/article/2071914/excellent-explanation-of-dependency-injection--inversion-of-control-.html)

# Spring beans
A *spring bean* is an object that can be injected in a class. A bean can be declared in two ways: with __@Bean__ or with **@Component/@Service/@Controller**. The key difference is that in **@Component/@Service/@Controller** classes you can use *@Autowired* to inject other java objects.


## Simple project
Create a project with [spring initializr](https://start.spring.io) that has a *web* dependency.

+ Make the main class implement the **CommandLineRunner** interface.

Now, after the server has started, the *run* function will be called.

Let's make a class called *QuoteService* that looks like this: 

```java
public class QuoteService {
    public String getQuoteOfTheDay() {
        return "To be or not to be!";
    }
}
```

We would like to print to the screen the quote of the day, inside the *run* function.

First, let's make the QuoteService a bean.

The **@Bean** annotation must be declared over a function witch return's the object.

```java
	@Bean
	public QuoteService getQuoteService() {
		return new QuoteService();
	}
```

For simplicity, let's declare the bean in the main file.

```java
@SpringBootApplication
public class DemoApplication implements CommandLineRunner {

	public static void main(String[] args) {
		SpringApplication.run(DemoApplication.class, args);
	}

	@Bean
	public QuoteService getQuoteService() {
		return new QuoteService();
	}
}
```

Now we can use **@Autowired** to inject the object and get the quote.

```java
@SpringBootApplication
public class DemoApplication implements CommandLineRunner {

	@Autowired
	private QuoteService quoteService;

	public static void main(String[] args) {
		SpringApplication.run(DemoApplication.class, args);
	}

	@Override
	public void run(String... strings) throws Exception {
		System.out.println(quoteService.getQuoteOfTheDay());
	}

	@Bean
	public QuoteService getQuoteService() {
		return new QuoteService();
	}
}
```

If we declare declare the *QuoteService* class with the *@Service* annotation, then there is no need to define a bean.

```java
@Service
public class QuoteService {
    public String getQuoteOfTheDay() {
        return "To be or not to be";
    }
}
```

So the final code is just:
```java
@SpringBootApplication
public class DemoApplication implements CommandLineRunner {

	@Autowired
	private QuoteService quoteService;

	public static void main(String[] args) {
		SpringApplication.run(DemoApplication.class, args);
	}

	@Override
	public void run(String... strings) throws Exception {
		System.out.println(quoteService.getQuoteOfTheDay());
	}
	
}
```



