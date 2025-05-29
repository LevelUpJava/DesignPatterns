# 🎥 Java Design Pattern Tutorial: Builder Pattern

---

## 1. 🌟 Definition

> *The Builder Pattern is a creational design pattern that lets you construct complex objects step-by-step.*
---

## 2. 💻 Code Example – Burger Builder

```java
class Burger {
    private String bun;
    private boolean cheese;
    private boolean lettuce;
    private boolean tomato;
    private boolean onion;
    private boolean cucumber;
    private boolean ketchup;
    private int patties;

    private Burger(BurgerBuilder builder) {
        this.bun = builder.bun;
        this.cheese = builder.cheese;
        this.lettuce = builder.lettuce;
        this.tomato = builder.tomato;
        this.onion = builder.onion;
        this.cucumber = builder.cucumber;
        this.ketchup = builder.ketchup;
        this.patties = builder.patties;
    }

    public void display() {
        System.out.println("Burger with " + patties + " patties, Bun: " + bun +
                ", Cheese: " + cheese + ", Lettuce: " + lettuce + ", Tomato: " + tomato +
                ", Onion: " + onion + ", Cucumber: " + cucumber + ", Ketchup: " + ketchup);
    }

    public static class BurgerBuilder {
        private String bun;
        private boolean cheese;
        private boolean lettuce;
        private boolean tomato;
        private boolean onion;
        private boolean cucumber;
        private boolean ketchup;
        private int patties;

        public BurgerBuilder setBun(String bun) {
            this.bun = bun;
            return this;
        }
        public BurgerBuilder setCheese(boolean cheese) {
            this.cheese = cheese;
            return this;
        }
        public BurgerBuilder setLettuce(boolean lettuce) {
            this.lettuce = lettuce;
            return this;
        }
        public BurgerBuilder setTomato(boolean tomato) {
            this.tomato = tomato;
            return this;
        }
        public BurgerBuilder setOnion(boolean onion) {
            this.onion = onion;
            return this;
        }
        public BurgerBuilder setCucumber(boolean cucumber) {
            this.cucumber = cucumber;
            return this;
        }
        public BurgerBuilder setKetchup(boolean ketchup) {
            this.ketchup = ketchup;
            return this;
        }
        public BurgerBuilder setPatties(int patties) {
            this.patties = patties;
            return this;
        }
        public Burger build() {
            return new Burger(this);
        }
    }
}

public class BurgerClient {
    public static void main(String[] args) {
        Burger burger = new Burger.BurgerBuilder()
                .setBun("Sesame")
                .setCheese(true)
                .setLettuce(true)
                .setTomato(true)
                .setOnion(true)
                .setCucumber(true)
                .setKetchup(true)
                .setPatties(2)
                .build();

        burger.display();
    }
}
```

---

## 3.1 🔧 Problem with Traditional Constructor

```java
class SimpleBurger {
    private String bun;
    private boolean cheese;
    private boolean lettuce;
    private boolean tomato;
    private boolean onion;
    private boolean cucumber;
    private boolean ketchup;
    private int patties;

    public SimpleBurger(String bun) {
        this(bun, false);
    }
    public SimpleBurger(String bun, boolean cheese) {
        this(bun, cheese, false);
    }
    public SimpleBurger(String bun, boolean cheese, boolean lettuce) {
        this(bun, cheese, lettuce, false);
    }
    public SimpleBurger(String bun, boolean cheese, boolean lettuce, boolean tomato) {
        this(bun, cheese, lettuce, tomato, false);
    }
    public SimpleBurger(String bun, boolean cheese, boolean lettuce, boolean tomato, boolean onion) {
        this(bun, cheese, lettuce, tomato, onion, false);
    }
    public SimpleBurger(String bun, boolean cheese, boolean lettuce, boolean tomato, boolean onion, boolean cucumber) {
        this(bun, cheese, lettuce, tomato, onion, cucumber, false);
    }
    public SimpleBurger(String bun, boolean cheese, boolean lettuce, boolean tomato, boolean onion, boolean cucumber, boolean ketchup) {
        this(bun, cheese, lettuce, tomato, onion, cucumber, ketchup, 1);
    }
    public SimpleBurger(String bun, boolean cheese, boolean lettuce, boolean tomato, boolean onion, boolean cucumber, boolean ketchup, int patties) {
        this.bun = bun;
        this.cheese = cheese;
        this.lettuce = lettuce;
        this.tomato = tomato;
        this.onion = onion;
        this.cucumber = cucumber;
        this.ketchup = ketchup;
        this.patties = patties;
    }

    public void display() {
        System.out.println("[Traditional] Burger with " + patties + " patties, Bun: " + bun +
                ", Cheese: " + cheese + ", Lettuce: " + lettuce + ", Tomato: " + tomato +
                ", Onion: " + onion + ", Cucumber: " + cucumber + ", Ketchup: " + ketchup);
    }
}

public class TraditionalClient {
    public static void main(String[] args) {
        SimpleBurger traditional = new SimpleBurger("Wheat", true, false, true, false, true, false, 3);
        traditional.display();
    }
}
```

---

## 4. 🧐 Why Not Use `new` Directly?

* Leads to telescoping constructors and unreadable parameter lists
* Hard to manage optional arguments
* Code becomes tightly coupled and error-prone
* Builder offers a fluent and readable alternative

---

## 5. 🔍 Which SOLID Principles Are Used?

| SOLID Principle                   | How It’s Applied                                                              |
| --------------------------------- | ----------------------------------------------------------------------------- |
| ✅ Single Responsibility Principle | Builder handles object creation, product handles data and behavior            |
| ✅ Open/Closed Principle           | Easily extend builder for new fields without modifying client code            |
| ✅ Liskov Substitution Principle   | Builder can be extended for different product types without breaking behavior |
| ✅ Dependency Inversion Principle  | Clients rely on builder abstraction rather than concrete construction process |

---

## 6. 📦 Where It’s Used in the JDK

```java
StringBuilder sb = new StringBuilder().append("Hello").append(" World");
ProcessBuilder pb = new ProcessBuilder("notepad.exe");
ByteBuffer buffer = ByteBuffer.allocate(1024);
Stream.Builder<String> builder = Stream.builder().add("a").add("b");
Locale locale = new Locale.Builder().setLanguage("en").setRegion("US").build();
```

---

## 7. 🌟 Key Benefits

* Fluent and readable object construction
* No need for large constructors with many parameters
* Better maintainability and extensibility
* Safer and clearer code, especially with optional fields
* Helps create immutable objects

---

## 8. 🔁 Comparison & Recap

| Pattern          | Use Case                                 | Example                                      |
| ---------------- | ---------------------------------------- | -------------------------------------------- |
| Factory          | Single simple object creation            | `ProductFactory.create()`                    |
| Abstract Factory | Families of related objects              | `ThemeFactory.createButton() + createMenu()` |
| **Builder**      | Complex object step-by-step construction | `new Builder().setX().setY().build()`        |

✨ Use Builder when your object has many optional fields or combinations.
