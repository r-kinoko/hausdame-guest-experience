# HAUSDAME GUEST EXPERIENCE
# GUEST GUIDE LIFECYCLE

Documento oficial para definir el ciclo de vida de la Guía del huésped dentro del ecosistema Hausdame.

Este documento pertenece al repo estratégico `r-kinoko/hausdame-guest-experience` y debe servir como fuente de verdad antes de implementar lógica de creación, eliminación, duplicación o persistencia real en `rrenteriaz/hausdame`.

---

# 1. Propósito

Definir cuándo se crea, elimina o conserva una Guía del huésped y cómo se relaciona con el ciclo de vida de una propiedad.

La Guía del huésped siempre pertenece a una propiedad.

```txt
Property
└── GuestGuide
```

---

# 2. Creación

La Guía del huésped NO se crea automáticamente cuando se crea una propiedad.

Se crea únicamente cuando el Host presiona por primera vez:

```txt
Configurar guía
```

Esto evita:

- registros innecesarios;
- guías vacías no usadas;
- complejidad prematura;
- ruido operativo.

---

# 3. Primera creación de guía

Cuando el Host configura una guía por primera vez, Hausdame debe crear:

```txt
GuestGuide
└── GuestGuideSection[]
```

Todas las secciones conocidas del MVP deben crearse en ese momento.

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

# 4. Eliminación de propiedad

Si una propiedad se elimina, su Guía del huésped debe eliminarse también.

La relación debe comportarse como cascade conceptual:

```txt
Delete Property
→ Delete GuestGuide
→ Delete GuestGuideSections
```

La guía no debe quedar huérfana.

---

# 5. Duplicación de propiedad

Duplicar una propiedad NO duplica automáticamente la Guía del huésped en MVP.

Razón:

- una propiedad duplicada puede requerir instrucciones distintas;
- accesos, Wi-Fi, estacionamiento y normas pueden cambiar;
- copiar guías automáticamente puede generar errores operativos;
- es más seguro obligar al Host a revisar y configurar.

Regla MVP:

```txt
Duplicate Property
≠
Duplicate GuestGuide
```

En el futuro podría existir una acción explícita:

```txt
Copiar guía desde otra propiedad
```

pero no debe implementarse en MVP inicial.

---

# 6. Cambio de nombre o datos de propiedad

Si una propiedad cambia de nombre, dirección u otros datos, la guía sigue perteneciendo a la misma propiedad.

No se recrea.

No se elimina.

No se duplica.

La guía puede reutilizar datos actualizados de la propiedad cuando corresponda.

---

# 7. Publicación y despublicación

El ciclo de vida básico de publicación vive en GuestGuide.

Estados:

- Draft
- Published

El cambio de estado no modifica la propiedad.

La propiedad puede existir sin guía publicada.

---

# 8. Guía inexistente

Una propiedad sin guía debe mostrarse al Host como:

```txt
Sin configurar
```

CTA esperado:

```txt
Configurar guía
```

Al presionar ese CTA inicia la primera creación de GuestGuide y sus secciones base.

---

# 9. Regla de seguridad

No crear guías en background sin acción explícita del Host.

No crear guías durante sincronizaciones, importaciones o procesos ajenos a la configuración de Guest Experience.

---

# 10. Decisión final

La Guía del huésped se crea bajo demanda, se elimina con la propiedad y no se duplica automáticamente.

Esto mantiene el sistema simple, seguro y alineado con el MVP.
