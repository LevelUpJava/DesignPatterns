# 🎯 Abstract Factory Pattern

---

## 1. Definition

The Abstract Factory Pattern provides an interface to create families of related objects without specifying their concrete classes.

---

## 2. Code Example

```java
// Product Interface
interface IceCream {
    void serve();
}

// Brand A Products
class CreamLandChocolate implements IceCream {
    public void serve() {
        System.out.println("CreamLand Chocolate Ice Cream");
    }
}
class CreamLandVanilla implements IceCream {
    public void serve() {
        System.out.println("CreamLand Vanilla Ice Cream");
    }
}

// Brand B Products
class KulfiGharChocolate implements IceCream {
    public void serve() {
        System.out.println("KulfiGhar Chocolate Kulfi");
    }
}
class KulfiGharVanilla implements IceCream {
    public void serve() {
        System.out.println("KulfiGhar Vanilla Kulfi");
    }
}

// Abstract Factory
interface IceCreamFactory {
    IceCream createChocolate();
    IceCream createVanilla();
}

// Concrete Factories
class CreamLandFactory implements IceCreamFactory {
    public IceCream createChocolate() { return new CreamLandChocolate(); }
    public IceCream createVanilla() { return new CreamLandVanilla(); }
}
class KulfiGharFactory implements IceCreamFactory {
    public IceCream createChocolate() { return new KulfiGharChocolate(); }
    public IceCream createVanilla() { return new KulfiGharVanilla(); }
}

// Client
public class IceCreamClient {
    public static void main(String[] args) {
        IceCreamFactory factory = new CreamLandFactory();
        IceCream choco = factory.createChocolate();
        IceCream vanilla = factory.createVanilla();
        choco.serve();
        vanilla.serve();
    }
}
```

---

## 3. SOLID Principles Used

| Principle                      |
|-------------------------------|
| ✅ Single Responsibility       |
| ✅ Open/Closed                 |
| ✅ Liskov Substitution         |
| ✅ Dependency Inversion        |

---

## 4. JDK Usage Examples

```java
DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
SSLContext sslContext = SSLContext.getInstance("TLS");
GraphicsEnvironment ge = GraphicsEnvironment.getLocalGraphicsEnvironment();
UIManager.setLookAndFeel("com.sun.java.swing.plaf.windows.WindowsLookAndFeel");
Toolkit toolkit = Toolkit.getDefaultToolkit();
```

---

## 5. Key Benefits

- Supports creation of related object families
- Promotes loose coupling between code and product variants
- Easier to swap entire product families
- Maintains consistency among created objects
- Centralizes object creation logic

---
