# RentFlix 🎬

Aplicación de escritorio en Java para gestionar un videoclub: catálogo de películas, copias por formato, alquileres, devoluciones, pagos e informes.

Proyecto integrador de 1.º del Ciclo Formativo de Grado Superior en Desarrollo de Aplicaciones Multiplataforma (DAM) — Universidad Europea de Madrid. Desarrollado con metodología Scrum.

## Funcionalidades

**Invitado**
- Consultar el catálogo de películas disponibles

**Cliente**
- Registro e inicio de sesión
- Alquilar películas eligiendo formato y número de días
- Consultar sus alquileres y los datos de su cuenta

**Empleado**
- Gestionar alquileres y registrar devoluciones
- Añadir películas y gestionar el catálogo
- Consultar informes

**Administrador (empleado jefe)**
- Todo lo del empleado
- Gestionar empleados y clientes (altas, bajas lógicas y bloqueos)

**Otras reglas del negocio**
- Precio según formato: DVD 2,50 €, Blu-ray 5,00 € y 4K 7,50 € por día
- Los alquileres que superan la fecha de devolución se marcan automáticamente como vencidos

## Tecnologías

- Java 17 · Swing con [FlatLaf](https://www.formdev.com/flatlaf/)
- SQLite 3 mediante JDBC
- Arquitectura MVC + patrón DAO
- JUnit para las pruebas
- Git / GitHub · JIRA (Scrum)

## Estructura

```
RentFlix/
├── RentFlix/
│   ├── src/
│   │   ├── main/         → Main.java (arranque)
│   │   ├── model/        → clases del modelo (Pelicula, Copia, Alquiler, Cliente…)
│   │   ├── dao/          → acceso a datos (interfaces + implementaciones, ConexionDB)
│   │   ├── view/         → paneles Swing
│   │   └── controller/   → Controlador.java
│   ├── test/             → pruebas JUnit
│   ├── DB/               → base de datos SQLite y ConfiguracionDB.properties
│   ├── lib/              → librerías (FlatLaf, sqlite-jdbc)
│   ├── javadoc/          → documentación generada
│   └── RentFlix.jar      → ejecutable
├── database/             → scripts SQL (estructura y datos de prueba) y MER
└── diagramas/            → casos de uso, MER y diagrama de clases
```

## Cómo ejecutarlo

Requisito: **Java 17** o superior.

**Con el ejecutable**

Desde la carpeta `RentFlix/` (la que contiene `RentFlix.jar` y la carpeta `DB`):

```bash
java -jar RentFlix.jar
```

> Hay que lanzarlo desde esa carpeta, porque la aplicación busca la base de datos en la ruta relativa `DB/`.

**Desde Eclipse**

1. *File → Import → Existing Projects into Workspace* y selecciona la carpeta `RentFlix/`.
2. Comprueba que `lib/flatlaf-3.7.1.jar` y `lib/sqlite-jdbc-3.51.3.0.jar` están en el *Build Path*.
3. Ejecuta `main/Main.java`.

**Restaurar la base de datos**

Para empezar con datos limpios, ejecuta sobre `DB/rentflix.db` los scripts `database/rentflixBBDD.sql` (estructura) y `database/rentflixINSERTdatos.sql` (datos de prueba).

## Usuarios de prueba

| Rol | Usuario | Contraseña |
|---|---|---|
| Administrador | carlos_admin | 1234 |
| Empleado | laura_emp | 1234 |
| Cliente | ana_cli | 1234 |

## Equipo

| Integrante | Rol Scrum | Responsabilidad |
|---|---|---|
| Ana Belén Rueda Reina | Scrum Master | Capa DAO y documentación |
| Fiorella Ruth Albújar Albino | Cloud Master | Vistas Swing y GitHub |
| Gabriel Fernández Cañadas | Designer | Modelo, controlador y Main |

Product Owner: Pilar (profesora).
