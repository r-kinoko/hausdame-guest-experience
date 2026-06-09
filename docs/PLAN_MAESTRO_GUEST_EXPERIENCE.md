# HAUSDAME — GUEST EXPERIENCE PLATFORM

Plan Maestro de Producto, Arquitectura y Ejecución

---

# 1. VISIÓN DEL PRODUCTO

Hausdame Guest Experience será una extensión natural de Hausdame orientada al huésped.

No será solamente una “guía digital”.
La visión real es convertir cada alojamiento en una experiencia interactiva, automatizada y personalizada.

## Objetivo principal

- Reducir preguntas repetitivas al Host
- Mejorar experiencia del huésped
- Reducir incidencias
- Centralizar información del alojamiento
- Automatizar comunicación operativa
- Generar una experiencia premium tipo “app del alojamiento”

El huésped recibirá un enlace privado asociado a su reserva y podrá acceder desde cualquier dispositivo sin necesidad de login.

Ejemplo:

```txt
stay.hausdame.com/casa-luna?token=abc123
```

---

# 2. CONCEPTO GENERAL

La plataforma funcionará como una mini app pública de cada propiedad.

El huésped verá:

- Bienvenida
- Check-in
- Accesos
- WiFi
- Ubicación
- Normas
- Transporte
- Restaurantes
- Actividades
- Compras
- Emergencias
- Contacto
- Check-out
- etc.

Todo configurable por el Host.

Cada propiedad podrá tener:

- Diseño personalizado
- Secciones activas/inactivas
- Contenido editable
- Idiomas
- Información dinámica
- Integraciones futuras

---

# 3. OBJETIVOS ESTRATÉGICOS

## 3.1 Objetivos para el Host

- Ahorrar tiempo
- Reducir mensajes repetitivos
- Profesionalizar operación
- Mejorar reviews
- Diferenciarse de otros alojamientos
- Centralizar toda la información

## 3.2 Objetivos para el huésped

- Tener toda la información en un solo lugar
- Reducir estrés de llegada
- Sentirse acompañado
- Descubrir actividades y recomendaciones
- Acceder fácilmente a servicios y soporte

## 3.3 Objetivos para Hausdame

- Aumentar valor percibido del producto
- Diferenciarse de PMS tradicionales
- Crear funcionalidades premium
- Abrir futuras líneas de monetización
- Convertirse en plataforma integral de hospitalidad

---

# 4. PRINCIPIOS DE ARQUITECTURA

## MUY IMPORTANTE

No construir pantallas hardcodeadas.

Construir un sistema modular y renderizable.

## 4.1 Lo que NO se debe hacer

NO crear:

- páginas fijas
- layouts rígidos
- JSON gigantes
- componentes acoplados

Ejemplo incorrecto:

```ts
if(section === "wifi") { ... }
```

Esto explota conforme crece el sistema.

## 4.2 Arquitectura correcta

Sistema basado en:

- Sections
- Blocks
- Render registry
- Visibility rules
- Dynamic content

---

# 5. MODELO CONCEPTUAL

## 5.1 GuestGuide

Representa la app huésped principal.

Campos conceptuales:

- propertyId
- slug
- theme
- published
- requiresReservationAccess
- defaultLanguage
- enabledLanguages

## 5.2 GuestGuideSection

Representa una sección.

Ejemplos:

- Welcome
- WiFi
- Restaurants
- Transport

Campos:

- id
- guideId
- type
- visible
- order
- title
- icon
- layout

## 5.3 GuestGuideBlock

Contenido renderizable dentro de cada sección.

Ejemplos:

- texto
- imagen
- galería
- botón
- mapa
- restaurante
- teléfono
- QR
- horario
- lista
- checklist

Campos:

- id
- sectionId
- type
- content
- metadata
- order
- visibilityRules

## 5.4 GuestGuideAccessToken

Controla acceso seguro.

Campos:

- reservationId
- token
- expiresAt
- revokedAt
- lastAccessAt

---

# 6. SISTEMA DE ACCESO

## 6.1 Requisitos

- Público
- Sin login
- Seguro
- Asociado a reserva

## 6.2 Propuesta

El huésped recibe:

```txt
stay.hausdame.com/casa-luna?token=abc123
```

El token:

- está asociado a reserva
- puede expirar
- puede revocarse
- conoce fechas de estancia

## 6.3 Ventajas

El sistema podrá:

- ocultar información antes del check-in
- activar códigos smart lock sólo durante estancia
- desactivar acceso al terminar
- personalizar experiencia

---

# 7. SISTEMA DE RENDERIZADO

## 7.1 Registry Pattern

Ejemplo conceptual:

```ts
const SECTION_COMPONENTS = {
  wifi: WifiSection,
  restaurants: RestaurantsSection,
  transport: TransportSection,
}
```

El sistema renderiza dinámicamente.

Ventajas:

- Escalable
- Modular
- Fácil de mantener
- Permite themes
- Permite IA futura

