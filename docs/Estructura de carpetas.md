# Estructura de carpetas para proyectos pequeños

En proyectos web, los nombres de las carpetas dependen del tipo de proyecto, su escala y las tecnologías utilizadas, pero hay convenciones comunes que se usan para organizar los archivos de manera clara y escalable. A continuación, te detallo los nombres de carpetas más habituales en proyectos web, junto con su propósito:

### Carpetas comunes en proyectos web

1.  `css/`
    
    - Contiene archivos de hojas de estilo (CSS).
        
    - Ejemplo: main.css, styles.css, theme.css.
        
    - A veces se usa styles/ como alternativa.
        
2.  `js/`
    
    - Almacena archivos JavaScript.
        
    - Ejemplo: main.js, app.js, utils.js.
        
    - Alternativas: scripts/ o javascript/.
        
3.  `html/`
    
    - Guarda archivos HTML secundarios (el index.html suele estar en la raíz).
        
    - Ejemplo: about.html, contact.html.
        
    - No siempre se usa, ya que algunos proyectos mantienen todos los HTML en la raíz.
        
4.  `assets/`
    
    - Centraliza recursos estáticos como imágenes, fuentes, íconos, etc.
        
    - Subcarpetas comunes:
        
      - **img/ o images/:** Para imágenes (logo.png, banner.jpg).
            
      - **fonts/:** Para fuentes personalizadas.
            
      - **icons/:** Para íconos o favicons.
            
      - **media/:** Para videos, audios u otros archivos multimedia.
            
    - Alternativas: static/ o resources/.
        
5.  `src/`
    
    - Contiene el código fuente antes de ser procesado (usado en proyectos con compiladores o frameworks como React, Vue, etc.).
        
    - Ejemplo: Archivos JavaScript, TypeScript, Sass, o plantillas.
        
    - Subcarpetas: components/, pages/, utils/.
        
6.  `dist/` o `build/`
    
    - Almacena los archivos compilados o listos para producción después de procesar el código (minificados, optimizados, etc.).
        
    - Ejemplo: index.html, bundle.js, styles.min.css.
        
    - Usado en proyectos con herramientas como Webpack, Vite o Parcel.
        
7.  `public/`
    
    - Contiene archivos estáticos que se sirven directamente al navegador sin procesamiento (común en frameworks como Next.js o Create React App).
        
    - Ejemplo: favicon.ico, robots.txt, imágenes, o index.html.
        
    - A veces reemplaza o complementa assets/.
        
8.  `components/`
    
    - Almacena componentes reutilizables, especialmente en proyectos con frameworks (React, Vue, Angular).
        
    - Ejemplo: Header.js, Footer.jsx.
        
    - Puede estar dentro de src/ o en la raíz.
        
9.  `pages/`
    
    - Contiene archivos que representan páginas específicas del sitio (usado en frameworks o generadores de sitios estáticos).
    
    - Ejemplo: Home.jsx, About.js.
    
    - A veces se combina con html/ en proyectos simples.
        
10.  `utils/` o `helpers/`
    
    - Guarda funciones, utilidades o módulos reutilizables (generalmente JavaScript o TypeScript).
    
    - Ejemplo: api.js, formatDate.js.
    

11.  `data/`
    
    - Almacena datos estáticos como archivos JSON, YAML o CSV usados en el proyecto.
        
    - Ejemplo: products.json, config.yaml.
        
12.  `tests/` o `__tests__/`
    
    - Contiene archivos de pruebas unitarias o de integración.
        
    - Ejemplo: app.test.js, component.spec.js.
        
    - Común en proyectos con Jest, Mocha o Vitest.
        
13.  `docs/`
    
    - Guarda documentación del proyecto, como guías, especificaciones o archivos Markdown.
        
    - Ejemplo: API.md, setup.md.
        
14.  `node_modules/`
    
    - Generada automáticamente al instalar dependencias con npm o Yarn.
        
    - Contiene las librerías y paquetes externos.
        
    - No se sube a control de versiones (se ignora en .gitignore).
        
15.  `vendor/`
    
    - Almacena librerías externas o de terceros que no se gestionan con un administrador de paquetes (poco común hoy en día).
        
    - Ejemplo: Archivos de jQuery o Bootstrap descargados manualmente.
        
16.  `config/`
    
    - Contiene archivos de configuración para herramientas o frameworks.
        
    - Ejemplo: webpack.config.js, vite.config.js.
        
17.  `content/`
    
    - Usada en generadores de sitios estáticos (como Hugo o Gatsby) para almacenar contenido en Markdown u otros formatos.
        
    - Ejemplo: posts/, blog/.
        
18.  `layouts/` o `templates/` -          
    
    - Contiene plantillas reutilizables para generar páginas (común en generadores de sitios estáticos o CMS).
        
    - Ejemplo: base.html, post-template.html.

### Ejemplos de estructura de carpetas

Ejemplo de estructura para un proyecto web sencillo por tipos

```text
mi_sitio/
├── index.html
├── css/
│   ├── main.css
│   ├── about.css
│   ├── contact.css
│   └── global.css
├── html/
│   ├── about.html
│   └── contact.html
├── assets/
│   ├── img/
│   │   ├── logo.png
│   │   └── banner.jpg
└── README.md
```

Ejemplo de estructura para un proyecto web sencillo

```text
mi_proyecto/
├── index.html
├── css/
│   ├── main.css
│   ├── about.css
├── js/
│   ├── app.js
├── html/
│   ├── about.html
│   ├── contact.html
├── assets/
│   ├── img/
│   │   ├── logo.png
│   ├── fonts/
│   │   ├── custom-font.woff
└── README.md
```

Ejemplo de estructura para un proyecto con framework (ej. React)

```text
mi_app/
├── public/
│   ├── index.html
│   ├── favicon.ico
├── src/
│   ├── components/
│   │   ├── Header.jsx
│   │   ├── Footer.jsx
│   ├── pages/
│   │   ├── Home.jsx
│   │   ├── About.jsx
│   ├── css/
│   │   ├── main.css
│   ├── utils/
│   │   ├── api.js
├── tests/
│   ├── Home.test.jsx
├── node_modules/
├── package.json
└── README.md
```

### Notas importantes

-   `Convenciones:` Los nombres como css/, js/, assets/ son ampliamente reconocidos y facilitan la colaboración. Evita nombres ambiguos como stuff/ o files/.
    
-   `Proyectos pequeños:` En sitios web simples, puedes omitir carpetas como src/, dist/ o tests/ y mantener solo css/, js/, y assets/.
    
-   `Frameworks:` Si usas frameworks o herramientas (React, Vue, Angular, Next.js), la estructura puede incluir carpetas específicas como pages/, components/, o public/.
    
-   `Personalización:` Adapta la estructura según las necesidades del proyecto, pero mantén consistencia para facilitar el mantenimiento.