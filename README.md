#  Arquitectura N-Capas + Patrones de Diseño

| **Capa**              | **Responsabilidad**                                                                 | **Patrones aplicados**                               | **Herramientas / Tecnologías**                |
|------------------------|-------------------------------------------------------------------------------------|------------------------------------------------------|-----------------------------------------------|
| **Presentación (UI)** | Renderizar vistas, manejar interacción del usuario, navegación y estado visual.     | *Component-Based Architecture*, *Container/Presentational Pattern*. | React, TypeScript, Tailwind, Redux Toolkit (slices). |
| **Controladores**      | Orquestar casos de uso y comunicación entre UI y servicios.                         | *Controller Pattern*, *Mediator* (coordina flujos).  | React Hooks + RTK Query (queries/mutations). |
| **Dominio (Entidades + Lógica de negocio)** | Representar reglas del negocio (usuarios, coaches, sesiones).                    | *Domain Model Pattern*, *DTO Pattern*.              | TypeScript (DTOs, Models). |
| **Servicios**          | Lógica de aplicación, acceso a datos y APIs externas.                              | *Service Layer Pattern*, *Dependency Injection*.     | ApiClient, AuthService, SessionService, etc. |
| **Infraestructura**    | Conexiones técnicas (API REST, WebRTC, Socket.io, Auth0).                          | *Adapter Pattern* (ApiClient), *Observer / Pub-Sub* (Socket.io). | WebRTC, Socket.io, Auth0, AWS Cognito, REST API. |
| **Cross-Cutting (Middleware + Validación + Logging)** | Funciones comunes que atraviesan capas (auth, logs, validaciones).                | *Chain of Responsibility* (middlewares), *Decorator* (validadores). | Express middlewares, Yup/Zod, Sentry. |