## 7.2 Tipos de bloques iniciales

V1:

- RichText
- Image
- Gallery
- Button
- Map
- ContactCard
- RestaurantCard
- Checklist
- InfoCard
- TransportCard

---

# 8. EDITOR PARA HOST

## 8.1 Filosofía

NO intentar construir Canva desde el inicio.

El MVP debe priorizar:

- simplicidad
- velocidad
- estabilidad

## 8.2 UX propuesta

Sidebar:
- Secciones

Main:
- Preview mobile en tiempo real

Panel lateral:
- configuración del bloque

## 8.3 Funcionalidades iniciales

- activar/desactivar secciones
- reordenar secciones
- editar textos
- subir imágenes
- editar horarios
- agregar enlaces
- editar teléfonos
- elegir idiomas

---

# 9. IDIOMAS

## 9.1 MVP

Idiomas manuales:

- Español
- Inglés
- Francés
- Italiano
- Alemán

## 9.2 Futuro

IA para:

- traducción automática
- detección idioma huésped
- contenido dinámico

---

# 10. AUTOMATIZACIONES FUTURAS

## 10.1 Check-in automático

Cuando inicia reserva:

- guest guide se activa
- huésped recibe link automático

## 10.2 Smart Locks

Integración futura:

- TTLock
- Nuki
- Yale
- etc.

Mostrar código sólo:

- durante estancia
- al huésped correcto

## 10.3 Incidencias huésped

El huésped reporta:

- agua caliente
- ruido
- limpieza
- wifi

Esto crea automáticamente:

- incidencia
- notificación
- prioridad

## 10.4 Checkout inteligente

Guest app puede incluir:

- checklist salida
- confirmación salida
- basura
- llaves
- apagado luces

Y automáticamente:

- disparar limpieza

---

# 11. SISTEMA DE THEMES

Desde el inicio se debe considerar.

## 11.1 MVP

Theme simple:

- colores
- tipografías
- portada
- estilo botones

## 11.2 Futuro

Marketplace de templates.

Ejemplo:

- Luxury
- Minimal
- Beach
- Modern
- Boutique
- Family

---

# 12. FASES DE DESARROLLO

## FASE 1 — FOUNDATION

Objetivo:
Definir arquitectura correctamente.

Incluye:

- modelos Prisma
- rutas públicas
- token access
- render engine
- base editor
- sections registry

NO enfocarse aún en diseño complejo.

## FASE 2 — MVP HUÉSPED

Incluye:

- Welcome
- Check-in
- WiFi
- Contacto
- Ubicación
- Check-out
- Idiomas
- Compartir link

Objetivo:
tener primera experiencia usable.

## FASE 3 — EDITOR HOST

Incluye:

- preview realtime
- activar/desactivar secciones
- reordenar
- edición básica
- upload imágenes

## FASE 4 — EXPERIENCE MODULES

Agregar:

- restaurantes
- actividades
- transporte
- compras
- emergencia
- recomendaciones

## FASE 5 — AUTOMATIZACIÓN

Agregar:

- links automáticos
- mensajes automáticos
- incidencias huésped
- checkout inteligente

## FASE 6 — SMART EXPERIENCE

Agregar:

- smart locks
- IA
- recomendaciones dinámicas
- contenido inteligente

---

# 13. ESTRATEGIA TÉCNICA

## 13.1 Backend

Mantener stack actual:

- Next.js
- Prisma
- PostgreSQL
- Railway
- Supabase Storage

## 13.2 Frontend

Reutilizar:

- Tailwind
- sistema mobile-first
- componentes Hausdame

## 13.3 Storage

Separar assets:

- property-assets
- guest-guide-assets

---

# 14. RIESGOS

## 14.1 Riesgo principal

Intentar construir demasiado desde el inicio.

## 14.2 Solución

Priorizar:

- arquitectura correcta
- MVP pequeño
- escalabilidad futura

---

# 15. MVP RECOMENDADO REAL

La primera versión NO debe incluir:

- IA
- marketplace
- themes avanzados
- automatizaciones complejas

## 15.1 MVP ideal

- Welcome
- WiFi
- Check-in
- Ubicación
- Contacto
- Checkout
- Idiomas
- Compartir link
- Editor simple
- Mobile-first

---

# 16. VISIÓN A FUTURO

Hausdame puede evolucionar de:

“software de limpieza”

a:

“ecosistema operativo de hospitalidad”

Este módulo Guest Experience tiene potencial de convertirse en:

- diferenciador principal
- funcionalidad premium
- herramienta de automatización
- canal de comunicación huésped
- sistema operativo de estancia

---

# 17. RECOMENDACIÓN FINAL

La clave del éxito será:

NO construir páginas.

Construir:
un sistema modular de experiencias renderizables.

Eso permitirá:

- crecer sin rehacer arquitectura
- agregar IA
- agregar templates
- agregar automatizaciones
- agregar integraciones
- escalar producto
- mantener código limpio
