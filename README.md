# CRM API Challenge - The Agile Monkeys

Este proyecto implementa una API RESTful para gestionar usuarios y clientes utilizando arquitectura hexagonal, seguridad JWT y documentación OpenAPI.

---

## ✅ Tecnologías usadas

- Java 17
- Spring Boot 3
- Spring Security
- JWT (Json Web Tokens)
- Spring Data JPA + H2
- OpenAPI Generator + Swagger
- Arquitectura Hexagonal
- Docker y GitHub Actions (opcional)

---

## 🚀 Cómo ejecutar el proyecto

### Requisitos:
- JDK 17
- Maven 3.8+
- (Opcional) Docker

### Ejecutar localmente:
```bash
mvn clean compile spring-boot:run
```

### Acceder a Swagger:
[http://localhost:8080/swagger-ui/index.html](http://localhost:8080/swagger-ui/index.html)

---

## 🔐 Endpoints de autenticación

| Método | Endpoint         | Descripción             |
|--------|------------------|-------------------------|
| POST   | `/auth/register` | Registro de usuario     |
| POST   | `/auth/login`    | Login y obtener JWT     |

---

## 👥 Endpoints de clientes

| Método | Endpoint           | Descripción               |
|--------|--------------------|---------------------------|
| GET    | `/customers`       | Listar todos los clientes |
| GET    | `/customers/{id}`  | Obtener cliente por ID    |
| POST   | `/customers`       | Crear cliente             |
| PUT    | `/customers/{id}`  | Actualizar cliente        |
| DELETE | `/customers/{id}`  | Eliminar cliente          |

> 🔐 Todos requieren JWT excepto `/auth/*`.

---

## 🎭 Roles y autorización

| Rol        | Permisos                                                     |
|------------|--------------------------------------------------------------|
| `ROLE_USER` | Ver, crear, actualizar y eliminar sus clientes              |
| `ROLE_ADMIN` | Acceso total (usuarios, roles, clientes, administración)   |

- Los usuarios nuevos se registran como `ROLE_USER` por defecto.
- El rol se asigna en base al campo `admin` en la base de datos.
- El sistema puede extenderse fácilmente con `@PreAuthorize`.

---

## 🧱 Arquitectura Hexagonal

```text
domain/
├── model
├── port
│   ├── in
│   └── out

application/
└── service

infrastructure/
├── controller (REST)
├── security (JWT)
├── persistence (JPA + Adapter)
```

---

## 📦 Generación automática con OpenAPI

```bash
mvn openapi-generator:generate
```

Genera:
- Interfaces `AuthApi`, `CustomersApi`
- Modelos `LoginRequest`, `JwtResponse`, etc.

---

## 🧪 Pruebas
Puedes usar Postman o Swagger para probar los endpoints:
1. Registrar usuario (`/auth/register`)
2. Hacer login (`/auth/login`) y copiar el token
3. Usar el token en el header:  
   `Authorization: Bearer <token>`

---

## 📝 Licencia

MIT © 2025 - Construido para The Agile Monkeys Challenge.
