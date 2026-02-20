# Design Patterns Guide

This repository is a compact revision guide for key design patterns.

## Revision PDFs Covered

- [Abstract Factory](Revision/Abstract+Factory.pdf)
- [Builder](Revision/Builder.pdf)
- [Simple Factory](Revision/Simpe+Factory.pdf)
- [Factory Method](Revision/Factory+Method.pdf)
- [Prototype](Revision/Prototype.pdf)
- [Bridge](Revision/Bridge.pdf)
- [Composite](Revision/Composite.pdf)
- [Class Adapter](Revision/Class+Adapter.pdf)
- [Object Adapter](Revision/Object_Adapter.pdf)

## UML Diagrams

### 1) Abstract Factory

```mermaid
classDiagram
    class AbstractFactory {
      +createProductA()
      +createProductB()
    }
    class ConcreteFactory1
    class ConcreteFactory2

    class AbstractProductA
    class ProductA1
    class ProductA2

    class AbstractProductB
    class ProductB1
    class ProductB2

    class Client

    AbstractFactory <|.. ConcreteFactory1
    AbstractFactory <|.. ConcreteFactory2

    AbstractProductA <|.. ProductA1
    AbstractProductA <|.. ProductA2

    AbstractProductB <|.. ProductB1
    AbstractProductB <|.. ProductB2

    Client --> AbstractFactory
    ConcreteFactory1 ..> ProductA1
    ConcreteFactory1 ..> ProductB1
    ConcreteFactory2 ..> ProductA2
    ConcreteFactory2 ..> ProductB2
```

### 2) Builder

```mermaid
classDiagram
    class Director {
      +construct()
    }

    class Builder {
      <<interface>>
      +buildPartA()
      +buildPartB()
      +getResult()
    }

    class ConcreteBuilder
    class Product

    Director --> Builder
    Builder <|.. ConcreteBuilder
    ConcreteBuilder --> Product
```

### 3) Simple Factory

```mermaid
classDiagram
    class Client

    class SimpleFactory {
      +createProduct(type)
    }

    class Product {
      <<interface>>
      +operation()
    }

    class ConcreteProductA
    class ConcreteProductB

    Client --> SimpleFactory
    Client --> Product

    Product <|.. ConcreteProductA
    Product <|.. ConcreteProductB

    SimpleFactory ..> ConcreteProductA
    SimpleFactory ..> ConcreteProductB
```

### 4) Factory Method

```mermaid
classDiagram
    class Creator {
      <<abstract>>
      +anOperation()
      +factoryMethod() Product
    }

    class ConcreteCreator

    class Product {
      <<interface>>
      +operation()
    }

    class ConcreteProduct

    Creator <|-- ConcreteCreator
    Product <|.. ConcreteProduct

    Creator --> Product
    ConcreteCreator ..> ConcreteProduct
```

### 5) Prototype

```mermaid
classDiagram
    class Prototype {
      <<interface>>
      +clone() Prototype
    }

    class ConcretePrototypeA
    class ConcretePrototypeB
    class Client

    Prototype <|.. ConcretePrototypeA
    Prototype <|.. ConcretePrototypeB

    Client --> Prototype
```

### 6) Bridge

```mermaid
classDiagram
    class Abstraction {
      -implementor: Implementor
      +operation()
    }

    class RefinedAbstraction

    class Implementor {
      <<interface>>
      +operationImpl()
    }

    class ConcreteImplementorA
    class ConcreteImplementorB

    Abstraction <|-- RefinedAbstraction
    Abstraction --> Implementor

    Implementor <|.. ConcreteImplementorA
    Implementor <|.. ConcreteImplementorB
```

### 7) Composite

```mermaid
classDiagram
    class Component {
      <<abstract>>
      +operation()
      +add(Component)
      +remove(Component)
      +getChild(index)
    }

    class Leaf

    class Composite {
      -children: List~Component~
      +operation()
      +add(Component)
      +remove(Component)
      +getChild(index)
    }

    class Client

    Component <|-- Leaf
    Component <|-- Composite
    Composite *-- Component
    Client --> Component
```

### 8) Class Adapter

```mermaid
classDiagram
    class Target {
      <<interface>>
      +request()
    }

    class Adaptee {
      +specificRequest()
    }

    class Adapter
    class Client

    Target <|.. Adapter
    Adaptee <|-- Adapter
    Client --> Target
```

### 9) Object Adapter

```mermaid
classDiagram
    class Target {
      <<interface>>
      +request()
    }

    class Adaptee {
      +specificRequest()
    }

    class Adapter {
      -adaptee: Adaptee
      +request()
    }

    class Client

    Target <|.. Adapter
    Adapter --> Adaptee
    Client --> Target
```

## Notes

- UML diagrams are written in Mermaid syntax so they render directly on GitHub.
- Pattern names and coverage are aligned with files in the `Revision/` directory.