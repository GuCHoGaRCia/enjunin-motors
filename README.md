# 🚗 enJunin Motors

> **Vitrina pública** del proyecto *Enjunin Motors* — portal multi-tenant de
> avisos de venta de autos. Acá vas a encontrar descripción, stack y
> capturas; **el código fuente es privado**.

![PHP](https://img.shields.io/badge/PHP-8.x-777BB4?logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-5.7%2B-4479A1?logo=mysql&logoColor=white)
![Responsive](https://img.shields.io/badge/responsive-320%2F768%2F1280-2ea44f)

## Qué es

Plataforma multi-tenant para avisos automotores: cada agencia recibe su
subdominio **`agencia.enjunin.com.ar`** (wildcard DNS + SSL) y publica su
catálogo con fotos, mientras un panel central administra agencias, usuarios
y métricas de toda la red.

## Funcionalidades

- 🌐 **Sitio público por agencia** — home con destacados, catálogo con
  filtros (marca, precio, año, km, combustible, caja), ficha de vehículo
  con galería y consultas de clientes (leads).
- 🔑 **Panel de agencia** (`/panel`) — login con recuperación de contraseña,
  CRUD de vehículos con subida de fotos (resize + miniatura + WebP),
  consultas con seguimiento de no-leídas, perfil y logo de la agencia,
  roles dueño/staff.
- 🛠 **Panel de plataforma** (`/admin`) — alta y suspensión de agencias,
  gestión de usuarios por agencia y métricas globales.
- 🔒 **Seguridad** — CSRF en todos los POST, rate limiting en logins,
  Content-Security-Policy estricta (`script-src 'self'`), HSTS, sesiones
  endurecidas, subidas sin ejecución de scripts y `.htaccess` de defensa en
  los directorios sensibles.
- 📱 **Responsive mobile-first** — verificado en 320 / 768 / 1280 px.
- 🗄 **Multi-tenant de verdad** — una sola base con `tenant_id` en cada
  tabla y resolución de agencia por `HTTP_HOST`. PHP puro con MVC propio,
  sin Composer ni frameworks: despliegue por FTP a hosting cPanel.

## Capturas

### 🌐 Sitio público — catálogo con filtros

![Catálogo público con filtros](screenshots/sitio-publico.png)

### 🔑 Panel de agencia — vista móvil (320 px)

![Panel de agencia en móvil](screenshots/panel-agencia.png)

### 🛠 Panel de plataforma — dashboard

![Panel de plataforma](screenshots/panel-plataforma.png)

## Vehículos de muestra

Galería del catálogo demo (`demo.enjunin.com.ar`) con fotos reales de los
7 modelos del seed:

<table>
  <tr>
    <td align="center"><img src="vehicles/toyota-hilux-2021.jpg" width="320" alt="Toyota Hilux 2021"><br>🛻 <b>Toyota Hilux 2021</b></td>
    <td align="center"><img src="vehicles/volkswagen-amarok-2020.jpg" width="320" alt="Volkswagen Amarok 2020"><br>🛻 <b>Volkswagen Amarok 2020</b></td>
    <td align="center"><img src="vehicles/ford-ranger-2022.jpg" width="320" alt="Ford Ranger 2022"><br>🛻 <b>Ford Ranger 2022</b></td>
  </tr>
  <tr>
    <td align="center"><img src="vehicles/chevrolet-cruze-2019.jpg" width="320" alt="Chevrolet Cruze 2019"><br>🚗 <b>Chevrolet Cruze 2019</b></td>
    <td align="center"><img src="vehicles/renault-sandero-2021.jpg" width="320" alt="Renault Sandero 2021"><br>🚗 <b>Renault Sandero 2021</b></td>
    <td align="center"><img src="vehicles/peugeot-208-2020.jpg" width="320" alt="Peugeot 208 2020"><br>🚗 <b>Peugeot 208 2020</b></td>
  </tr>
  <tr>
    <td align="center"><img src="vehicles/fiat-cronos-2022.jpg" width="320" alt="Fiat Cronos 2022"><br>🚗 <b>Fiat Cronos 2022</b></td>
    <td></td>
    <td></td>
  </tr>
</table>

### Créditos de fotos

Fotografías de [Wikimedia Commons](https://commons.wikimedia.org/),
usadas en la demo con fines ilustrativos:

- *Toyota Hilux Revo GR Sport* — Chanokchon, [CC BY-SA 4.0](https://commons.wikimedia.org/wiki/File:2021_Toyota_Hilux_Revo_GR_Sport_Double-Cab_2.8_4x4.jpg)
- *Volkswagen Amarok Highline (Argentina)* — Just a Man, [CC BY 4.0](https://commons.wikimedia.org/wiki/File:2024_Volkswagen_Amarok_Highline_3.0_V6_(facelift,_Argentina)_(1-3).jpg)
- *Ford Ranger 4x2 XLT 2022* — Captainmorlypogi1959, [CC BY-SA 4.0](https://commons.wikimedia.org/wiki/File:Ford_Ranger_4x2_XLT_2022_(4).jpg)
- *Chevrolet Cruze Turbo LTZ* — Damian B Oh, [CC BY-SA 4.0](https://commons.wikimedia.org/wiki/File:Chevrolet_Cruze_Turbo_LTZ_D2LC_Modern_Black_(2).jpg)
- *Dacia Sandero Stepway (Renault Sandero)* — Vauxford, [CC BY-SA 4.0](https://commons.wikimedia.org/wiki/File:2021_Dacia_Sandero_Stepway_Prestige_TCE_1.0_Front.jpg)
- *Peugeot 208 Allure* — Harvey Bold, [CC0](https://commons.wikimedia.org/wiki/File:2016_Peugeot_208_Allure_PureTech_-_1200cc_1.2_(100PS)_Petrol_-_Silver_-_07-2024,_Front.jpg)
- *Fiat Cronos 1.3 GSE* — Just a Man, [CC BY 4.0](https://commons.wikimedia.org/wiki/File:2024_Fiat_Cronos_1.3_GSE_Precision.jpg)

<!--
## Roadmap

- [x] Fases 0–5 — núcleo MVC, esquema, sitio público, panel de agencia y
      panel de plataforma
- [x] **Fase 6** — despliegue a producción (cPanel) + smoke test
      (desplegado y funcionando en `enjunin.com.ar/autos`, 2026-09-26)
- [ ] **Fase 7** — vitrina transversal `autos.enjunin.com.ar`: cada agencia
      destaca hasta 5 vehículos con galería y CTA hacia su subdominio
      (modelo de negocio: cuota configurable por agencia)
-->      
## Stack

PHP 8 · MySQL/MariaDB · Apache (`mod_rewrite`) · HTML/CSS/JS vanilla ·
MVC propio sin dependencias · Git
