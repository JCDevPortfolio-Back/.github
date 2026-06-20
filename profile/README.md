<h1 align="center">JCDevPortfolio · Plataforma de Microservicios</h1>

<p align="center">
  Arquitectura de <b>microservicios en NestJS</b> y <b>microfrontends Single SPA</b><br/>
  que potencia el portafolio y los productos de <b>Wilson Javier Arias Cardona</b>.
</p>

<p align="center">
  🌐 <a href="https://javiercardona.dev">javiercardona.dev</a>
  &nbsp;·&nbsp; API <code>api.javiercardona.dev</code>
  &nbsp;·&nbsp; 📚 <a href="https://storybook.javiercardona.dev">Storybook</a>
</p>

---

## 🎯 Qué es

Una plataforma completa, diseñada y operada de punta a punta: **~18 microservicios**
de backend, una capa de **microfrontends** independientes y una infraestructura
**self-hosted** con despliegue automatizado. La base sobre la que lanzo nuevos
productos sin reescribir infraestructura cada vez.

## 🏗️ Arquitectura

![Arquitectura del portafolio](./diagrama_portafolio_arquitectura.svg)

- **Enrutamiento por path** con Cloudflare Tunnel — sin nginx ni gateway adicional:
  `javiercardona.dev` y `api.javiercardona.dev` resuelven al servicio correcto
  según la ruta.
- **Frontend (Single SPA):** `portfolio-root` orquesta microfrontends independientes
  (`header`, `home`, `footer`, `admin`, `front-auth`, `payment`…), desplegables por
  separado.
- **Backend (NestJS):** `portfolio-commons` aporta utilidades transversales (manejo
  de errores HTTP, guards, DTOs) a todos los servicios (`auth`, `users`, `billing`,
  `payment`, `files`, `email`, `agents`, `webhooks`…).
- **Datos:** PostgreSQL como almacenamiento principal y Redis para caché/colas.

## 🔄 CI/CD

Despliegue **totalmente automatizado**: al publicar una nueva versión de
`portfolio-commons`, un `repository_dispatch` en GitHub Actions dispara el redeploy
coordinado de los servicios dependientes. Convención de ramas: servicios en
`develop`, librería común promovida a `master`.

## 💳 Ejemplo destacado · Facturación con Stripe

- Recepción y verificación de **webhooks** de Stripe (manejo de `rawBody`) y
  procesamiento de eventos en producción.
- Mapeo centralizado de errores a códigos HTTP correctos vía un `HttpExceptionFilter`
  en la librería común.

## 🛠️ Stack

`TypeScript` · `NestJS` · `Single SPA` · `React` · `PostgreSQL` · `Redis` ·
`Docker` · `Kubernetes` · `GitHub Actions` · `Cloudflare` · `Stripe`

## 📫 Contacto

**Wilson Javier Arias Cardona** — Desarrollador Full-Stack
🌐 [javiercardona.dev](https://javiercardona.dev) · ✉️ javiercardona.dev@gmail.com
