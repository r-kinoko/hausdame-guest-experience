# SISTEMA VISUAL GUEST GUIDE

Sistema de diseño para la plataforma de experiencia del huésped — Hausdame.

---

# 1. PRINCIPIOS DE DISEÑO

## 1.1 Core Principles

- **Mobile-first:** Todas las vistas deben optimizarse para dispositivos móviles
- **Claridad:** Información organizada y accesible sin fricción
- **Accesibilidad:** WCAG 2.1 Level AA mínimo
- **Consistencia:** Sistema unificado de componentes y patrones
- **Flexibilidad:** Temas y customización por propiedad
- **Performance:** Carga rápida, interactividad inmediata

## 1.2 Tonalidad

- Profesional pero cálido
- Amigable y acogedor
- Confiable y seguro
- Moderno y limpio

---

# 2. ESTRUCTURA VISUAL

## 2.1 Niveles de jerarquía

### Nivel 1: Header
- Logo/nombre propiedad
- Identificación reserva (opcional)
- Menú principal

### Nivel 2: Section
- Título
- Subtítulo (opcional)
- Contenido principal

### Nivel 3: Blocks
- Componentes modulares
- Contenido específico
- Llamadas a acción

### Nivel 4: Elementos
- Texto
- Imágenes
- Iconos
- Botones

---

# 3. TIPOGRAFÍA

## 3.1 Familias recomendadas

### Display (Títulos principales)
- **Opción 1:** Inter (sans-serif, moderno)
- **Opción 2:** Poppins (sans-serif, amigable)
- **Fallback:** -apple-system, BlinkMacSystemFont

### Body (Contenido)
- **Inter 400, 500, 600**
- **Line-height:** 1.6 para cuerpo, 1.2 para títulos

## 3.2 Escala tipográfica

```
Título 1:  32px / 700 / línea 1.2
Título 2:  24px / 600 / línea 1.2
Título 3:  20px / 600 / línea 1.3
Subtítulo: 16px / 500 / línea 1.4
Body:      16px / 400 / línea 1.6
Small:     14px / 400 / línea 1.5
Tiny:      12px / 400 / línea 1.4
```

---

# 4. SISTEMA DE COLOR

## 4.1 Paleta Base (Theme Default)

### Primarios
- **Primary:** `#2563EB` (azul - acciones principales)
- **Primary-dark:** `#1E40AF` (hover/active)
- **Primary-light:** `#DBEAFE` (background)

### Neutrales
- **Black:** `#000000`
- **Dark gray:** `#1F2937`
- **Gray:** `#6B7280`
- **Light gray:** `#D1D5DB`
- **Lighter gray:** `#F3F4F6`
- **White:** `#FFFFFF`

### Estados
- **Success:** `#10B981` (operaciones exitosas)
- **Warning:** `#F59E0B` (alertas)
- **Error:** `#EF4444` (errores)
- **Info:** `#3B82F6` (información)

### Especiales
- **Overlay dark:** `rgba(0, 0, 0, 0.5)`
- **Overlay light:** `rgba(255, 255, 255, 0.9)`
- **Border:** `#E5E7EB`

## 4.2 Aplicación por sección

Cada sección puede tener un acento:

- **WiFi:** Púrpura `#7C3AED`
- **Check-in:** Verde `#059669`
- **Restaurantes:** Naranja `#EA580C`
- **Transporte:** Azul marino `#0369A1`
- **Emergencias:** Rojo `#DC2626`
- **Actividades:** Naranja cálido `#F97316`

---

# 5. ESPACIADO

## 5.1 Scale (en píxeles)

```
xs:   4px
sm:   8px
md:  16px
lg:  24px
xl:  32px
2xl: 48px
3xl: 64px
```

## 5.2 Márgenes estándar

- **Contenedor:** 16px padding en mobile, 24px en desktop
- **Secciones:** 24px - 32px margin-bottom
- **Elementos:** 8px - 16px spacing vertical
- **Texto e imagen:** 12px - 16px entre ellos

---

# 6. COMPONENTES CORE

## 6.1 Botones

### Primary
```
Padding: 12px 24px
Border-radius: 8px
Font: 16px / 600
Background: #2563EB
Color: #FFFFFF
Hover: #1E40AF, shadow
Active: scale 0.98
```

### Secondary
```
Padding: 12px 24px
Border-radius: 8px
Font: 16px / 500
Background: #F3F4F6
Color: #1F2937
Border: 1px #D1D5DB
Hover: background #E5E7EB
```

### Tertiary (Ghost)
```
Padding: 12px 16px
Background: transparent
Color: #2563EB
Underline: opcional
Hover: background #DBEAFE
```

### Icon Button
```
Size: 40px
Padding: 8px
Border-radius: 6px
Hover: background #F3F4F6
```

## 6.2 Cards

```
Border-radius: 12px
Background: #FFFFFF
Border: 1px #E5E7EB
Padding: 16px
Box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1)
Hover: shadow aumenta, transform slight
```

