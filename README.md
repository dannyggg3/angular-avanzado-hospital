# AdminPro - Sistema de Gestión Hospital

## 📋 Descripción

**AdminPro** es un sistema integral de administración hospitalaria desarrollado con Angular 5. Proporciona una plataforma completa para la gestión de usuarios, hospitales, médicos y recursos, con autenticación robusta mediante JWT y Google OAuth 2.0. Diseñado para facilitar las operaciones administrativas del sector salud con una interfaz moderna y responsive.

## 🚀 Tipo de Proyecto

**Sistema de Gestión Administrativa para Hospitales** - Aplicación Web SPA

## 🛠️ Tecnologías Utilizadas

- **Angular 5.0.0** - Framework frontend
- **TypeScript 2.4.2** - Lenguaje de programación
- **RxJS 5.5.2** - Programación reactiva
- **Node.js** - Entorno de ejecución
- **HTML5 / CSS3 / SCSS** - Estructura y estilos
- **MongoDB** - Base de datos (inferida por uso de _id)

## 📚 Frameworks y Librerías

### UI/UX
- **ng2-charts 1.6.0** - Gráficos interactivos basados en Chart.js
- **SweetAlert 2.1.0** - Alertas y diálogos personalizados
- **Bootstrap** - Framework CSS responsive
- **Font Awesome** - Iconos

### Autenticación
- **Google OAuth 2.0** - Autenticación social
- **JWT** - Tokens de autenticación

### Testing
- **Jasmine ~2.6.2** - Framework de testing unitario
- **Karma ~1.7.0** - Test runner
- **Protractor ~5.1.2** - Testing E2E

### Herramientas de Desarrollo
- **Angular CLI 1.6.1** - Herramienta de desarrollo
- **TSLint ~5.7.0** - Linter de TypeScript
- **Codelyzer** - Reglas de linting para Angular

## 🏗️ Arquitectura

### Patrón Arquitectónico: MVC Modular + Servicios Inyectables

La aplicación implementa una arquitectura en capas con separación de responsabilidades:

```
┌──────────────────────────────────────────────┐
│       CAPA DE PRESENTACIÓN (Views)          │
│  Dashboard | Usuarios | Hospitales | etc.   │
└─────────────────────┬────────────────────────┘
                      ↓
┌─────────────────────┴────────────────────────┐
│      COMPONENTES COMPARTIDOS (Shared)       │
│    Header | Sidebar | Breadcrumbs | 404    │
└─────────────────────┬────────────────────────┘
                      ↓
┌─────────────────────┴────────────────────────┐
│       CAPA DE SERVICIOS (Services)          │
│  Usuario | Hospital | Médico | Auth        │
└─────────────────────┬────────────────────────┘
                      ↓
┌─────────────────────┴────────────────────────┐
│     GUARDS (Protección de Rutas)            │
│  LoginGuard | AdminGuard | VerificaToken   │
└─────────────────────┬────────────────────────┘
                      ↓
┌─────────────────────┴────────────────────────┐
│      MODELOS DE DATOS (TypeScript)          │
│     Usuario | Hospital | Médico             │
└─────────────────────┬────────────────────────┘
                      ↓
┌─────────────────────┴────────────────────────┐
│          HTTP CLIENT (Angular)              │
│        Comunicación con API REST            │
└─────────────────────┬────────────────────────┘
                      ↓
┌─────────────────────┴────────────────────────┐
│            BACKEND API REST                 │
│      (Node.js/Express + MongoDB)            │
│        http://localhost:3000                │
└──────────────────────────────────────────────┘
```

### Patrones Implementados
- **MVC (Model-View-Controller)** - Separación de lógica y presentación
- **Inyección de Dependencias** - Servicios singleton
- **Guards de Rutas** - Protección basada en roles
- **Pipes Personalizados** - Transformación de datos
- **Observable Pattern** - Manejo de datos asíncronos

## 📁 Estructura del Proyecto

