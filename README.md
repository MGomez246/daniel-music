# 🎵 Daniel Music

Sitio web de **clases de música (flauta traversa y canto)** con un **panel de administración integrado**: el docente inicia sesión y edita textos, imágenes, secciones y fondo directamente sobre la página, sin tocar código.

## ✨ Características

- **Sitio público** con secciones de portada, "Sobre Daniel", clases e inscripción.
- **Edición en línea** (solo para administradores): textos con estilo, imágenes, logo y fondo (color, degradado, imagen o video).
- **Secciones personalizables**: se pueden agregar, ordenar, ocultar y restaurar. Bloques disponibles: texto, imagen, texto + imagen, cita destacada, galería y publicaciones embebidas de Instagram, X/Twitter o Facebook.
- **Contenido persistente en Supabase**: el contenido del sitio se guarda en la base de datos y se carga al abrir la página.
- **Autenticación de administrador** con Supabase Auth y tabla `admin_users`.
- **Subida de archivos validada**: solo PNG, JPEG, WebP y MP4, máximo 10 MB, con verificación de los bytes de cabecera del archivo (SVG excluido a propósito porque puede ejecutar código).
- **Cabeceras de seguridad** (CSP, HSTS, X-Frame-Options, entre otras) configuradas en `vercel.json`.
- Diseño responsive con Tailwind CSS.

## 🛠️ Tecnologías

- **React 19** (componentes, hooks personalizados `useAdmin` y `useSiteContent`)
- **Vite**
- **Tailwind CSS 4**
- **Supabase** (Auth, base de datos y Storage)
- **Vercel** (configuración de despliegue y cabeceras de seguridad)

## ▶️ Cómo ejecutarlo en local

1. Clona el repositorio:
   ```bash
   git clone https://github.com/MGomez246/daniel-music.git
   cd daniel-music
   ```
2. Instala las dependencias:
   ```bash
   npm install
   ```
3. Crea un archivo `.env.local` con las credenciales de tu proyecto de Supabase:
   ```bash
   VITE_SUPABASE_URL=https://TU-PROYECTO.supabase.co
   VITE_SUPABASE_ANON_KEY=tu-anon-key
   ```
4. En Supabase necesitas: una tabla `site_content` (fila con `id = 1` y columna `content` de tipo JSON), una tabla `admin_users` con los `user_id` autorizados y un bucket `site-images`. La escritura debe protegerse con políticas RLS para que solo los administradores puedan modificar.
5. Arranca el servidor de desarrollo:
   ```bash
   npm run dev
   ```
6. Abre `http://localhost:5173`.

## 🗂️ Estructura

```
src/
├── components/
│   ├── admin/        # Barra de administrador y login
│   ├── sections/     # Secciones fijas y bloques personalizados
│   └── ui/           # Texto, imagen y carrusel editables
├── hooks/            # useAdmin, useSiteContent
└── lib/              # Cliente de Supabase, contenido y almacenamiento
```

## 📚 Lo que practiqué en este proyecto

- Construir un sitio completo con React y hooks personalizados.
- Integrar un backend como servicio (Supabase) para autenticación, datos y archivos.
- Diseñar un editor en línea con roles (visitante vs. administrador).
- Validar archivos subidos y aplicar cabeceras de seguridad.

---

> Proyecto personal de [Martin Gómez](https://github.com/MGomez246).
