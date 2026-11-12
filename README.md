# 💍 Boda Enmanuel & Diana — Invitación Digital

Invitación de boda interactiva, animada y responsive (mobile-first) en **un solo archivo `index.html`**, lista para alojar en GitHub Pages.

**Domingo 20 de diciembre de 2026 · 5:00 pm · Zona Social Riviera del Este**

## ✨ Secciones

- **Sobre de introducción** — al abrir el enlace, lo primero que se ve es un elegante sobre verde oliva estilo *Bridgerton* con sello dorado "E&D"; al tocarlo, la solapa gira, sale la tarjeta y se revela la invitación completa.
- **Portada** — efecto arco bohemio, nombres en caligrafía y scroll suave.
- **Cuenta regresiva** en vivo (días / horas / minutos / segundos).
- **Ubicación** — tarjeta del venue con botones a Google Maps y Google Calendar.
- **Código de vestimenta "Etiqueta"** — paleta sugerida + colores restringidos (negro, rojo, beige).
- **Nota "solo adultos"** — bloque elegante y afectuoso.
- **Lluvia de sobres** — botón *Copiar datos de cuenta* con feedback "¡Copiado!".
- **Galería** con lightbox (teclado, gestos táctiles, hover suave).
- **RSVP por WhatsApp** — pases dinámicos leídos de la URL.

## ⚙️ Configuración (importante)

Abre `index.html` y busca el bloque `CONFIG` al inicio del `<script>`:

| Campo | Descripción |
| --- | --- |
| `whatsappNumber` | Número que recibirá las confirmaciones: código de país + número, **sin `+`, sin espacios ni guiones** (ej. `5215512345678`) |
| `bank` | Datos para la lluvia de sobres: `banco`, `tipo`, `titular`, `numero` y `extra` opcional (CLABE, alias, email…) |
| `venue.address` | Dirección del lugar (opcional: si se deja vacía, se oculta sola) |
| `venue.mapsQuery` | Texto con el que Google Maps buscará el lugar |
| `event` | Fecha y hora usadas por la cuenta regresiva y el calendario |
| `rsvpDeadline` | Fecha límite de confirmación que se muestra al invitado |

## 🔗 Pases personalizados por invitado

El RSVP lee parámetros de la URL:

```
https://tu-usuario.github.io/tu-repo/boda-enmanuel-diana/?nombre=Familia%20Perez&pases=3
```

- `pases` (o `invitados`) → pases asignados a esa invitación (por defecto **1**).
- `nombre` (o `name`) → pre-llena el nombre del invitado con un saludo personalizado.

Genera un enlace distinto por cada invitado y compártelo por WhatsApp. El formulario limita la cantidad de asistentes a los pases asignados y arma el mensaje automáticamente.

## 🖼️ Fotos

Reemplaza los archivos dentro de `img/` por las fotos reales de la pareja **conservando los nombres** (`hero`, `galeria-1` … `galeria-6`). Recomendado: orientación vertical y al menos 900 px de ancho.

## 🚀 Publicar en GitHub Pages

1. Sube la carpeta (o su contenido) a tu repositorio.
2. En el repo: **Settings → Pages → Source: Deploy from a branch → `main` / `(root)`** (o la carpeta donde vivan el `index.html` y `img/`).
3. Abre `https://tu-usuario.github.io/nombre-del-repo/`.

> Para un dominio directo `usuario.github.io`, sube solo el **contenido** de esta carpeta a la raíz de ese repositorio.

También funciona abriendo `index.html` con doble clic — sin build, sin frameworks, sin dependencias locales.

## 🛠️ Tecnología

- HTML semántico + CSS y JavaScript puro (vanilla).
- Google Fonts: *Great Vibes*, *Cormorant Garamond* y *Jost* (vía CDN).
- Animaciones nativas con `IntersectionObserver` + keyframes CSS; respeta `prefers-reduced-motion`.
- Botánica dibujada en SVG inline (sin imágenes de decoración pesadas).