```
angular-avanzado-hospital/
├── src/
│   ├── app/
│   │   ├── pages/              # Páginas principales
│   │   │   ├── dashboard/
│   │   │   ├── usuarios/
│   │   │   ├── hospitales/
│   │   │   ├── medicos/
│   │   │   ├── busqueda/
│   │   │   └── profile/
│   │   ├── login/              # Autenticación
│   │   ├── services/           # 8+ servicios
│   │   │   ├── guards/         # 3 guards
│   │   │   ├── usuario/
│   │   │   ├── hospital/
│   │   │   └── medico/
│   │   ├── models/             # Modelos TypeScript
│   │   ├── shared/             # Componentes compartidos
│   │   ├── components/         # Componentes reutilizables
│   │   └── pipes/              # Pipes personalizados
│   ├── assets/                 # Recursos estáticos
│   └── environments/           # Configuración por ambiente
├── .angular-cli.json
├── tsconfig.json
└── package.json
```

## ✨ Características Principales

### 🔐 Autenticación y Seguridad
- **Login Local**: Email/contraseña con JWT
- **Google OAuth 2.0**: Autenticación social integrada
- **Renovación Automática de Tokens**: Sistema de refresh tokens
- **Guards de Rutas**: Protección basada en roles
  - `LoginGuard`: Verifica autenticación
  - `AdminGuard`: Solo administradores
  - `VerificaTokenGuard`: Valida integridad del token
- **Opción "Recuérdame"**: Persistencia en localStorage

### 👥 Gestión de Usuarios
- CRUD completo de usuarios
- Paginación de resultados
- Búsqueda en tiempo real
- Gestión de roles (Admin/Usuario)
- Carga de foto de perfil
- Prevención de auto-eliminación

### 🏥 Gestión de Hospitales
- Crear, editar y eliminar hospitales
- Listado completo
- Búsqueda avanzada
- Gestión de logo/imagen
- Vinculación con médicos

### 👨‍⚕️ Gestión de Médicos
- CRUD de médicos
- Asociación con hospitales
- Vinculación con usuarios
- Búsqueda por nombre
- Carga de foto profesional

### 🔍 Búsqueda Avanzada
- Búsqueda unificada multi-colección
- Resultados de usuarios, hospitales y médicos
- Búsqueda en tiempo real

### 📊 Dashboard y Visualización
- Panel principal con métricas
- Gráficos interactivos (ng2-charts)
- Componente de gráfico dona reutilizable
- Visualización de datos en tiempo real

### 📸 Gestión de Archivos
- Modal de carga de archivos
- Upload de imágenes para:
  - Usuarios (foto de perfil)
  - Hospitales (logo)
  - Médicos (foto profesional)
- Servicio centralizado de carga

### 🎨 Componentes Reutilizables
- **Incrementador**: Input numérico con botones +/-
- **Gráfico Dona**: Componente de gráfico personalizado
- **Modal Upload**: Diálogo de carga de archivos
- **Header**: Navegación con datos de usuario
- **Sidebar**: Menú dinámico según roles
- **Breadcrumbs**: Navegación por migas de pan
- **404 Page**: Página de error personalizada

### 🎯 Configuración de Tema
- Cambio dinámico de tema visual
- Estilos personalizables
- Almacenamiento de preferencias

## 🔧 Instalación

### Prerrequisitos

- Node.js (v8 o superior)
- npm (v5 o superior)
- Angular CLI 1.6.1

```bash
npm install -g @angular/cli@1.6.1
```

### Pasos

1. Clonar el repositorio
```bash
git clone https://github.com/dannyggg3/angular-avanzado-hospital.git
cd angular-avanzado-hospital
```

2. Instalar dependencias
```bash
npm install
```

3. Configurar Google OAuth (opcional)
```typescript
// Editar src/index.html
// Reemplazar el CLIENT_ID con tu Google App ID
<meta name="google-signin-client_id" content="TU_CLIENT_ID.apps.googleusercontent.com">
```

4. Configurar URL del backend
```typescript
// Editar src/app/config/config.ts
export const URL_SERVICIOS = 'http://localhost:3000';
```

5. Iniciar el servidor de desarrollo
```bash
ng serve
```

6. Abrir en navegador
```
http://localhost:4200
```

## 💻 Uso

### Desarrollo
```bash
ng serve
# Navegar a http://localhost:4200
# La aplicación se recargará automáticamente
```

### Build de Producción
```bash
ng build --prod
# Los archivos compilados estarán en dist/
```

