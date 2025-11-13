# 🏢 Condominio360

Sistema completo de gestión de condominios tipo SaaS, inspirado en Vivook y Comunidad Feliz.

## 🚀 Características

- ✅ Autenticación JWT con roles (admin, residente, conserje)
- ✅ Gestión de condominios y unidades
- ✅ Pagos en línea con Stripe
- ✅ Reservas de áreas comunes
- ✅ Panel de administración
- ✅ Diseño responsive con modo oscuro
- ✅ API REST completa
- ✅ Validaciones y seguridad

## 📦 Tecnologías

### Backend
- Node.js + Express
- PostgreSQL (Neon)
- JWT Authentication
- Stripe Payments
- Bcrypt

### Frontend
- React 18
- Vite
- Tailwind CSS
- React Router
- Axios

## 🛠️ Instalación

### 1. Backend

```bash
cd backend
npm install

# Configurar variables de entorno
cp .env.example .env
# Editar .env con tus credenciales

# Inicializar base de datos PostgreSQL
psql -h tu-host -U usuario -d database -f database_init.sql

# Iniciar servidor de desarrollo
npm run dev
```

### 2. Frontend

```bash
cd frontend
npm install

# Configurar API URL
# Editar .env
VITE_API_URL=http://localhost:5000

# Iniciar servidor de desarrollo
npm run dev
```

## 🗄️ Base de Datos

El proyecto usa PostgreSQL. Para configurar:

1. Crea una base de datos en [Neon.tech](https://neon.tech) (gratis)
2. Copia la URL de conexión
3. Ejecuta el script `backend/database_init.sql`

### Tablas:
- `users` - Usuarios del sistema
- `condominios` - Condominios
- `unidades` - Departamentos/casas
- `pagos` - Registro de pagos
- `reservas` - Reservas de áreas comunes

## 🔐 Autenticación

El sistema usa JWT para autenticación. Los roles disponibles son:

- **admin** - Acceso completo al sistema
- **residente** - Ver información y hacer pagos/reservas
- **conserje** - Gestión operativa

## 💳 Pagos con Stripe

1. Crea una cuenta en [Stripe.com](https://stripe.com)
2. Obtén tus claves API (test o producción)
3. Configura `STRIPE_SECRET` en el backend
4. Los pagos se procesan vía Stripe Checkout

## 🚀 Deploy

### Backend → Render.com

```bash
# 1. Sube tu código a GitHub
git init
git add .
git commit -m "Initial commit"
git remote add origin tu-repo.git
git push -u origin main

# 2. En Render.com:
# - Conecta tu repositorio
# - Usa el archivo render.yaml (configuración automática)
# - Configura las variables de entorno
# - Deploy automático
```

### Frontend → Vercel.com

```bash
# 1. Instala Vercel CLI
npm i -g vercel

# 2. Deploy
cd frontend
vercel --prod

# O conecta tu repo en vercel.com para deploy automático
```

## 📁 Estructura del Proyecto

```
condominio360/
├── backend/
│   ├── src/
│   │   ├── controllers/     # Lógica de negocio
│   │   ├── routes/          # Rutas de la API
│   │   ├── middleware/      # Auth, errores
│   │   ├── db.js           # Conexión DB
│   │   └── index.js        # Servidor
│   ├── database_init.sql
│   ├── package.json
│   ├── render.yaml
│   └── .env
└── frontend/
    ├── src/
    │   ├── pages/          # Componentes de páginas
    │   ├── config.js       # Configuración API
    │   ├── App.jsx
    │   ├── main.jsx
    │   └── index.css
    ├── index.html
    ├── vite.config.js
    ├── tailwind.config.js
    ├── vercel.json
    └── package.json
```

## 🔧 Variables de Entorno

### Backend (.env)
```bash
PORT=5000
NODE_ENV=development
JWT_SECRET=tu_secreto_seguro
DATABASE_URL=postgresql://usuario:password@host/db
CLOUDINARY_URL=cloudinary://...
STRIPE_SECRET=sk_test_...
FRONTEND_URL=http://localhost:5173
```

### Frontend (.env)
```bash
VITE_API_URL=http://localhost:5000
```

## 📝 API Endpoints

### Auth
- `POST /api/auth/register` - Registrar usuario
- `POST /api/auth/login` - Login
- `GET /api/auth/profile` - Perfil (requiere token)

### Condominios
- `GET /api/condos` - Listar
- `GET /api/condos/:id` - Ver detalle
- `POST /api/condos` - Crear (admin)
- `PUT /api/condos/:id` - Actualizar (admin)
- `DELETE /api/condos/:id` - Eliminar (admin)

### Pagos
- `POST /api/pagos/crear` - Crear pago
- `GET /api/pagos` - Listar pagos
- `GET /api/pagos/:id` - Ver pago
- `GET /api/pagos/verificar?session_id=xxx` - Verificar pago

## 🔒 Seguridad

- ✅ Contraseñas hasheadas con bcrypt
- ✅ Tokens JWT con expiración
- ✅ Validación de inputs
- ✅ Protección contra SQL injection
- ✅ CORS configurado
- ✅ Roles y permisos

## 🐛 Troubleshooting

### Error: Cannot find module
```bash
# Verifica que instalaste las dependencias
npm install
```

### Error de conexión a la DB
```bash
# Verifica tu DATABASE_URL en .env
# Asegúrate que incluya ?sslmode=require para Neon
```

### Error de CORS
```bash
# Verifica que FRONTEND_URL esté correctamente configurado en el backend
# Debe coincidir con la URL donde corre tu frontend
```

## 📄 Licencia

MIT License - Proyecto de código abierto

## 👥 Contribuir

1. Fork el proyecto
2. Crea una rama (`git checkout -b feature/nueva-funcionalidad`)
3. Commit cambios (`git commit -m 'Agregar nueva funcionalidad'`)
4. Push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Abre un Pull Request

## 📧 Soporte

Para reportar bugs o solicitar funcionalidades, abre un issue en GitHub.

---

**Hecho con ❤️ para la comunidad de condominios**

Versión: 1.0.0