## 6.3 Input Fields

```
Border-radius: 8px
Border: 1px #D1D5DB
Padding: 12px 16px
Font: 16px
Focus: border #2563EB, shadow
Placeholder: #9CA3AF
Background: #FFFFFF
```

## 6.4 Iconografía

- **Set:** Feather Icons o Heroicons
- **Tamaño estándar:** 24px (iconos en bloques), 16px (texto)
- **Color:** Heredar color del texto
- **Peso:** 2px stroke

---

# 7. SECCIONES — TEMPLATES VISUALES

## 7.1 Welcome Section

```
┌─────────────────┐
│  [Portada img]  │ (full-width, 40vh)
│                 │
├─────────────────┤
│ Bienvenida      │ (Título 1, centered)
│                 │
│ Estamos alegres │ (Body, centered, gray)
│ de tu llegada   │
│                 │
├─────────────────┤
│ [Botón] Comenzar│ (Primary)
└─────────────────┘
```

## 7.2 WiFi Section

```
┌─────────────────┐
│ 📡 WiFi         │ (icon + título)
├─────────────────┤
│                 │
│ Nombre:         │ (label gray)
│ Casa-Luna-5GHz  │ (value large, selectable)
│                 │
│ Contraseña:     │
│ [Icon] ••••••   │ (con toggle show)
│ [Copy button]   │
│                 │
└─────────────────┘
```

## 7.3 Check-in Section

```
┌─────────────────┐
│ 🔑 Check-in     │
├─────────────────┤
│                 │
│ 📍 Ubicación    │ (Card)
│ Calle Luna 42   │
│ [Ver en mapa]   │
│                 │
│ 🔐 Smart Lock   │ (Card)
│ Código: 4582    │
│ [Copiar]        │
│                 │
│ 🚪 Acceso       │ (Card)
│ Puerta principal│
│ Instrucciones..│
│                 │
└─────────────────┘
```

## 7.4 Ubicación Section

```
┌─────────────────┐
│ 📍 Ubicación    │
├─────────────────┤
│  [Map embed]    │ (Google Maps iframe)
│  (full-width)   │
├─────────────────┤
│ Dirección:      │
│ Calle Luna 42   │
│ [Copiar/Ir]     │
│                 │
│ Código postal:  │
│ 08001 Barcelona │
└─────────────────┘
```

## 7.5 Restaurants Section

```
┌─────────────────┐
│ 🍽️ Restaurantes │
├─────────────────┤
│                 │
│ [Card 1]        │ (Restaurant card)
│ 🏷️ El Borne     │
│ ⭐ 4.8 (234)    │
│ 5 min a pie     │
│ [Abrir]         │
│                 │
│ [Card 2]        │
│ ...             │
│                 │
└─────────────────┘
```

## 7.6 Transport Section

```
┌─────────────────┐
│ 🚕 Transporte   │
├─────────────────┤
│                 │
│ Metro Línea 4   │ (Card)
│ 2 min a pie     │
│ L4 🔵 Barcelo.. │
│                 │
│ Autobús línea 7 │ (Card)
│ 100m             │
│ Parada actual   │
│                 │
│ Taxi            │ (Card)
│ +34 933 033 033 │
│ [Llamar]        │
│                 │
└─────────────────┘
```

## 7.7 Emergencies Section

```
┌─────────────────┐
│ 🆘 Emergencias  │
├─────────────────┤
│                 │
│ ❌ Urgencia     │ (Red button - primary)
│ [Reportar]      │
│                 │
│ 📞 Contactos    │
│ Anfitrión       │
│ +34 600 000 000 │
│ [Llamar/Chat]   │
│                 │
│ 🚨 Servicios    │
│ Policía: 091    │
│ Ambulancia: 061 │
│                 │
└─────────────────┘
```

## 7.8 Contact Section

```
┌─────────────────┐
│ 💬 Contacto     │
├─────────────────┤
│                 │
│ Ana García      │ (Card)
│ 🏠 Anfitriona   │
│ ⭐⭐⭐⭐⭐       │
│                 │
│ 📞 +34 600 000  │
│ [Llamar/Chat]   │
│                 │
│ 💌 Mensaje      │
│ [Escribir]      │
│                 │
└─────────────────┘
```

---

# 8. PATTERNS COMUNES

## 8.1 Info Card

```
┌──────────────────┐
│ [Icon] Título    │ (16px, 600)
│ Descripción      │ (14px, 400, gray)
│ detallada        │
└──────────────────┘
```

## 8.2 Call-to-Action Inline

```
Texto descriptivo que termina
con → [link text] ← o con
[botón primario]
```

## 8.3 Confirmation Flow

```
1. Card con contexto
2. Botones: [Confirmar] [Cancelar]
3. Mensaje success/error
```

## 8.4 Loading State

- Skeleton screens (preferido)
- Spinner centrado (40px)
- Nunca "cargando..." solo texto

## 8.5 Empty State

