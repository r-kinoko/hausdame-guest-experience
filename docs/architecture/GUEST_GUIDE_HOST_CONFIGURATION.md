# HAUSDAME GUEST EXPERIENCE
# GUEST GUIDE HOST CONFIGURATION

Documento oficial de arquitectura de producto para definir cómo el Host configura la Guía del huésped.

Este documento pertenece al repo estratégico `r-kinoko/hausdame-guest-experience` y sirve como fuente de verdad antes de implementar editor, modelos de datos o UI funcional en `rrenteriaz/hausdame`.

---

# 1. Propósito

Definir una experiencia de configuración simple, controlada y coherente para el Host.

El Host debe poder crear y mantener una Guía del huésped sin convertirse en diseñador, administrador técnico o constructor de páginas.

Principio central:

```txt
El Host configura contenido.
Hausdame controla la experiencia visual.
```

---

# 2. Alcance

Este documento define:

- flujo de configuración del Host;
- secciones iniciales;
- secciones opcionales;
- reglas de edición;
- orden de secciones;
- vista previa;
- publicación;
- restricciones del editor.

Este documento NO define todavía:

- modelos Prisma;
- migraciones;
- APIs;
- server actions;
- tokens públicos;
- render público final;
- automatizaciones;
- smart locks.

---

# 3. Flujo Host

Flujo esperado:

```txt
Guía del huésped
  → seleccionar propiedad
  → configurar secciones
  → editar contenido
  → vista previa
  → publicar
```

La configuración debe sentirse directa y guiada.

No debe sentirse como un CMS libre, Canva, Notion o page builder.

---

# 4. Primera configuración

Cuando el Host configura por primera vez una propiedad, Hausdame debe generar una guía base.

La guía base evita que el Host empiece desde una pantalla vacía.

El Host no debe tener que decidir desde cero qué estructura crear.

---

# 5. Secciones activas por defecto

Estas secciones deben existir desde el inicio:

1. Bienvenida
2. Check-in
3. Wi-Fi
4. Normas
5. Contacto
6. Check-out

Estas secciones representan el mínimo operativo para una estancia útil.

---

# 6. Secciones opcionales

Estas secciones pueden activarse después:

- Ubicación
- Transporte
- Actividades
- Restaurantes
- Compras
- Información
- Emergencias
- Bares y clubes
- Comodidades

El Host puede activarlas si aportan valor a la propiedad.

---

# 7. Qué puede hacer el Host

El Host puede:

- activar o desactivar secciones;
- ordenar secciones completas;
- editar contenido de cada sección;
- subir imágenes útiles;
- elegir idioma o traducción cuando exista soporte;
- ver vista previa;
- publicar o despublicar la guía.

---

# 8. Qué NO puede hacer el Host

El Host no puede:

- crear layouts arbitrarios;
- mover bloques internos libremente;
- crear widgets personalizados;
- diseñar una interfaz desde cero;
- modificar navegación visual del huésped;
- romper el sistema de cards;
- convertir la guía en dashboard;
- crear un CMS libre.

La arquitectura es section-driven, no page-builder-driven.

---

# 9. Regla crítica de orden

El orden de secciones definido por el Host gobierna:

- la pantalla Home / menú principal del huésped;
- la navegación interna;
- el orden de render de secciones.

No debe existir un orden duplicado o hardcodeado para Home.

Home debe ser un índice visual renderizado desde las secciones activas ordenadas por `order`.

Ejemplo:

```txt
Si el Host ordena:
1. Check-in
2. Wi-Fi
3. Contacto
4. Normas

Home debe mostrar exactamente ese orden.
```

---

# 10. Edición de secciones

Cada sección debe tener un formulario propio y simple.

El Host llena campos, no diseña interfaces.

## Ejemplo: Wi-Fi

Campos posibles:

- nombre de red;
- contraseña;
- instrucciones;
- imagen opcional.

## Ejemplo: Check-in

Campos posibles:

- hora de check-in;
- instrucciones de llegada;
- acceso;
- llaves o código;
- estacionamiento;
- imágenes útiles.

## Ejemplo: Contacto

Campos posibles:

- nombre del Host;
- teléfono;
- WhatsApp;
- email;
- instrucciones de contacto.

---

# 11. Vista previa

Debe existir una vista previa de lo que verá el huésped.

La vista previa debe basarse en el mismo modelo de secciones que la vista pública futura.

No debe existir una preview falsa separada de la estructura real.

---

# 12. Publicación

Estados iniciales:

- Draft
- Published

Draft permite al Host preparar la guía sin exponerla.

Published representa una guía lista para compartir o asociar a reservas futuras.

No agregar estados complejos en MVP.

---

# 13. Experiencia Host vs experiencia huésped

La experiencia huésped debe seguir:

- app feeling;
- mobile-first;
- hospitality-first;
- cards grandes;
- contenido escaneable.

La experiencia Host debe ser:

- simple;
- clara;
- eficiente;
- guiada;
- sin complejidad innecesaria.

El editor del Host no debe copiar exactamente la UI del huésped, porque configurar y consumir son acciones distintas.

---

# 14. Referencias visuales

Las pantallas huésped deben respetar las referencias visuales auditadas del repo estratégico.

Referencia oficial:

```txt
images/IMAGENES_AUDITADAS.md
```

Para la experiencia Host, esas imágenes sirven como referencia de resultado final, no como patrón directo de edición.

---

# 15. Restricciones de implementación

Antes de implementar funcionalidad real, no introducir:

- editor visual avanzado;
- drag-and-drop interno de bloques;
- modelos Prisma;
- migraciones;
- tokens públicos;
- automatizaciones;
- smart locks;
- IA;
- render público final.

Cualquier implementación debe ser incremental, reversible y alineada con este documento.

---

# 16. Decisión final

La Guía del huésped debe ser fácil de configurar porque su estructura ya viene guiada.

El Host no construye una app.

El Host completa una experiencia diseñada por Hausdame.
