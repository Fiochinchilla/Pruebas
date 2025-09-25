#  Arquitectura N-Capas + Patrones de Diseño

| **Capa**              | **Responsabilidad**                                                                 | **Patrones aplicados**                               | **Herramientas / Tecnologías**                |
|------------------------|-------------------------------------------------------------------------------------|------------------------------------------------------|-----------------------------------------------|
| **Presentación (UI)** | Renderizar vistas, manejar interacción del usuario, navegación y estado visual.     | *Component-Based Architecture*, *Container/Presentational Pattern*. | React, TypeScript, Tailwind, Redux Toolkit (slices). |
| **Controladores**      | Orquestar casos de uso y comunicación entre UI y servicios.                         | *Controller Pattern*, *Mediator* (coordina flujos).  | React Hooks + RTK Query (queries/mutations). |
| **Dominio (Entidades + Lógica de negocio)** | Representar reglas del negocio (usuarios, coaches, sesiones).                    | *Domain Model Pattern*, *DTO Pattern*.              | TypeScript (DTOs, Models). |
| **Servicios**          | Lógica de aplicación, acceso a datos y APIs externas.                              | *Service Layer Pattern*, *Dependency Injection*.     | ApiClient, AuthService, SessionService, etc. |
| **Infraestructura**    | Conexiones técnicas (API REST, WebRTC, Socket.io, Auth0).                          | *Adapter Pattern* (ApiClient), *Observer / Pub-Sub* (Socket.io). | WebRTC, Socket.io, Auth0, AWS Cognito, REST API. |
| **Cross-Cutting (Middleware + Validación + Logging)** | Funciones comunes que atraviesan capas (auth, logs, validaciones).                | *Chain of Responsibility* (middlewares), *Decorator* (validadores). | Express middlewares, Yup/Zod, Sentry. |


### Capas y responsabilidades