```
┌──────────────────┐
│     [Icon]       │ (grande, light gray)
│   Sin contenido  │ (Título)
│   Para esta      │ (Body, gray)
│   sección        │
│                  │
│  [Refresh] btn   │ (opcional)
└──────────────────┘
```

---

# 9. DISEÑO RESPONSIVO

## 9.1 Breakpoints

```
Mobile:  < 640px  (default)
Tablet:  640px - 1024px
Desktop: > 1024px
```

## 9.2 Adaptaciones

### Mobile
- Full width
- Padding: 16px
- Stack vertical
- Bottom safe area: 16px+ (mobile notch)

### Tablet
- 2-columnas donde sea apropiado
- Padding: 24px
- Cards wider

### Desktop
- Máximo width: 1200px
- Centered container
- Padding: 32px lateral

---

# 10. ANIMACIONES

## 10.1 Transiciones

- **Duración estándar:** 200ms
- **Easing:** ease-in-out
- **Hover:** color, shadow (no scale)
- **Active:** opacity, transform slight

## 10.2 Ejemplos

```css
Button:
  transition: all 200ms ease-in-out;
  &:hover { transform: translateY(-1px); }
  &:active { transform: scale(0.98); }

Card:
  transition: box-shadow 200ms ease-in-out;
  &:hover { box-shadow: 0 8px 16px rgba(...); }

Text link:
  transition: color 150ms ease-in-out;
  &:hover { opacity: 0.8; text-decoration: underline; }
```

## 10.3 Motion principles

- Mínimas y sutiles
- No deben distraer
- Útiles (feedback visual)
- Rápidas (<300ms)

---

# 11. TEMAS CUSTOMIZABLES

## 11.1 Theme Object

```ts
interface GuestGuideTheme {
  name: string;
  colors: {
    primary: string;
    secondary: string;
    accent: string;
    background: string;
    surface: string;
    text: string;
    border: string;
  };
  typography: {
    fontFamily: string;
    scale: 'compact' | 'normal' | 'spacious';
  };
  border: {
    radius: 'small' | 'medium' | 'large';
  };
  spacing: 'compact' | 'normal' | 'spacious';
}
```

## 11.2 Temas predefinidos V1

- **Default:** Azul profesional
- **Luxury:** Dorado y blanco
- **Warm:** Naranjas y calidez
- **Modern:** Blanco y acentos
- **Beachy:** Azul turquesa

---

# 12. ACCESIBILIDAD

## 12.1 Estándares

- **WCAG 2.1 Level AA mínimo**
- **Ratios de contraste:** 4.5:1 texto pequeño, 3:1 grande

## 12.2 Checklist

- [ ] Todos los botones y links son keyboard-accessible
- [ ] Uso de `aria-labels` donde sea necesario
- [ ] Textos alt en imágenes
- [ ] Estructura de headings correcta (H1 → H6)
- [ ] Color no es único medio de información
- [ ] Focus visible en todos los elementos interactivos
- [ ] Lenguaje simple y claro
- [ ] Tiempo suficiente para leer (sin auto-dismiss)

---

# 13. DARK MODE (Futuro)

Preparar estructura para dark mode sin implementarlo en V1.

## 13.1 CSS Custom Properties

```css
:root {
  --color-bg: #FFFFFF;
  --color-text: #1F2937;
  --color-border: #E5E7EB;
}

@media (prefers-color-scheme: dark) {
  :root {
    --color-bg: #111827;
    --color-text: #F3F4F6;
    --color-border: #374151;
  }
}
```

---

# 14. GUÍA DE USO PARA DESARROLLADORES

## 14.1 Importar componentes

```tsx
import { Button, Card, Section } from '@/components/guest-guide';

// Con tema
import { withTheme } from '@/lib/themes';

const ThemedCard = withTheme(Card, theme);
```

## 14.2 Spacing utilities

```tsx
<div className="mt-4 mb-6 px-4">
  Content
</div>
```

## 14.3 Colores dinámicos

```tsx
<button style={{
  backgroundColor: theme.colors.primary,
  color: theme.colors.text,
}}>
  Action
</button>
```

---

# 15. PERFORMANCE

## 15.1 Optimizaciones

- **Images:** WebP + JPEG fallback, lazy loading
- **Fonts:** Subsets (es, en, fr, it, de)
- **CSS:** Purged / minified
- **JS:** Code splitting por sección

## 15.2 Target metrics

- LCP: < 2.5s
- FID: < 100ms
- CLS: < 0.1

---

# 16. DOCUMENTACIÓN DE MARCA

## 16.1 Recursos

- [ ] Figma design system (link)
- [ ] Component storybook (link)
- [ ] Iconografía pack (Feather/Heroicons)
- [ ] Fuentes (Inter)

## 16.2 Versionado

- V1.0: Sistema base (2026-06-09)
- Actualizaciones en: `/docs/design/UPDATES.md`

---

**Última actualización:** 2026-06-09  
**Estado:** Base system definido  
**Próximo paso:** Implementación en componentes React + Tailwind
