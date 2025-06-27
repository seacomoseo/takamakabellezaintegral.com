# var_domain

[![var_domain](/assets/media/base/icon.png)](https://var_domain/)


## STEPS


### Local

- If new project (not fork):
  - Copy [var_domain project files](https://github.com/seacomoseo/var_domain)
  - `git submodule add https://github.com/seacomoseo/sansoul.git themes/sansoul`
- Else if fork:
  - Download submódule theme files: `git submodule update --init --recursive`
- Now you can see the run project in the browser with the `do server` comand
- `README.md` ⏩ edit baseURL ("var_domain") + delete steps bit by bit
- Design
  - You can edit any file with the same structure of theme sansoul
  - GENERAL
    - `config.yml`
    - `data/*.{yml,md}`
  - IMG + LOGO + FAVICON
    - `assets/media/` folder ⏩ [Compress image tool](https://compressor.io/)
      - `base/poster.png`
      - `logo.svg`
      - `logo.png`
      - `icon.png`
      - `favicon.ico` ⏩ [Favicon converter tool](https://favicon.io/favicon-converter/)
    - Netlify and Cloudflare Pages update icon (project and account)
  - FONTS
    - Fonts that not be in Google Fonts:
      - .otf/.ttf files in `assets/fonts` + rename
      - You need the `sansoul_tools` project in `../_tools` folder
      - Run `do fonts` comand
      - `Family` + `Style` + `Weight` must match in `styles.yml ⏩ fonts` + `_fonts.scss` (and disable `fonts.google` if appropriate)
  - CONTENT
    - `content/*`
      - `page/divisores.md` ⏩ remove
      - SCRAP
        - Copy [this Spreadsheet Layout](https://docs.google.com/spreadsheets/d/1bJQaAFoBAwHhWz_WFRIHlkHoDmZZyT8H8NtdCnSTdaU)
        - First scrap with Screaming Frog and paste `url` and `title`
        - Second scrap with `IMPORTXML` formula in `content-start` tab
        - If need HTML content
          - Three scrap with `Web Scraper` chrome extension and paste in `content-scrap` tab
          - Copy `content-start` tab into `content-next` and get `body_code` (by `content-scrap`) with `VLOOKUP` formula
          - Copy `body_code` column to `body`, replace double quotes, [convert to Markdown](https://smalldev.tools/html-to-markdown-converter-online) and clean it
          - Paste in `file.md` in `./Downloads` and run `_tools/md-replaces.command`
          - Check `file_new.md` content:
            - headers: `^#`
            - images: `!\[.+?\)`
            - links: `(^|[^!])\[.+?\)`
            - internal links: `https?://(www\.)?example\.com`
          - Paste in sheet
        - Export to CSV like `./Downloads/file.csv` and run `_tools/csv-to-md.command`
        - Move files from `markdown_files` to `blog` project
  - HTML: `data/config.yml ⏩ langs[*].html.{head,body}`
  - CSS: `assets/css/` ⏩ `{*,_variables-custom.scss,_custom.scss}`
  - JS: `assets/js/*,custom.js`
  - IMG: `assets/media/*`
  - REDIRECTS: `assets/redirects.md`
  - ROBOTS: `assets/robots.md`
  - If Multilanguaje and Multihosting, add `cp ./public/[es|en]/404.html ./public/` in `netlify.toml ⏩ build.command`
  - Try in Safari and Firefox
  - Check in [W3 Validator](https://validator.w3.org/)
  - Check in [PageSpeed Insights](https://pagespeed.web.dev/)


### After client validate web


#### Domain

- If Netlify
  - [`Domain Management / settings`](https://app.netlify.com/sites/var_name/settings/domain)
  - `Add custom domain`
  - `Check DNS configuration` Copy
  - Add `DNS Records` copied from Netlify to Domain gestor:
    - From: `var_domain`
      DNS Record: `ALIAS`, `ANAME` or `flattened CNAME`
      To: `apex-loadbalancer.netlify.com`
    - From: `var_domain`
      DNS Record: `A`
      To: `75.2.60.5`
    - From: `www`
      DNS Record: `CNAME`
      To: `var_name.netlify.app.`
    - Maybe you need to eliminate the previous records with similar names
  - `Verify DNS configuration`
  - If it does not work after a while, try `Set as main domain` in the `www` version and also in te `nowww` version
- If Cloudflare Pages
  - [Custom domains](https://dash.cloudflare.com/?to=/:account/pages/view/var_name/domains)
  - `Set up a custom domains`
  - `var_domain`
  - `Continue`
  - Add `DNS Records` copied from Cloudflare Pages to Domain gestor:
    - From: `var_domain`
      DNS Record: `CNAME`
      To: `var_name.pages.dev`
    - From: `www`
      DNS Record: `CNAME`
      To: `var_name.pages.dev`
  - `Activate domain` (if `Begin DNS transfer` end)
  - Repeat with `www.var_domain`
  - ...........................................................


#### Forms

- If SanSoulSend Form
  - Add domain and emails in [GSS](https://docs.google.com/spreadsheets/d/1yQEoxReqnvQbQ5LkGnhUvu2_Aa-PhGfFztoRG1qY6iM/edit?gid=0#gid=0)
- If Netlify Form
  - Don't need configure nothing! Build like you want in local or with CMS
  - [`Netlify ⏩ Site ⏩ Forms ⏩ Form Notifications`](https://app.netlify.com/sites/var_name/settings/forms#form-notifications) ⏩ `Add notification ⏩ Email notification ⏩ Email to Notify`
    - `Email to notify` = Emails of collaborators that want receive submissions
    - `Custom email subject line` = `Formulario de contacto de var_domain`
    - `Save`
  - Submissions: [`Netlify site ⏩ Forms`](https://app.netlify.com/sites/var_name/forms)
- [formsubmit.co](https://formsubmit.co/)
- If Google Form: [Tutorial](https://seacomoseo.com/instrucciones/#google-forms)


#### [Google Analytics](https://analytics.google.com/)

- `Admin ⏩ Libre acount ⏩ New property ⏩ ...` copy ID
- `data/config.yml ⏩ google_analytics` ⏩ paste ID
- `Ajustes de datos`
  - `Recogida de datos`
    - `Recogida de datos de Google signals ⏩ Empezar`
    - `Consentimiento de recogida de datos de usuario` ⏩ Check
  - `Conservación de datos ⏩ Conservación de datos de eventos ⏩ 14 meses ⏩ Guardar`
- `Eventos clave ⏩ Nuevo eventos clave ⏩ Nombre de evento nuevo` ⏩ add `contact`
- `Definiciones personalizadas ⏩ Crear dimensión personalizada ⏩ Nombre de la dimensión + Parámetro de evento` ⏩ add `ID + id` + `Label + label` + `Type + type`


#### [Google Search Console](https://search.google.com/search-console)

- Add property
- Verify versions ⏩ `data/config.yml`
  - `google_analytics`
  - `google_site_verification`
  - `google_file_verification`
  - DNS:
    From: `@`
    DNS Record: `TXT`
    To: `google-site-verification=[google_site_verification]`
- Link with Analytics
- Add sitemap.xml


#### [Google My Business](https://business.google.com/)

- `Add company ⏩ ...` ⏩ whait 13 days to receive postal and insert code to verify


#### [Disqus](https://disqus.com/)

- `data/config.yml ⏩ disqus`


#### Collaborators

- [Google Analytics](https://analytics.google.com/) ⏩ `Admin ⏩ Libre acount ⏩ Site ⏩ Property access management ⏩ Add users` ⏩ Add emails of collaborators with role `Reader` or `Admin`.
- [Google Search Console](https://search.google.com/search-console) ⏩ `Site ⏩ Settings ⏩ Users and permissions ⏩ Add user` Add emails of collaborators with `Full` permission
- [Google My Business](https://business.google.com/)
  - `Site ⏩ Users ⏩ Add users` ⏩ Add emails of collaborators with role `Owner`


##### Services Layout

1. [Servicios var_domain](https://drive.google.com/file/d/1trq28fMfEVwoZOk4ue0tJzAJDZtj64BK) ⏩ `File ⏩ Make a copy` ⏩ Select client directory.
1. Change the info.
1. `Share` ⏩ Add emails of collaborators with `Editor` permission.


##### Delivery

Send to all collaborators next:

###### WhatsApp

```md
*ENTREGA WEB var_domain*

Te dejo aquí este mensaje como referencia (también te lo paso por email con el asunto `ENTREGA WEB var_domain`).

En el siguiente enlace tienes instrucciones sobre cosas referentes a tu sitio web (cómo modificar cosas, información extra, ect.):

https://seacomoseo.com/entrega/

No es necesario que lo veas, solo lo es si quieres hacer cosas por tu cuenta o si no estoy disponible.

¡Un saludo!
```

###### Mail

```
Asunto: ENTREGA WEB var_domain
Cuerpo:
Te dejo aquí este email como referencia.

En el siguiente enlace tienes instrucciones sobre cosas referentes a tu sitio web (cómo modificar cosas, información extra, ect.):

https://seacomoseo.com/entrega/

No es necesario que lo veas, solo lo es si quieres hacer cosas por tu cuenta o si no estoy disponible.

¡Un saludo!
```

## GADS

### GA4

- Vincular
  - `Herramientas`
  - `Gestor de datos`
  - `Google Analytics (GA4) & Firebase ⏩ Detalles`
  - Buscar proyecto y ⏩ `Vincular`
- Importar conversiones
  - `Objetivos`
  - `Conversiones`
  - `Resumen`
  - `Nueva acción de conversión`
  - `Importar`
  - `Propiedades de Google Analytics 4`
  - `Web`
  - `Continuar`
  - Seleccionar `contact_click` y `contact_form_submit`
  - `Importar y continuar`
- Cambiar a `Maximizar conversiones`
  - `Campañas`
  - `⚙️`
  - `Puja`
  - `Cambiar estrategia de puja`
  - `¿En qué quieres centrarte? ⏩ Conversiones`
