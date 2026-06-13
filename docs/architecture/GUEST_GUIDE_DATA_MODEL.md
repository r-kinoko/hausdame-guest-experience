# HAUSDAME GUEST EXPERIENCE
# GUEST GUIDE DATA MODEL

Documento oficial de arquitectura conceptual para definir cómo se almacena la Guía del huésped.

Este documento pertenece al repo estratégico `r-kinoko/hausdame-guest-experience` y debe servir como fuente de verdad antes de implementar Prisma, migraciones o persistencia real en `rrenteriaz/hausdame`.

---

# 1. Propósito

Definir el modelo de datos conceptual para la Guía del huésped, manteniendo el MVP simple, escalable y alineado con la arquitectura section-driven.

La prioridad es evitar una estructura excesivamente compleja tipo CMS o page builder.

---

# 2. Decisión principal

La Guía del huésped siempre pertenece a una propiedad.

```txt
Property
└── GuestGuide
```

No existen guías independientes en el MVP.

No existen guías globales compartidas entre propiedades en el MVP.

---

# 3. Cardinalidad

Una propiedad puede tener:

```txt
0..1 GuestGuide
```

Esto significa:

- una propiedad puede no tener guía todavía;
- una propiedad puede tener una guía;
- una propiedad no debe tener múltiples guías activas en MVP.

---

# 4. Relación conceptual

Modelo base:

```txt
Property
└── GuestGuide
    └── GuestGuideSection[]
```

La propiedad es el ownership principal.

La guía representa la experiencia huésped de esa propiedad.

Las secciones representan unidades configurables y renderizables.

---

# 5. GuestGuide

GuestGuide representa la guía principal asociada a una propiedad.

Campos conceptuales:

- propertyId
- status
- defaultLanguage
- enabledLanguages
- theme
- createdAt
- updatedAt
- publishedAt

## Status

Estados iniciales:

- Draft
- Published

No agregar estados complejos en MVP.

---

# 6. GuestGuideSection

GuestGuideSection representa una sección completa de la guía.

Ejemplos:

- Bienvenida
- Check-in
- Wi-Fi
- Normas
- Contacto
- Check-out
- Restaurantes
- Transporte

Campos conceptuales:

- guideId
- type
- title
- enabled
- order
- content
- createdAt
- updatedAt

---

# 7. Content JSON

Cada sección debe almacenar su contenido en un JSON estructurado según el tipo de sección.

Ejemplo Wi-Fi:

```json
{
  "networkName": "IZZI-123",
  "password": "abcd1234",
  "instructions": "Conéctate a esta red al llegar."
}
```

Ejemplo Check-in:

```json
{
  "checkInTime": "15:00",
  "arrivalInstructions": "Entra por la puerta principal del edificio.",
  "accessMethod": "Lockbox",
  "parkingInstructions": "Puedes estacionarte en el cajón 12."
}
```

---

# 8. Por qué JSON en MVP

Usar `content JSON` por sección permite:

- menos tablas;
- menos joins;
- menos migraciones;
- mayor velocidad de desarrollo;
- flexibilidad controlada;
- buena compatibilidad con secciones diferentes.

Cada tipo de sección conoce su propio esquema.

Esto evita crear una estructura excesiva como:

```txt
Guide
└── Section
    └── Block
        └── Field
```

Ese modelo se parece demasiado a un CMS genérico y no es necesario para el MVP.

---

# 9. Secciones precreadas

Cuando se crea una GuestGuide, Hausdame debe crear todas las secciones conocidas del MVP.

Algunas estarán activas por defecto y otras desactivadas.

## Activas por defecto

- Bienvenida
- Check-in
- Wi-Fi
- Normas
- Contacto
- Check-out

## Opcionales desactivadas inicialmente

- Ubicación
- Transporte
- Actividades
- Restaurantes
- Compras
- Información
- Emergencias
- Bares y clubes
- Comodidades

---

# 10. Regla de orden

Cada sección tiene un campo `order`.

Ese orden gobierna:

- Home / menú principal del huésped;
- navegación interna;
- render público;
- preview del Host.

No debe existir un orden duplicado o hardcodeado para Home.

Home debe renderizar las secciones activas ordenadas por `order`.

---

# 11. Enabled vs Disabled

Una sección puede existir aunque no esté visible.

Esto permite que todas las secciones del MVP estén disponibles desde el inicio sin que todas aparezcan al huésped.

```txt
enabled = true   → visible para huésped
enabled = false  → oculta para huésped, editable por Host
```

---

# 12. Publicación

Para MVP, la publicación vive en GuestGuide.

Estados:

```txt
Draft
Published
```

No implementar todavía:

- versionado;
- historial;
- published snapshots;
- revisiones múltiples;
- rollback.

La guía publicada representa el estado actual visible cuando esté disponible el acceso huésped.

---

# 13. Idiomas

Para MVP, los idiomas pueden tratarse de forma simple.

Conceptualmente:

- defaultLanguage define el idioma principal;
- enabledLanguages define idiomas disponibles;
- content puede evolucionar hacia contenido por idioma.

No implementar sistema complejo de traducciones todavía.

---

# 14. Assets

Las imágenes asociadas a la guía deben separarse conceptualmente de assets generales de la propiedad.

Bucket o namespace recomendado:

```txt
guest-guide-assets
```

Ejemplos de assets:

- fotos de acceso;
- fotos de estacionamiento;
- fotos de lockbox;
- imágenes de referencia para llegada;
- imágenes de secciones.

---

# 15. Restricciones MVP

No implementar en MVP:

- CMS libre;
- page builder;
- widgets personalizados;
- blocks internos movibles;
- versionado avanzado;
- múltiples guías por propiedad;
- templates múltiples;
- layouts arbitrarios;
- automatizaciones complejas;
- smart locks;
- IA.

---

# 16. Extensibilidad futura

El modelo debe permitir agregar después:

- templates;
- themes;
- más secciones;
- IA;
- automatizaciones;
- smart locks;
- reglas de visibilidad;
- contenido por reserva.

Pero esas extensiones deben incorporarse sin romper la regla principal:

```txt
Property
└── GuestGuide
    └── Sections ordenadas
```

---

# 17. Decisión final

El MVP debe usar un modelo simple:

```txt
Property
└── GuestGuide
    └── GuestGuideSection
        └── content JSON
```

Esto mantiene la arquitectura simple, flexible y suficientemente potente sin convertir Guest Experience en un CMS genérico.
