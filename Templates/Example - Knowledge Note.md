---
tags:
  - note
  - note
status: active
created: 2024-02-10
up:
  - - Software Design Patterns
related:
  - - Inversion of Control
---

# Dependency Injection

## Core Idea
> La Inyección de Dependencias (DI) es un patrón de diseño donde un objeto recibe otros objetos de los que depende, en lugar de crearlos internamente.

## Explanation
En la programación tradicional, una clase podría instanciar sus propias dependencias (ej: `this.service = new UserService()`). Esto acopla fuertemente la clase a una implementación específica.

Con DI, la dependencia se pasa (inyecta), usualmente a través del constructor. Esto hace que el código sea más modular, testeable y flexible porque puedes intercambiar implementaciones fácilmente (ej: pasar un `MockUserService` para pruebas).

## Connections
- **Related to:** [[Inversion of Control]] (DI es una forma específica de IoC)
- **Contrast with:** [[Singleton Pattern]] (que a menudo introduce estado global y acoplamiento fuerte)

## Application / Example
```typescript
// Sin DI
class OrderService {
  constructor() {
    this.db = new Database(); // Fuertemente acoplado
  }
}

// Con DI
class OrderService {
  constructor(private db: Database) {} // Bajo acoplamiento
}
// Uso
const db = new PostgresDatabase();
const service = new OrderService(db);
```

## References
- Source: [Martin Fowler sobre DI](https://martinfowler.com/articles/injection.html)
