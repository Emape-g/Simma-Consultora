# SIMMA. — Sitio Web

Web institucional de **SIMMA. Comunicación Estratégica y Relaciones Institucionales**, construida en HTML + CSS + JavaScript vanilla, lista para desplegar en cualquier hosting estático (Vercel, Netlify, GitHub Pages).

## Estructura

```
simma-web/
├── index.html      # Estructura y contenido
├── styles.css      # Identidad visual (manual de marca aplicado)
├── script.js       # EmailJS + interacciones
└── README.md       # Este archivo
```

## Configuración de EmailJS (5 minutos)

El formulario usa [EmailJS](https://www.emailjs.com) para mandar los mensajes a tu casilla **sin necesidad de backend**. Plan gratuito: **200 emails/mes**.

### Pasos

1. **Crear cuenta** → https://www.emailjs.com/ (gratis con email)
2. **Conectar servicio de email**
   - Dashboard → *Email Services* → *Add New Service*
   - Elegí Gmail/Outlook/etc. → autorizar
   - Copiá el **Service ID** (ej: `service_abc1234`)
3. **Crear plantilla**
   - Dashboard → *Email Templates* → *Create New Template*
   - **Subject:** `Nuevo contacto desde SIMMA — {{from_name}}`
   - **Content (ejemplo):**
     ```
     Te contactaron desde la web de SIMMA.

     Nombre: {{from_name}}
     Email:  {{reply_to}}
     Organización: {{organization}}
     Servicio de interés: {{service}}

     Mensaje:
     {{message}}
     ```
   - **To Email:** tu casilla
   - **Reply To:** `{{reply_to}}` (para que al "Responder" vaya al cliente)
   - Guardá → copiá el **Template ID** (ej: `template_xyz5678`)
4. **Public Key**
   - Dashboard → *Account* → *General* → copiá **Public Key**

### Pegar las claves en `script.js`

Abrí `script.js` y reemplazá las 3 líneas marcadas con `// 👈`:

```js
const EMAILJS_CONFIG = {
  PUBLIC_KEY:  "TU_PUBLIC_KEY_REAL",
  SERVICE_ID:  "TU_SERVICE_ID_REAL",
  TEMPLATE_ID: "TU_TEMPLATE_ID_REAL",
};
```

Listo. Probá enviando un mensaje de prueba desde la web.

## Deploy

### Opción A — Vercel (recomendada)
1. Subí la carpeta a un repo de GitHub
2. https://vercel.com → *New Project* → importar repo → *Deploy*
3. Vercel detecta que es estático automáticamente.

### Opción B — Netlify
Arrastrar la carpeta a https://app.netlify.com/drop

### Opción C — GitHub Pages
Subir al repo, *Settings* → *Pages* → Source: `main` / `/ (root)` → guardar.

## Personalización rápida

| Cambio | Dónde |
|---|---|
| Número de WhatsApp | `index.html` — buscar `5492613078320` (3 lugares) |
| Email de Martina (firma) | El email se configura en EmailJS, no hace falta tocar el código |
| Texto de servicios | `index.html` — sección `.services__list` |
| Bio de Martina | `index.html` — sección `.direction__text` |
| Colores | `styles.css` — bloque `:root` (variables `--c-*`) |

## Notas técnicas

- **Tipografías:** Sora + Inter cargadas desde Google Fonts (sin tracking adicional).
- **Accesibilidad:** navegación por teclado, atributos ARIA, `prefers-reduced-motion` respetado.
- **Performance:** sin frameworks, todo en 3 archivos (~25 KB sin minificar). El sitio carga en <1s en buena conexión.
- **Responsive:** breakpoints a 900px, 820px, 720px, 640px y 540px.
- **SEO base:** meta description, lang `es-AR`, títulos jerárquicos.

## Cumplimiento del Manual de Marca

✅ Paleta exacta: `#DC6F49`, `#1C375B`, `#E7E1D9`, `#222222`
✅ Tipografías: Sora (display) + Inter (cuerpo)
✅ Punto distintivo (`.`) en color naranja (sufijo de `simma.`)
✅ Botones tipo *pill* con flecha circular `›`
✅ Onda/montaña del isotipo como recurso decorativo
✅ Asterisco como recurso gráfico de eyebrows (misceláneas)
✅ Tagline oficial: *"Orden interno. Posicionamiento externo."*
✅ Descriptor institucional: *"Comunicación Estratégica · Relaciones Institucionales"*
