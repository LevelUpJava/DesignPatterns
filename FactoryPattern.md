
# 🎥 Factory Method Pattern

## 1. 🎯 Definition

The Factory Method Pattern is a creational pattern that provides a way to create objects without specifying the exact class of the object that will be created.

---

## 2. 🌟 Benefits of the Factory Method Pattern

- Loose coupling
- Centralized creation logic
- Easy to maintain and extend
- Interface-based design
- Works with dependency injection
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

### Calendar

```java
Calendar calendar = Calendar.getInstance();
```

### Collections

```java
List<String> list = Collections.singletonList("Java");
```

### Optional

```java
Optional<String> name = Optional.of("Ashwani");
Optional<String> empty = Optional.empty();
```

### Arrays

```java
List<Integer> list = Arrays.asList(1, 2, 3);
```

### Logger

```java
Logger logger = Logger.getLogger("MyAppLogger");
```

### DriverManager

```java
Connection conn = DriverManager.getConnection("jdbc:postgresql://localhost:5432/mydb", "user", "password");
```

### Executors

```java
ExecutorService pool = Executors.newFixedThreadPool(5);
```

---

## 5. 💻 Code Example – Ice Cream Analogy

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
public class IceCreamClient {
    public static void main(String[] args) {
        IceCream chocolateIceCream = IceCreamFactory.getIceCream("chocolate");
        chocolateIceCream.serve();

        IceCream vanillaIceCream = IceCreamFactory.getIceCream("vanilla");
        vanillaIceCream.serve();
    }
}
```

---
