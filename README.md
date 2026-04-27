<div align="center">

# 🐾 Petlink — AdoptaHub

### Plataforma web de adopción de animales en tiempo real

[![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/es/docs/Web/HTML)
[![React](https://img.shields.io/badge/React_18-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://react.dev/)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/es/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/es/docs/Web/JavaScript)
[![IndexedDB](https://img.shields.io/badge/IndexedDB-FF6F00?style=for-the-badge&logo=databricks&logoColor=white)](#)

<br/>

![Petlink Banner](https://images.unsplash.com/photo-1601979031925-424e53b6caaa?w=900&h=300&fit=crop&q=80)

<br/>

> **Conecta animales que necesitan un hogar con familias que quieren adoptarlos.**  
> Una SPA completamente funcional, sin backend, que vive en un solo archivo HTML.

<br/>

[✨ Ver Demo](#demo) · [🚀 Empezar](#instalación) · [📋 Funcionalidades](#funcionalidades) · [🛠️ Tecnologías](#tecnologías)

</div>

---

## 📖 ¿Qué es Petlink?

**Petlink (AdoptaHub)** es una aplicación web de adopción de mascotas diseñada como **Single Page Application (SPA)** con React 18, completamente autocontenida en un único archivo HTML. Permite a los usuarios explorar un catálogo de animales, solicitar su adopción rellenando un formulario detallado, y gestionar todas las solicitudes desde un panel de administración integrado — todo sin necesidad de un servidor backend.

Los datos de solicitudes persisten localmente en el navegador mediante **IndexedDB**, lo que permite demostrar flujos completos de una aplicación real de forma offline y portable.

---

## ✨ Funcionalidades

### 🔍 Catálogo de animales
- Vista en **cuadrícula o lista** con toggle intercambiable
- **Paginación** con 8 animales por página
- **Búsqueda** en tiempo real por nombre o especie

### 🎛️ Filtros avanzados en sidebar
| Filtro | Opciones |
|--------|----------|
| Especie | Todos, Perro, Gato, Pájaro, Conejo, Hámster, Tortuga, Pez |
| Tamaño | Todos, Pequeño, Mediano, Grande |
| Edad | Cachorro, Joven, Adulto, Senior |
| Estado | Disponible, En revisión, No disponible |

### 📋 Ficha de animal
- Modal detallado con descripción, especie, raza, tamaño y edad
- Indicador visual de estado (disponible / en revisión / no disponible)
- Botón de adopción contextual según disponibilidad

### 📝 Formulario de adopción
- Validación en tiempo real de todos los campos
- Campos: nombre, email, teléfono, ciudad, tipo de vivienda, experiencia previa, motivación
- Aceptación de términos y condiciones obligatoria
- Generación de **código de referencia único** (`SOL-XXXXXX`)

### 🗄️ Panel de solicitudes (Admin)
- Listado completo de todas las solicitudes registradas
- Estados: **Pendiente / Aprobada / Rechazada**
- Detalle completo de cada solicitud
- Opción para limpiar el historial completo

### 🔑 Sistema de sesión simulado
- Modal de **Login / Registro** con tabs
- Avatar con iniciales del usuario en el header
- Menú desplegable con opciones de perfil y cierre de sesión
- Flujo visual completo sin backend real

### 💾 Persistencia local
- **IndexedDB** para almacenar solicitudes entre sesiones
- Sin cookies, sin localStorage para datos críticos
- Estructura de base de datos documentada en el código

---

## 🛠️ Tecnologías

| Tecnología | Uso |
|---|---|
| **React 18** (CDN) | UI declarativa con Hooks (`useState`, `useEffect`, `useMemo`) |
| **Babel Standalone** | Transpilación de JSX en el navegador |
| **IndexedDB** | Persistencia de solicitudes de adopción |
| **CSS Custom Properties** | Sistema de diseño con variables de color y espaciado |
| **Google Fonts — Nunito** | Tipografía redondeada y amigable |
| **HTML5 puro** | Sin bundler, sin build step, sin dependencias de Node |

---

## 🚀 Instalación

No requiere instalación. Es un único archivo HTML autocontenido.

```bash
# 1. Clona el repositorio
git clone https://github.com/tu-usuario/petlink.git

# 2. Navega al directorio
cd petlink

# 3. Abre el archivo en tu navegador
open Petlink.html
# o en Windows:
start Petlink.html
```

> 💡 También puedes arrastrarlo directamente al navegador o usar la extensión **Live Server** de VS Code para desarrollo.

---

## 📂 Estructura del proyecto

```
petlink/
│
├── Petlink.html          # ✅ Toda la aplicación en un solo archivo
│   ├── <style>           # Sistema de diseño CSS completo
│   ├── <script type="text/babel">
│   │   ├── IndexedDB     # Capa de persistencia (openDB, insert, getAll, clear)
│   │   ├── ANIMALS[]     # Dataset de 18 animales
│   │   ├── Componentes   # Card, Sidebar, Modals, Forms, Panels
│   │   └── App           # Componente raíz con estado global
│   └── ReactDOM.render   # Punto de entrada
│
└── README.md             # Este archivo
```

---

## 🗃️ Modelo de datos

### Solicitud de adopción (IndexedDB)

```js
{
  id:                 Number,   // autoincrement
  id_animal:          Number,   // FK al animal del catálogo
  nombre_animal:      String,
  especie:            String,
  emoji:              String,
  solicitante_nombre: String,
  solicitante_email:  String,
  solicitante_telefono: String,
  solicitante_ciudad: String,
  vivienda:           String,   // 'piso' | 'casa' | 'otro'
  experiencia:        String,
  motivo:             String,
  acepta_terminos:    Boolean,
  estado:             String,   // 'pendiente' | 'aprobada' | 'rechazada'
  fecha:              String,   // ISO 8601
  referencia:         String    // 'SOL-XXXXXX'
}
```

---

## 📸 Capturas de pantalla

| Catálogo en cuadrícula | Ficha de animal | Formulario de adopción |
|---|---|---|
| Vista principal con filtros sidebar | Modal con detalles del animal | Formulario completo con validación |

---

## 🎨 Sistema de diseño

El proyecto implementa un sistema de diseño propio basado en **CSS Custom Properties**:

```css
/* Paleta verde principal */
--g500: #3da86a   /* Color de acción primaria */
--g700: #1e6b3f   /* Header y énfasis */

/* Neutros */
--n50:  #f8f8f6   /* Fondo de página */
--n900: #1a1917   /* Texto principal */

/* Estados */
--sa:   #2d8a55   /* Disponible (verde) */
--sr:   #c07a10   /* En revisión (ámbar) */
--su:   #a32d2d   /* No disponible (rojo) */
```

---

## 🤝 Contribuciones

Las contribuciones son bienvenidas. Si quieres mejorar el proyecto:

1. **Fork** el repositorio
2. Crea una rama: `git checkout -b feature/nueva-funcionalidad`
3. Realiza tus cambios y haz commit: `git commit -m 'feat: descripción del cambio'`
4. Haz push: `git push origin feature/nueva-funcionalidad`
5. Abre un **Pull Request**

---

## 💡 Ideas de mejora futuras

- [ ] Conectar con un backend real (Node.js / Supabase)
- [ ] Sistema de favoritos persistente
- [ ] Notificaciones por email al solicitar adopción
- [ ] Panel de administración con actualización de estados
- [ ] Diseño responsive para móviles
- [ ] Modo oscuro

---

## 📄 Licencia

Este proyecto está bajo la licencia **MIT**. Puedes usarlo, modificarlo y distribuirlo libremente.

---

<div align="center">

Hecho con ❤️ para los animales que esperan un hogar

**[⬆ Volver al inicio](#-petlink--adoptahub)**

</div>