| Capa | Ubicación | Responsabilidad | Patrones aplicados |
|------|----------|----------------|-----------------|
| Presentación (UI) | [`/src/components`](https://github.com/Javo294/caso1DS/tree/main/src/components) | Renderiza vistas, interacción del usuario y navegación | Contenedor/Presentativo |
| Contenedores | [`/src/containers`](https://github.com/Javo294/caso1DS/tree/main/src/containers) | Combina componentes UI con controladores | Patrón Contenedor |
| Controladores | [`/src/controllers`](https://github.com/Javo294/caso1DS/tree/main/src/controllers) | Orquesta casos de uso y comunicación con servicios | Mediator, Hook-based |
| Modelos | [`/src/models`](https://github.com/Javo294/caso1DS/tree/main/src/models) | Entidades del dominio central | DTO, Strategy (validaciones) |
| DTOs | [`/src/dto`](https://github.com/Javo294/caso1DS/tree/main/src/dto) | Contratos de intercambio de datos con API | DTO |
| Servicios | [`/src/services`](https://github.com/Javo294/caso1DS/tree/main/src/services) | Lógica de negocio y llamadas a APIs | Service, Dependency Injection |
| Store | [`/src/store`](https://github.com/Javo294/caso1DS/tree/main/src/store) | Gestión de estados globales | Redux Toolkit slices |
| API | [`/src/api`](https://github.com/Javo294/caso1DS/tree/main/src/api) | Clientes para APIs externas y Auth | Adapter, Proxy |
| Listeners | [`/src/listeners`](https://github.com/Javo294/caso1DS/tree/main/src/listeners) | WebSockets, eventos en tiempo real | Observer / Pub-Sub |
| Middleware | [`/src/middleware`](https://github.com/Javo294/caso1DS/tree/main/src/middleware) | Interceptores de request/responses, logging, auth | Chain of Responsibility |
| Excepciones | [`/src/exceptions`](https://github.com/Javo294/caso1DS/tree/main/src/exceptions) | Manejo estandarizado de errores | Template Method |
| Utils | [`/src/utils`](https://github.com/Javo294/caso1DS/tree/main/src/utils) | Funciones y helpers compartidos (logger, constantes, formateos) | Singleton (logger) |
| Estilos | [`/src/styles`](https://github.com/Javo294/caso1DS/tree/main/src/styles) | Configuración de Tailwind, themes | - |
| Validators | [`/src/validators`](https://github.com/Javo294/caso1DS/tree/main/src/validators) | Validación de modelos y DTOs | Decorator |

---


### Ubicación
- Hooks: [`/src/hooks/useNotifications.ts`](https://github.com/Javo294/caso1DS/blob/main/src/hooks/useNotifications.ts)
- Listeners: [`/src/listeners`](https://github.com/Javo294/caso1DS/tree/main/src/listeners)
- Servicios: [`/src/services/socket.ts`](https://github.com/Javo294/caso1DS/blob/main/src/services/socket.ts)




  - [`/src/listeners/websocket.ts`](https://github.com/Javo294/caso1DS/blob/main/src/listeners/websocket.ts)  


  - [`.eslintrc.js`](https://github.com/Javo294/caso1DS/blob/main/.eslintrc.js)  
  - [`.prettierrc`](https://github.com/Javo294/caso1DS/blob/main/.prettierrc)  








- **Location:** [`/src/services`](https://github.com/Javo294/caso1DS/tree/main/src/services)  

- **Examples:**  
  - [`CoachService.ts`](https://github.com/Javo294/caso1DS/blob/main/src/services/CoachService.ts)  
  - [`SessionService.ts`](https://github.com/Javo294/caso1DS/blob/main/src/services/SessionService.ts)
 

- **File:** [`/src/exceptions`](https://github.com/Javo294/caso1DS/tree/main/src/exceptions)  

- **Classes:**  
  - [`BaseException.ts`](https://github.com/Javo294/caso1DS/blob/main/src/exceptions/BaseException.ts) → abstract base class for custom errors.  
  - [`AuthException.ts`](https://github.com/Javo294/caso1DS/blob/main/src/exceptions/AuthException.ts) → handles authentication/authorization errors.  
  - [`SessionException.ts`](https://github.com/Javo294/caso1DS/blob/main/src/exceptions/BaseException.ts) *(can be extended as needed for session domain errors).*  




- **Location:** [`/src/middleware`](https://github.com/Javo294/caso1DS/tree/main/src/middleware)  

- **Examples:**  
  - [`authMiddleware.ts`](https://github.com/Javo294/caso1DS/blob/main/src/middleware/authMiddleware.ts) → validates authentication & permissions.  
  - [`logMiddleware.ts`](https://github.com/Javo294/caso1DS/blob/main/src/middleware/logMiddleware.ts) → structured logging for requests and state changes.  
  - [`errorMiddleware.ts`](https://github.com/Javo294/caso1DS/blob/main/src/middleware/errorMiddleware.ts) → catches and forwards errors.
 


### Files
- [`CoachValidator.ts`](https://github.com/Javo294/caso1DS/blob/main/src/validators/CoachValidator.ts)
- [`SessionValidator.ts`](https://github.com/Javo294/caso1DS/blob/main/src/validators/SessionValidator.ts)

 
 
 
 - **CI File:** [`.github/workflows/ci.yml`](https://github.com/Javo294/caso1DS/blob/main/.github/workflows/ci.yml)





---------------------------

### Location
- [`/src/dto`](https://github.com/Javo294/caso1DS/tree/main/src/dto)

### Purpose
DTOs define the structure of the data that moves between the frontend and backend. They enforce contracts, ensure type safety, and simplify data transformations.

### Examples
- [`CoachDTO.ts`](https://github.com/Javo294/caso1DS/blob/main/src/dto/CoachDTO.ts)
- [`SessionDTO.ts`](https://github.com/Javo294/caso1DS/blob/main/src/dto/SessionDTO.ts)

### Transformation Example




------------------------


## State Management / Store

### Location
- [`/src/store`](https://github.com/Javo294/caso1DS/tree/main/src/store)

### Purpose
Manage global state in a predictable way using Redux Toolkit slices and hooks. Each slice is responsible for a specific domain (Auth, Coach, Session).

### Slices
- [`useAuthStore.ts`](https://github.com/Javo294/caso1DS/blob/main/src/store/useAuthStore.ts)
- [`useCoachStore.ts`](https://github.com/Javo294/caso1DS/blob/main/src/store/useCoachStore.ts)
- [`useSessionStore.ts`](https://github.com/Javo294/caso1DS/blob/main/src/store/useSessionStore.ts)



----------------------------------------------
### Location
- [`/src/styles`](https://github.com/Javo294/caso1DS/tree/main/src/styles)

### Purpose
Manage global styles, themes, and responsive design using Tailwind CSS.

### Files
- [`index.css`](https://github.com/Javo294/caso1DS/blob/main/src/styles/index.css) → Global CSS import, Tailwind base, components, and utilities.
- [`tailwind.config.ts`](https://github.com/Javo294/caso1DS/blob/main/src/styles/tailwind.config.ts) → Tailwind configuration, custom colors, breakpoints, and plugins.
- [`themes.ts`](https://github.com/Javo294/caso1DS/blob/main/src/styles/themes.ts) → Theme definitions, e.g., dark/light mode, shared colors, font sizes.



---------------------------


### Files and Examples

- [`constants.ts`](https://github.com/Javo294/caso1DS/blob/main/src/utils/constants.ts)  
  Contains global constants for the application.
Aquí va el código guía para el programador, falta agregarlo

- [`formatTime.ts`](https://github.com/Javo294/caso1DS/blob/main/src/utils/formatTime.ts)  
  Utility functions for formatting date and time.
Aquí va el código guía para el programador, falta agregarlo

- [`logger.ts`](https://github.com/Javo294/caso1DS/blob/main/src/utils/logger.ts)  
  Singleton logger for application-wide logging using Sentry.
Aquí va el código guía para el programador, falta agregarlo




