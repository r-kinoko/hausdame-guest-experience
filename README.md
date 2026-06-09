# Hausdame Guest Experience

Repositorio estratégico y documental para la iniciativa **Hausdame Guest Experience**.

Este repositorio NO contiene el código principal de Hausdame.

## Acuerdo de trabajo

A partir de esta iniciativa se llevarán dos registros separados:

### 1. Repositorio principal de producto

**Repositorio:** `rrenteriaz/hausdame`

Uso:

- Código fuente real.
- Implementación en Next.js.
- Prisma, migraciones y modelos.
- Integraciones.
- Fixes.
- Features productivas.
- Cambios que impacten deploy.
- Infraestructura relacionada con Railway, Neon, Supabase, etc.

Todo cambio funcional o técnico del producto se commitea en:

```txt
rrenteriaz/hausdame
```

### 2. Repositorio estratégico/documental

**Repositorio:** `r-kinoko/hausdame-guest-experience`

Uso:

- Plan maestro.
- Visión del producto.
- Notas de diseño.
- Comentarios estratégicos.
- Roadmap.
- Decisiones arquitectónicas.
- Alcance MVP.
- Bitácora conceptual.
- Referencias visuales.
- Criterios de UX.
- Ideas futuras.

Este repositorio funciona como una fuente de verdad documental para la iniciativa Guest Experience.

## Regla principal

El código vive en:

```txt
rrenteriaz/hausdame
```

La planeación, notas y diseño conceptual viven en:

```txt
r-kinoko/hausdame-guest-experience
```

## Propósito de Guest Experience

Hausdame Guest Experience será la capa orientada al huésped dentro del ecosistema Hausdame.

La idea es construir una app pública, privada por reserva, personalizable por propiedad y accesible sin login tradicional, que permita al huésped consultar:

- bienvenida;
- check-in;
- WiFi;
- ubicación;
- normas;
- transporte;
- recomendaciones;
- restaurantes;
- compras;
- emergencias;
- contacto;
- check-out;
- reportes o solicitudes futuras.

## Principio estratégico

Guest Experience debe formar parte del ecosistema Hausdame, pero no debe bloquear el desarrollo del producto principal.

Las integraciones externas, como TTLock u otras plataformas de cerraduras inteligentes, deberán diseñarse como módulos desacoplados y no como dependencias centrales.

La app huésped debe funcionar perfectamente incluso sin integración con cerraduras inteligentes.

## Estado actual

Fase actual:

```txt
Planificación estratégica y definición arquitectónica.
```

No se debe iniciar desarrollo funcional hasta definir claramente:

- visión;
- alcance MVP;
- arquitectura;
- modelo de datos;
- acceso público por reserva;
- límites de la primera versión.
