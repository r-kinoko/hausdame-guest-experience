# Guest Guide — Content Model Architecture

> Estado: documento conceptual / arquitectónico.
> No define Prisma, migraciones, APIs, componentes ni editor.
> Objetivo: establecer el modelo de contenido de "Guía del huésped" antes de cualquier implementación funcional.

---

## 1. Definición conceptual

La Guía del huésped se estructura en tres niveles jerárquicos:

```txt
Guide
 └── Sections
      └── Blocks
```

- **Guide**: la guía completa de una propiedad. Es el contenedor de nivel superior; representa "la experiencia huésped" de esa propiedad.
- **Section**: una unidad temática dentro de la guía (ej. WiFi, Check-in, Normas). Las secciones se activan/desactivan y se ordenan, pero su estructura interna (layout, jerarquía visual) está predefinida por Hausdame.
- **Block**: la unidad mínima de contenido dentro de una sección (ej. nombre de red WiFi, contraseña, una tarjeta de restaurante). Los blocks son los campos/elementos que el Host llena.

Esta jerarquía es la única superficie de configuración permitida para el Host.

---

## 2. Filosofía de arquitectura

La arquitectura correcta es:

```txt
section-driven architecture
```

No:

```txt
free-form page builder
```

Hausdame debe controlar:

- diseño visual;
- spacing;
- jerarquía;
- app feeling;
- responsive/mobile-first;
- accesibilidad;
- consistencia entre propiedades.

El Host debe controlar:

- contenido;
- activación de secciones;
- orden de secciones;
- imágenes permitidas;
- idioma/configuración;
- publicación.

El Host NO debe controlar:

- layouts arbitrarios;
- componentes internos;
- estructura visual;
- navegación huésped;
- diseño libre tipo CMS.

---

## 3. Por qué NO usar page builder

Un page builder libre introduce riesgos altos:

| Riesgo | Impacto |
|---|---|
| Layouts inconsistentes | La experiencia pierde calidad visual |
| UX rota en móvil | El huésped no entiende rápido |
| Mayor complejidad técnica | Más difícil de mantener |
| Host con demasiadas decisiones | Aumenta fricción |
| Preview/render más frágil | Más riesgo de bugs |
| Pérdida de app feeling | Se vuelve CMS, no guía |

La Guía del huésped debe sentirse simple, premium y clara. Para lograrlo, el Host debe llenar contenido dentro de estructuras controladas por Hausdame.

---

## 4. Definición de Guide

Una **Guide** representa la guía completa de una propiedad.

Características conceptuales:

- pertenece a una propiedad;
- contiene secciones ordenadas;
- puede estar en borrador o publicada;
- puede tener idioma principal;
- puede tener futuras traducciones;
- puede tener tema visual controlado;
- puede generar una experiencia pública huésped en el futuro.

No se define todavía modelo Prisma.

---

## 5. Definición de Section

Una **Section** es una unidad temática renderizable.

Ejemplos:

- Bienvenida;
- Check-in;
- WiFi;
- Normas;
- Transporte;
- Restaurantes.

Cada sección tiene:

- tipo predefinido;
- título;
- estado activo/inactivo;
- orden;
- contenido configurable;
- estructura visual controlada.

El Host puede ordenar secciones completas, pero no debe rediseñar internamente cada sección.

---

## 6. Secciones MVP

Catálogo inicial cerrado de secciones:

1. Bienvenida
2. Check-in
3. WiFi
4. Normas
5. Transporte
6. Actividades
7. Restaurantes
8. Compras
9. Información
10. Emergencias
11. Contacto
12. Check-out

Este catálogo está alineado con las referencias visuales auditadas y con el principio de experiencia simple.

---

## 7. Definición de Blocks

Un **Block** es una unidad de contenido dentro de una sección.

Los blocks NO son componentes libres que el Host arrastra arbitrariamente.

Son campos o elementos predefinidos por el tipo de sección.

### Ejemplo: WiFi

- networkName
- password
- instructions
- optionalImage

### Ejemplo: Check-in

- checkInTime
- accessInstructions
- keyInstructions
- parkingInstructions
- optionalImages

### Ejemplo: Restaurantes

- restaurantName
- description
- address
- mapLink
- phone
- image

### Ejemplo: Emergencias

- emergencyPhone
- nearestHospital
- policeContact
- hostEmergencyContact
- instructions

---

## 8. Reglas de renderizado

El render debe seguir:

- mobile-first;
- cards grandes;
- spacing generoso;
- jerarquía visual clara;
- contenido escaneable;
- app feeling;
- hospitality-first;
- simple feels premium.

El render público futuro debe consumir la estructura Guide → Sections → Blocks.

No debe existir un render hardcodeado separado por página si eso rompe el modelo section-driven.

---

## 9. Restricciones arquitectónicas

No permitir:

- drag-and-drop libre de blocks;
- layouts arbitrarios;
- builders anidados;
- CMS libre;
- dashboards;
- tablas como UI huésped;
- edición visual tipo Canva;
- componentes custom por Host;
- navegación huésped diseñada manualmente por el Host.

---

## 10. Futuro controlado

La arquitectura puede crecer con:

- templates;
- themes;
- traducciones;
- IA;
- integraciones;
- automatizaciones;
- smart locks;
- módulos premium.

Pero esas extensiones deben vivir dentro del modelo Guide → Sections → Blocks.

No deben reemplazarlo por un builder libre.

---

## 11. Regla final

La Guía del huésped debe ser configurable, no diseñable desde cero.

Hausdame diseña la experiencia.

El Host completa el contenido.

El huésped recibe una app simple, clara y útil.
