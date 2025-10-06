# Guía de configuración rápida

Este documento explica cómo preparar y ejecutar el skeleton modular Spring Boot.

## 1️⃣ Clonar el repositorio

```bash
git clone https://github.com/<usuario>/skeleton.git
cd skeleton
```

## 2️⃣ Compilar todos los módulos

```bash
./gradlew clean build
```

- Esto compila todos los submódulos (bootstrap, application, domain, infrastructure, shared-kernel) y ejecuta los tests.

## 3️⃣ Ejecutar la aplicación

El **entry point** es el módulo `bootstrap`:

```bash
./gradlew :bootstrap:bootRun
```

- Spring Boot inicializará todos los módulos transitivamente.

## 4️⃣ Recomendaciones

- Refrescar Gradle en IntelliJ después de clonar el proyecto.
- Usar Java 17 o superior.
- Asegurarse de que `settings.gradle` incluye todos los módulos:

```gradle
include(
"bootstrap",
"application",
"domain",
"infrastructure",
"shared-kernel"
)
```
