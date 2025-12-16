# takamakabellezaintegral.com

[![takamakabellezaintegral.com](/uploads/base/icon.svg)](https://takamakabellezaintegral.com/)


## STEPS


### Local

- If new project (not fork):
  - Copy [takamakabellezaintegral.com project files](https://github.com/seacomoseo/takamakabellezaintegral.com)
  - `git submodule add https://github.com/seacomoseo/sansoul.git themes/sansoul`
- Else if fork:
  - Download submódule theme files: `git submodule update --init --recursive`
- Now you can see the run project in the browser with the `do server` comand
- `README.md` ⏩ edit baseURL ("takamakabellezaintegral.com") + delete steps bit by bit
- Design
  - You can edit any file with the same structure of theme sansoul
  - GENERAL
    - `config.yml`
    - `data/*.{yml,md}`
  - IMG + LOGO + FAVICON
    - `uploads/` folder ⏩ [Compress image tool](https://compressor.io/)
      - `base/poster.svg`
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
  - HTML: `data/config.yml ⏩ langs[*].html.{head,body}`
  - CSS: `assets/css/` ⏩ `{*,_variables-custom.scss,_custom.scss}`
  - JS: `assets/js/*,custom.js`
  - IMG: `uploads/*`
  - REDIRECTS: `assets/redirects.md`
  - ROBOTS: `assets/robots.md`
  - If Multilanguaje and Multihosting, add `cp ./public/[es|en]/404.html ./public/` in `netlify.toml ⏩ build.command`
  - Try in Safari and Firefox
  - Check in [W3 Validator](https://validator.w3.org/)
  - Check in [PageSpeed Insights](https://pagespeed.web.dev/)


### After client validate web


#### Domain

- If Cloudflare Pages
  - [Custom domains](https://dash.cloudflare.com/?to=/:account/pages/view/takamaka/domains)
  - `Set up a custom domains`
  - `takamakabellezaintegral.com`
  - `Continue`
  - Add `DNS Records` copied from Cloudflare Pages to Domain gestor:
    - From: `takamakabellezaintegral.com`
      DNS Record: `CNAME`
      To: `takamaka.pages.dev`
    - From: `www`
      DNS Record: `CNAME`
      To: `takamaka.pages.dev`
  - `Activate domain` (if `Begin DNS transfer` end)
  - Repeat with `www.takamakabellezaintegral.com`
  - ...........................................................


#### [Google Search Console](https://search.google.com/search-console)

- Add property
- Verify versions ⏩ `data/config.yml`
  - `ga4`
  - `g_site_verify`
  - `g_file_verify`
  - DNS:
    From: `@`
    DNS Record: `TXT`
    To: `google-site-verification=[g_site_verify]`
- Link with Analytics
- Add sitemap.xml


#### [Google My Business](https://business.google.com/)

- `Add company ⏩ ...` ⏩ whait 13 days to receive postal and insert code to verify


##### Delivery

Send to all collaborators next:

###### WhatsApp

```md
*ENTREGA WEB takamakabellezaintegral.com*

Te dejo aquí este mensaje como referencia (también te lo paso por email con el asunto `ENTREGA WEB takamakabellezaintegral.com`).

En el siguiente enlace tienes instrucciones sobre cosas referentes a tu sitio web (cómo modificar cosas, información extra, ect.):

https://seacomoseo.com/entrega/

No es necesario que lo veas, solo lo es si quieres hacer cosas por tu cuenta o si no estoy disponible.

¡Un saludo!
```

###### Mail

```
Asunto: ENTREGA WEB takamakabellezaintegral.com
Cuerpo:
Te dejo aquí este email como referencia.

En el siguiente enlace tienes instrucciones sobre cosas referentes a tu sitio web (cómo modificar cosas, información extra, ect.):

https://seacomoseo.com/entrega/

No es necesario que lo veas, solo lo es si quieres hacer cosas por tu cuenta o si no estoy disponible.

¡Un saludo!
```
