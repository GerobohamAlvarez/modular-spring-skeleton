# Arquitectura Modular

Skeleton basado en **Clean Architecture**:

```
shared-kernel  --->  domain  --->  application  --->  infrastructure
^                                                           ^
|                                                           |
+-----------------------------------------------------------+
                            bootstrap
```

- **shared-kernel** → objetos y utilidades reutilizables (Value Objects, enums, exceptions).
- **domain** → entidades y reglas de negocio puras.
- **application** → casos de uso y lógica de aplicación.
- **infrastructure** → repositorios, adapters, Beans de Spring.
- **bootstrap** → entry point, arranca Spring Boot y carga los módulos.

# Módulo Bootstrap

- Entry point de la aplicación.
- Clase principal: `BootstrapApplication` con `@SpringBootApplication`.
- Dependencias: application, infrastructure, shared-kernel.

# Módulo Application

- Contiene casos de uso y lógica de aplicación.
- No tiene acceso directo a la infraestructura.
- Dependencias: domain, shared-kernel.

# Módulo Domain

- Entidades y reglas de negocio puras.
- Dependencias: shared-kernel.


# Módulo Infrastructure

- Implementa adapters, repositorios y beans de Spring Boot.
- No contiene `@SpringBootApplication`.
- Dependencias: application, shared-kernel.
- `bootJar` deshabilitado (enabled = false).

# Módulo Shared Kernel

- Contiene objetos y utilidades reutilizables (Value Objects, enums, exceptions).
- No depende de ningún módulo.
