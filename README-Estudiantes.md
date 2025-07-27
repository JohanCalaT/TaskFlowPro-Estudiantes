# 👥 TaskFlowPro - Proyecto para Estudiantes

## 📋 Descripción del Proyecto

¡Bienvenidos al proyecto **TaskFlowPro**! 🎉

En este proyecto desarrollarás un sistema completo de gestión de tareas y equipos utilizando las tecnologías más modernas de **.NET 9**. Aprenderás a implementar **Arquitectura Limpia**, trabajar con **Entity Framework Core**, crear APIs REST y desarrollar interfaces con **Blazor**.

## 🎯 Objetivos de Aprendizaje

Al completar este proyecto, habrás aprendido:

- ✅ **Arquitectura Limpia** - Separación de responsabilidades
- ✅ **Entity Framework Core** - ORM y manejo de base de datos
- ✅ **API REST** - Creación de endpoints y documentación
- ✅ **Autenticación JWT** - Seguridad en aplicaciones web
- ✅ **Blazor Server** - Desarrollo de interfaces interactivas
- ✅ **Aspire** - Orquestación y observabilidad
- ✅ **Patrones de Diseño** - Repository, Unit of Work, CQRS
- ✅ **Mejores Prácticas** - Clean Code y SOLID

## 🏗️ Arquitectura del Proyecto

```
📁 TaskFlowPro/
├── 📁 Backend/
│   ├── 📁 TaskFlowPro.Domain/          # 🏛️ Entidades y reglas de negocio
│   ├── 📁 TaskFlowPro.Application/     # 🎯 Casos de uso y DTOs
│   ├── 📁 TaskFlowPro.Persistence/     # 💾 Entity Framework y repositorios
│   └── 📁 TaskFlowPro.Api/             # 🌐 Controllers y configuración API
├── 📁 Frontend/
│   └── 📁 TaskFlowPro.Web/             # 🖥️ Aplicación Blazor Server
├── 📁 Orchestration/
│   ├── 📁 TaskFlowPro.AppHost/         # 🎭 Aspire App Host
│   └── 📁 TaskFlowPro.ServiceDefaults/ # ⚙️ Configuraciones compartidas
└── 📁 Database/
    └── 📁 TaskFlowPro-Database-Kit/    # 🗄️ Scripts de base de datos
```

## 📋 Prerrequisitos

Antes de comenzar, asegúrate de tener instalado:

