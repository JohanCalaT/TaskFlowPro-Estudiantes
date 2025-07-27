# 🎓 TaskFlowPro - Versión del Profesor

## 📋 Descripción

**TaskFlowPro** es un sistema completo de gestión de tareas y equipos desarrollado con **.NET 9**, **Entity Framework Core**, **Aspire** y **Blazor**. Esta es la versión del profesor con todas las implementaciones completas y soluciones a los ejercicios.

## 🏗️ Arquitectura

El proyecto implementa **Arquitectura Limpia (Clean Architecture)** con las siguientes capas:

```
📁 TaskFlowPro/
├── 📁 Backend/
│   ├── 📁 TaskFlowPro.Domain/          # Entidades y reglas de negocio
│   ├── 📁 TaskFlowPro.Application/     # Casos de uso y DTOs
│   ├── 📁 TaskFlowPro.Persistence/     # Entity Framework y repositorios
│   └── 📁 TaskFlowPro.Api/             # Controllers y configuración API
├── 📁 Frontend/
│   └── 📁 TaskFlowPro.Web/             # Aplicación Blazor Server
├── 📁 Orchestration/
│   ├── 📁 TaskFlowPro.AppHost/         # Aspire App Host
│   └── 📁 TaskFlowPro.ServiceDefaults/ # Configuraciones compartidas
└── 📁 Database/
    └── 📁 TaskFlowPro-Database-Kit/    # Scripts de base de datos
```

## 🚀 Tecnologías Utilizadas

- **.NET 9** - Framework principal
- **Entity Framework Core 9** - ORM para base de datos
- **SQL Server** - Base de datos
- **Aspire** - Orquestación y observabilidad
- **Blazor Server** - Frontend interactivo
- **AutoMapper** - Mapeo de objetos
- **JWT Authentication** - Autenticación
- **Scalar** - Documentación de API
- **Clean Architecture** - Patrón arquitectónico

## 📋 Prerrequisitos

Antes de ejecutar el proyecto, asegúrate de tener instalado:

- **.NET 9 SDK** - [Descargar aquí](https://dotnet.microsoft.com/download/dotnet/9.0)
- **SQL Server** (LocalDB, Express o completo)
- **Visual Studio 2022** o **Visual Studio Code**
- **Git** para clonar el repositorio

## 🛠️ Configuración e Instalación

### **Paso 1: Clonar el Repositorio**

```bash
git clone https://github.com/JohanCalaT/TaskFlowPro-Profesor.git
cd TaskFlowPro-Profesor
```

### **Paso 2: Configurar Base de Datos**

**⚠️ IMPORTANTE:** Antes de ejecutar la aplicación, debes configurar la base de datos siguiendo las instrucciones del archivo:

📁 **`Database/TaskFlowPro-Database-Kit/README.md`**

Este archivo contiene:
- ✅ Scripts de creación de base de datos
- ✅ Datos de prueba (seed data)
- ✅ Configuración de conexión
- ✅ Instrucciones paso a paso

### **Paso 3: Configurar Cadena de Conexión**

Edita el archivo `Backend/TaskFlowPro.Api/appsettings.json`:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost,1433;Database=TaskFlowProDB;User Id=sa;Password=TU_PASSWORD;TrustServerCertificate=true;MultipleActiveResultSets=true"
  }
}
```

### **Paso 4: Restaurar Paquetes**

```bash
dotnet restore
```

### **Paso 5: Ejecutar Migraciones**

```bash
dotnet ef database update --project Backend/TaskFlowPro.Persistence --startup-project Backend/TaskFlowPro.Api
```

## 🚀 Ejecutar la Aplicación

### **Opción 1: Con Aspire (Recomendado)**

```bash
dotnet run --project Orchestration/TaskFlowPro.AppHost/TaskFlowPro.AppHost.csproj
```

Esto abrirá:
- 🌐 **Aspire Dashboard** - Panel de control y monitoreo
- 🔗 **API** - Endpoints REST con documentación Scalar
- 🖥️ **Blazor Web** - Interfaz de usuario

### **Opción 2: Solo API**

```bash
dotnet run --project Backend/TaskFlowPro.Api/TaskFlowPro.Api.csproj
```

### **Opción 3: Solo Frontend**

```bash
dotnet run --project Frontend/TaskFlowPro.Web/TaskFlowPro.Web.csproj
```

## 📚 Documentación de API

Una vez ejecutada la aplicación, puedes acceder a:

- **Scalar Documentation**: `https://localhost:7001/scalar/v1`
- **OpenAPI/Swagger**: `https://localhost:7001/swagger`

## 🧪 Probar la Conexión

Para verificar que todo funciona correctamente:

```
GET /api/users/test-connection
```

Este endpoint verifica:
- ✅ Conexión a base de datos
- ✅ Conteo de registros en tablas
- ✅ Estado de la aplicación

## 👥 Funcionalidades Implementadas

### **Gestión de Usuarios**
- ✅ Registro y autenticación
- ✅ Roles (Admin, Manager, Developer, Tester)
- ✅ Perfiles de usuario
- ✅ JWT Authentication

### **Gestión de Equipos**
- ✅ Crear y administrar equipos
- ✅ Asignar líderes de equipo
- ✅ Gestionar miembros

### **Gestión de Tareas**
- ✅ Crear, editar y eliminar tareas
- ✅ Asignar tareas a usuarios
- ✅ Estados de tareas (Pendiente, En Progreso, Completada)
- ✅ Prioridades (Baja, Media, Alta, Crítica)

### **Dashboard y Reportes**
- ✅ Panel de control interactivo
- ✅ Estadísticas en tiempo real
- ✅ Filtros y búsquedas

## 🔧 Configuración Adicional

### **Variables de Entorno**

Puedes configurar variables de entorno en `appsettings.json`:

```json
{
  "JwtSettings": {
    "SecretKey": "TaskFlowPro_SuperSecretKey_2024!_MinimumLength32Characters",
    "ExpiryInHours": 24
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.EntityFrameworkCore": "Information"
    }
  }
}
```

## 🐛 Solución de Problemas

### **Error de Conexión a Base de Datos**
1. Verificar que SQL Server esté ejecutándose
2. Confirmar credenciales en `appsettings.json`
3. Ejecutar el endpoint `/api/users/test-connection`

### **Error de Migración**
```bash
dotnet ef migrations add InitialCreate --project Backend/TaskFlowPro.Persistence --startup-project Backend/TaskFlowPro.Api
dotnet ef database update --project Backend/TaskFlowPro.Persistence --startup-project Backend/TaskFlowPro.Api
```

### **Puerto en Uso**
Cambiar puertos en `Orchestration/TaskFlowPro.AppHost/Program.cs`

## 📖 Recursos Adicionales

- 📁 **Database/TaskFlowPro-Database-Kit/** - Kit completo de base de datos
- 📄 **Documentación de API** - Disponible en `/scalar/v1`
- 🎯 **Casos de Uso** - Implementados en `Backend/TaskFlowPro.Application/`

## 👨‍🏫 Para Profesores

Esta versión incluye:
- ✅ **Todas las implementaciones completas**
- ✅ **Comentarios explicativos en el código**
- ✅ **Ejemplos de mejores prácticas**
- ✅ **Patrones de diseño implementados**
- ✅ **Casos de prueba y validaciones**

## 📞 Soporte

Para dudas o problemas:
- 📧 **Email**: [tu-email@universidad.edu]
- 💬 **Issues**: Crear issue en este repositorio
- 📚 **Documentación**: Ver carpeta `docs/`

---

**Desarrollado con ❤️ para fines educativos**
