# gymSystem
Este repositorio contiene una API desarrollada en .NET 8 utilizando la **Clean Architecture** para un sistema de gestión de gimnasio. La arquitectura limpia facilita la escalabilidad, mantenibilidad y testeabilidad del código, asegurando una separación clara de responsabilidades.

## Estructura del Proyecto
La solución está organizada en varios proyectos con responsabilidades bien definidas:

### 1. **Application Core (`GymSystem.Core`)**

El **Application Core** es el núcleo de la aplicación y contiene la lógica de negocio y las reglas de negocio. Esta capa no depende de ninguna otra capa y es independiente de cualquier framework o tecnología externa.

- **Entities**: Clases que representan los modelos de negocio (`User`, `Membership`, `Transaction`, `Discount`, etc.).
- **Aggregates**: Grupos de entidades que son tratadas como una sola unidad para las operaciones de negocio.
- **Interfaces**: Definición de interfaces para repositorios y servicios.
- **Domain Services**: Contiene lógica de negocio que no pertenece a una sola entidad.
- **Specifications**: Patrones para encapsular criterios de consultas.
- **Custom Exceptions and Guard Clauses**: Excepciones personalizadas y validaciones específicas de negocio.
- **Domain Events and Handlers**: Manejo de eventos de dominio para implementar patrones de eventos.

### 2. **Infrastructure (`GymSystem.Infrastructure`)**

La capa de **Infrastructure** contiene las implementaciones de las interfaces definidas en la capa de Application Core. Esta capa se comunica con recursos externos, como bases de datos, servicios de archivos, etc.

- **EF Core types (DbContext, Migration)**: Contiene el contexto de base de datos y migraciones de Entity Framework Core.
- **Data Access Implementation Types (Repositories)**: Implementaciones de los repositorios que interactúan con la base de datos.
- **Infrastructure-specific Services**: Servicios específicos de la infraestructura como `FileLogger`, `EmailSender`, etc.

### 3. **UI Layer (`GymSystem.API`)**

La capa de **UI (API Layer)** es la entrada de la aplicación y contiene la API pública. Interactúa con el Application Core a través de interfaces.

- **Controllers**: Controladores que exponen los endpoints de la API.
- **ViewModels**: Modelos de vista para transmitir datos entre la UI y la lógica de aplicación.
- **Custom Filters**: Filtros personalizados para manejo de excepciones, autenticación, autorización, etc.
- **Middleware**: Middleware personalizado para manejar diferentes aspectos de la solicitud HTTP.

### 4. **Configuración de `Program.cs` (Startup)**

El archivo `Program.cs` (anteriormente `Startup.cs`) es responsable de configurar el contenedor de dependencias y otros aspectos de la aplicación.

### 5. **Pruebas Unitarias**

Los proyectos de pruebas están organizados para cubrir cada capa del sistema:

- **`GymSystem.Core.Tests`**: Pruebas unitarias para entidades y servicios de la lógica de negocio.
- **`GymSystem.Infrastructure.Tests`**: Pruebas de integración para la infraestructura de datos.
- **`GymSystem.API.Tests`**: Pruebas unitarias y de integración para los controladores de la API.

## Requisitos Previos

- [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
- [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads) (u otro proveedor de bases de datos compatible con EF Core)
- Visual Studio 2022 o Visual Studio Code

## Configuración del Proyecto

1. **Clonar el repositorio**:

   ```bash
   git clone https://github.com/tu-usuario/MyGymApp.git
   cd MyGymApp