- **.NET 9 SDK** - [Descargar aquí](https://dotnet.microsoft.com/download/dotnet/9.0)
- **SQL Server** (LocalDB, Express o completo)
- **Visual Studio 2022** o **Visual Studio Code**
- **Git** para clonar el repositorio

## 🚀 Configuración Inicial

### **Paso 1: Clonar el Repositorio**

```bash
git clone https://github.com/JohanCalaT/TaskFlowPro-Estudiantes.git
cd TaskFlowPro-Estudiantes
```

### **Paso 2: ⚠️ CONFIGURAR BASE DE DATOS (OBLIGATORIO)**

**🔴 IMPORTANTE:** Antes de hacer cualquier otra cosa, debes configurar la base de datos siguiendo las instrucciones del archivo:

📁 **`Database/TaskFlowPro-Database-Kit/README.md`**

Este archivo contiene:
- 📝 **Instrucciones paso a paso** para configurar SQL Server
- 🗄️ **Scripts de creación** de base de datos
- 🌱 **Datos de prueba** (usuarios, roles, equipos)
- 🔗 **Configuración de conexión**
- 🛠️ **Solución de problemas** comunes

**⚠️ NO CONTINÚES sin completar este paso primero.**

### **Paso 3: Configurar Cadena de Conexión**

Edita el archivo `Backend/TaskFlowPro.Api/appsettings.json` con tus credenciales:

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

### **Paso 5: Verificar Configuración**

Ejecuta la aplicación para verificar que todo funciona:

```bash
dotnet run --project Orchestration/TaskFlowPro.AppHost/TaskFlowPro.AppHost.csproj
```

Luego visita: `https://localhost:7001/api/users/test-connection`

Si ves un mensaje de éxito, ¡estás listo para comenzar! 🎉

## 📚 Ejercicios y TODOs

Este proyecto contiene ejercicios marcados con comentarios `// TODO:` que debes completar. Los ejercicios están organizados por dificultad:

### **🟢 Nivel Básico**
- Implementar métodos CRUD básicos
- Configurar AutoMapper profiles
- Crear validaciones simples

### **🟡 Nivel Intermedio**
- Implementar autenticación JWT
- Crear filtros y búsquedas
- Manejar relaciones entre entidades

### **🔴 Nivel Avanzado**
- Implementar patrones de diseño
- Crear middleware personalizado
- Optimizar consultas de base de datos

## 🛠️ Cómo Ejecutar el Proyecto

### **Opción 1: Con Aspire (Recomendado)**

```bash
dotnet run --project Orchestration/TaskFlowPro.AppHost/TaskFlowPro.AppHost.csproj
```

Esto abrirá:
- 🎭 **Aspire Dashboard** - Panel de control
- 🌐 **API** - `https://localhost:7001`
- 🖥️ **Blazor Web** - `https://localhost:7002`

### **Opción 2: Solo API**

```bash
dotnet run --project Backend/TaskFlowPro.Api/TaskFlowPro.Api.csproj
```

### **Opción 3: Solo Frontend**

```bash
dotnet run --project Frontend/TaskFlowPro.Web/TaskFlowPro.Web.csproj
```

## 📖 Documentación de API

Una vez ejecutada la aplicación:

- **Scalar Documentation**: `https://localhost:7001/scalar/v1`
- **Swagger UI**: `https://localhost:7001/swagger`

## 🧪 Endpoints de Prueba

### **Verificar Conexión**
```
GET /api/users/test-connection
```

### **Autenticación**
```
POST /api/auth/login
POST /api/auth/register
```

### **Gestión de Usuarios**
```
GET /api/users
POST /api/users
PUT /api/users/{id}
DELETE /api/users/{id}
```

## 📝 Guía de Desarrollo

### **1. Estructura de Carpetas**

Cada capa tiene una responsabilidad específica:

- **Domain**: Entidades y reglas de negocio
- **Application**: Casos de uso, DTOs y servicios
- **Persistence**: Acceso a datos con Entity Framework
- **Api**: Controllers y configuración web

### **2. Patrones Implementados**

- **Repository Pattern**: Para acceso a datos
- **Unit of Work**: Para transacciones
- **Dependency Injection**: Para inversión de control
- **AutoMapper**: Para mapeo de objetos

### **3. Convenciones de Código**

- Usar **PascalCase** para clases y métodos
- Usar **camelCase** para variables
- Agregar comentarios XML para documentación
- Seguir principios **SOLID**

## 🎯 Entregables

### **Entrega 1: Configuración Base**
- [ ] Configurar base de datos
- [ ] Ejecutar aplicación exitosamente
- [ ] Probar endpoint de conexión

### **Entrega 2: API Básica**
- [ ] Implementar CRUD de usuarios
- [ ] Configurar AutoMapper
- [ ] Crear validaciones

### **Entrega 3: Autenticación**
- [ ] Implementar JWT
- [ ] Crear middleware de autenticación
- [ ] Proteger endpoints

### **Entrega 4: Funcionalidades Avanzadas**
- [ ] Gestión de equipos
- [ ] Gestión de tareas
- [ ] Dashboard con estadísticas

## 🆘 Ayuda y Recursos

### **Documentación Útil**
- [.NET 9 Documentation](https://docs.microsoft.com/dotnet/)
- [Entity Framework Core](https://docs.microsoft.com/ef/core/)
- [Blazor Documentation](https://docs.microsoft.com/aspnet/core/blazor/)

### **Solución de Problemas Comunes**

**Error de conexión a base de datos:**
1. Verificar que SQL Server esté ejecutándose
2. Revisar credenciales en `appsettings.json`
3. Ejecutar `/api/users/test-connection`

**Error de compilación:**
```bash
dotnet clean
dotnet restore
dotnet build
```

**Puerto en uso:**
Cambiar puertos en `launchSettings.json`

## 📞 Soporte

¿Necesitas ayuda?

- 💬 **Crear Issue** en este repositorio
- 📧 **Email al profesor**: [profesor@universidad.edu]
- 👥 **Foro de la clase**: [enlace-al-foro]

## 🏆 Criterios de Evaluación

- **Funcionalidad** (40%): ¿El código funciona correctamente?
- **Calidad de Código** (30%): ¿Sigue buenas prácticas?
- **Arquitectura** (20%): ¿Respeta la arquitectura limpia?
- **Documentación** (10%): ¿Está bien documentado?

## 🎉 ¡Comienza tu Aventura!

¡Estás listo para comenzar! Recuerda:

1. 📖 **Lee toda la documentación** antes de empezar
2. 🗄️ **Configura la base de datos** siguiendo el kit
3. 🧪 **Prueba cada funcionalidad** que implementes
4. 💬 **Pregunta si tienes dudas**
5. 🎯 **Diviértete aprendiendo**

---

**¡Buena suerte y que disfrutes programando! 🚀**
