# 💍 Boda Enmanuel & Diana — Invitación Digital

Invitación de boda interactiva, animada y responsive (mobile-first) en **un solo archivo `index.html`**, lista para alojar en GitHub Pages.

**Domingo 20 de diciembre de 2026 · 5:00 pm · Zona Social Riviera del Este**

## ✨ Secciones

- **Sobre de introducción** — al abrir el enlace, lo primero que se ve es un elegante sobre verde oliva estilo *Bridgerton* (ilustraciones `img/SobreCerrado.png` y `img/SobreAbierto.png`, fondo transparente); al tocarlo se abre con un fundido cruzado y se revela la invitación completa.
- **Portada** — efecto arco bohemio, nombres en caligrafía y scroll suave.
- **Cuenta regresiva** en vivo (días / horas / minutos / segundos).
- **Ubicación** — tarjeta del venue con botones a Google Maps y Google Calendar.
- **Código de vestimenta "Etiqueta"** — con una nota sutil: atuendos en tonos pastel.
- **Nota "solo adultos"** — bloque elegante y afectuoso.
- **Lluvia de sobres** — botón *Copiar datos de cuenta* con feedback "¡Copiado!".
- **Galería** con lightbox (teclado, gestos táctiles, hover suave).
- **RSVP por WhatsApp** — pases dinámicos leídos de la URL + registro automático opcional en Google Sheets.

## ⚙️ Configuración (importante)

Abre `index.html` y busca el bloque `CONFIG` al inicio del `<script>`:

| Campo | Descripción |
| --- | --- |
| `whatsappNumber` | Número que recibirá las confirmaciones: código de país + número, **sin `+`, sin espacios ni guiones** (ej. `5215512345678`) |
| `bank` | Datos para la lluvia de sobres: `banco`, `tipo`, `titular`, `numero` y `extra` opcional (CLABE, alias, email…) |
| `googleForm` | URL (`action`) e IDs (`entries`) del Google Form donde se registran las confirmaciones en una hoja de Sheets |
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

## 📋 Registro de confirmaciones en Google Sheets

Cada confirmación enviada se registra **automáticamente** en una hoja de cálculo (además de abrirse WhatsApp). Solo necesitas crear un Google Form — 2 minutos, sin código:

1. Entra a [forms.google.com](https://forms.google.com) y crea un formulario en blanco con **4 preguntas**:

   | Pregunta | Tipo de pregunta |
   | --- | --- |
   | `Nombre` | Respuesta corta |
   | `¿Asiste?` | Opción múltiple: `Sí, confirmo` / `No podré asistir` |
   | `¿Cuántas personas?` | Respuesta corta |
   | `Mensaje` | Párrafo |

2. En la pestaña **Respuestas**, pulsa el ícono verde de Sheets ( *"Crear hoja de cálculo"* ). Esa hoja acumulará las confirmaciones.
3. En el menú **⋮** del formulario elige **"Obtener enlace prellenado"**, escribe cualquier valor en las 4 preguntas y pulsa **"Obtener enlace"**. El enlace generado contiene los IDs de cada pregunta, algo como `entry.1234567890=...` (anota el ID que aparece junto a cada pregunta, en orden).
4. Copia también la URL normal del formulario (botón **Enviar** → ícono de enlace 🔗) y cámbiale el final `viewform` por `formResponse`.
5. Pega ambos datos en el bloque `CONFIG.googleForm` dentro de `index.html`:

```js
googleForm: {
  action: 'https://docs.google.com/forms/d/e/1FAIpQLS…/formResponse',
  entries: {
    nombre:   'entry.1111111111',
    asiste:   'entry.2222222222',
    personas: 'entry.3333333333',
    mensaje:  'entry.4444444444'
  }
}
```

> **Tip:** si te resulta complicado, haz solo los pasos 1 y 2, pégame el enlace del formulario aquí, y yo completo la configuración por ti.

Mientras `googleForm.action` quede vacío, la invitación solo abre WhatsApp: el registro en la hoja es un extra que se activa al configurarlo.

## 🖼️ Fotos

Reemplaza los archivos dentro de `img/` por las fotos reales de la pareja **conservando los nombres** (`hero`, `galeria-1` … `galeria-6`). Recomendado: orientación vertical y al menos 900 px de ancho.

Las ilustraciones del sobre (`SobreCerrado.png` / `SobreAbierto.png`) deben compartir el mismo lienzo y encuadre para que el fundido cruzado se vea continuo; si las cambias, conserva los nombres y el formato PNG con fondo transparente.

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