### Testing
```bash
ng test       # Tests unitarios con Karma
ng e2e        # Tests end-to-end con Protractor
```

### Linting
```bash
ng lint
```

## 🔌 API Endpoints

La aplicación se conecta a un backend REST en `http://localhost:3000`:

### Autenticación
- `POST /login` - Login con email/password
- `POST /login/google` - Login con Google
- `GET /login/renuevatoken` - Renovar token JWT

### Usuarios
- `GET /usuario?desde={n}` - Listar usuarios (paginado)
- `POST /usuario` - Crear usuario
- `PUT /usuario/{id}` - Actualizar usuario
- `DELETE /usuario/{id}` - Eliminar usuario

### Hospitales
- `GET /hospital` - Listar hospitales
- `GET /hospital/{id}` - Obtener hospital
- `POST /hospital` - Crear hospital
- `PUT /hospital/{id}` - Actualizar hospital
- `DELETE /hospital/{id}` - Eliminar hospital

### Médicos
- `GET /medico` - Listar médicos
- `GET /medico/{id}` - Obtener médico
- `POST /medico` - Crear médico
- `PUT /medico/{id}` - Actualizar médico
- `DELETE /medico/{id}` - Eliminar médico

### Búsqueda
- `GET /busqueda/coleccion/{tipo}/{termino}` - Búsqueda global

### Archivos
- `POST /upload` - Subir archivo
- `GET /img/{tipo}/{archivo}` - Obtener imagen

## 🎯 Rutas Principales

| Ruta | Componente | Guard | Descripción |
|------|------------|-------|-------------|
| `/login` | LoginComponent | - | Autenticación |
| `/register` | RegisterComponent | - | Registro de usuario |
| `/dashboard` | DashboardComponent | VerificaToken | Panel principal |
| `/usuarios` | UsuariosComponent | Admin | Gestión de usuarios (solo admin) |
| `/hospitales` | HospitalesComponent | VerificaToken | Gestión de hospitales |
| `/medicos` | MedicosComponent | VerificaToken | Gestión de médicos |
| `/busqueda/:termino` | BusquedaComponent | VerificaToken | Resultados de búsqueda |
| `/perfil` | ProfileComponent | VerificaToken | Perfil de usuario |

## 📊 Pipe Personalizado: Imagen

```typescript
// Transforma rutas de imágenes dinámicamente
{{ usuario.img | imagen:'usuario' }}  // → URL completa de imagen
{{ hospital.img | imagen:'hospital' }}
{{ medico.img | imagen:'medico' }}

// Soporta:
// - Imágenes externas (HTTPS)
// - Imagen por defecto si no existe
// - Estructura: /img/{tipo}/{archivo}
```

## 📈 Estadísticas del Proyecto

| Métrica | Valor |
|---------|-------|
| Archivos TypeScript | 48 |
| Componentes | 13+ |
| Servicios | 8+ |
| Guards | 3 |
| Modelos | 3 |
| Módulos | 3 (App, Pages, Shared) |
| Pipes | 1 |

## 🔒 Seguridad Implementada

- Autenticación con JWT
- Guards de rutas basadas en roles
- Validación de token con renovación automática
- Almacenamiento seguro en localStorage
- Prevención de auto-eliminación de usuarios

## 🚀 Mejoras Sugeridas

- [ ] Migrar a Angular 16+ (versión actual: 5)
- [ ] Actualizar RxJS a versión 7+
- [ ] Implementar interceptores HTTP para headers centralizados
- [ ] Enviar token en headers `Authorization` en lugar de querystring
- [ ] Agregar tests unitarios completos
- [ ] Implementar HTTPS en producción
- [ ] Agregar CSRF protection
- [ ] Mejorar manejo de errores HTTP

## 📱 Responsive Design

La aplicación utiliza Bootstrap para garantizar una experiencia responsiva en:
- Desktop (1920x1080+)
- Tablet (768x1024)
- Mobile (320x568+)

## 📄 Licencia

Este proyecto es parte del portafolio de desarrollo de dannyggg3.

## 👤 Autor

**dannyggg3**
- GitHub: [@dannyggg3](https://github.com/dannyggg3)

---

⭐ Si este proyecto te fue útil, considera darle una estrella
