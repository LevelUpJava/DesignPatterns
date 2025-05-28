
# 🎥 Java Design Pattern Tutorial: Factory Pattern

## 1. 🎯 Definition

The Factory Design Pattern is a creational pattern that provides a way to create objects without specifying the exact class of the object that will be created.

---

## 2. 💻 Code Example – Ice Cream Analogy

```java
// Step 1: Common interface
interface IceCream {
    void serve();
}

// Step 2: Concrete classes
class ChocolateIceCream implements IceCream {
    public void serve() {
        System.out.println("Serving Chocolate Ice Cream");
    }
}

class VanillaIceCream implements IceCream {
    public void serve() {
        System.out.println("Serving Vanilla Ice Cream");
    }
}

// Step 3: Factory class
class IceCreamFactory {
    public static IceCream getIceCream(String type) {
        if (type.equalsIgnoreCase("chocolate")) {
            return new ChocolateIceCream();
        } else if (type.equalsIgnoreCase("vanilla")) {
            return new VanillaIceCream();
        }
        throw new IllegalArgumentException("Unknown Ice Cream Type");
    }
}

// Step 4: Client
public class IceCreamParlour {
    public static void main(String[] args) {
        IceCream ice1 = IceCreamFactory.getIceCream("chocolate");
        ice1.serve();

        IceCream ice2 = IceCreamFactory.getIceCream("vanilla");
        ice2.serve();
    }
}
```

---

## 3. 🔍 Which SOLID Principles Are Used?

| Principle |
|----------|
| ✅ Single Responsibility |
| ✅ Open/Closed |
| ✅ Liskov Substitution |
| ✅ Dependency Inversion |

---

## 4. 📦 Where It’s Used in the JDK

### 1. `Calendar`

```java
Calendar calendar = Calendar.getInstance();
```

### 2. `Optional`

```java
Optional<String> name = Optional.of("Ashwani");
Optional<String> empty = Optional.empty();
```

### 3. `Logger`

```java
Logger logger = Logger.getLogger("MyAppLogger");
```

### 4. `DriverManager`

```java
Connection conn = DriverManager.getConnection(
  "jdbc:postgresql://localhost:5432/mydb", "user", "password");
```

### 5. `Executors`

```java
ExecutorService pool = Executors.newFixedThreadPool(5);
```

---

## 5. 🌟 Benefits of the Factory Pattern

- Loose coupling
- Centralized creation logic
- Easy to manage, test, and modify
- Works well with dependency injection
- Encourages interface-based design

---
