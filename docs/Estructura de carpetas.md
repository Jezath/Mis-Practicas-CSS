# Estructura de carpetas para proyectos pequeños

En proyectos web, los nombres de las carpetas dependen del tipo de proyecto, su escala y las tecnologías utilizadas, pero hay convenciones comunes que se usan para organizar los archivos de manera clara y escalable. A continuación, te detallo los nombres de carpetas más habituales en proyectos web, junto con su propósito:

## Carpetas comunes en proyectos web

1. `css/`
   - Contiene archivos de hojas de estilo (CSS).
   - Ejemplos: `main.css`, `styles.css`, `theme.css`.
   - A veces se usa `styles/` como alternativa.

2. `js/`
   - Almacena archivos JavaScript.
   - Ejemplos: `main.js`, `app.js`, `utils.js`.
   - Alternativas: `scripts/` o `javascript/`.

3. `html/`
   - Guarda archivos HTML secundarios (el `index.html` suele estar en la raíz).
   - Ejemplos: `about.html`, `contact.html`.
   - No siempre se usa, ya que algunos proyectos mantienen todos los HTML en la raíz.

4. `assets/`
   - Centraliza recursos estáticos como imágenes, fuentes, íconos, etc.
   - Subcarpetas comunes:
     - `img/` o `images/`: Para imágenes (`logo.png`, `banner.jpg`).
     - `fonts/`: Para fuentes personalizadas.
     - `icons/`: Para íconos o favicons.
     - `media/`: Para videos, audios u otros archivos multimedia.
   - Alternativas: `static/` o `resources/`.

5. `src/`
   - Contiene el código fuente antes de ser procesado (usado en proyectos con compiladores o frameworks como React, Vue, etc.).
   - Ejemplos: archivos JavaScript, TypeScript, Sass, o plantillas.
   - Subcarpetas típicas: `components/`, `pages/`, `utils/`.

6. `dist/` o `build/`
   - Almacena los archivos compilados o listos para producción (minificados, optimizados, etc.).
   - Ejemplos: `index.html`, `bundle.js`, `styles.min.css`.
   - Usado en proyectos con herramientas como Webpack, Vite o Parcel.

7. `public/`
   - Contiene archivos estáticos que se sirven directamente al navegador sin procesamiento.
   - Común en frameworks como Next.js o Create React App.
   - Ejemplos: `favicon.ico`, `robots.txt`, imágenes, `index.html`.
   - A veces reemplaza o complementa `assets/`.

8. `components/`
   - Almacena componentes reutilizables, especialmente en frameworks como React, Vue o Angular.
   - Ejemplos: `Header.js`, `Footer.jsx`.
   - Puede estar dentro de `src/` o en la raíz del proyecto.

9. `pages/`
   - Contiene archivos que representan páginas específicas del sitio.
   - Común en frameworks o generadores de sitios estáticos.
   - Ejemplos: `Home.jsx`, `About.js`.
   - A veces se combina con `html/` en proyectos simples.

10. `utils/` o `helpers/`
    - Guarda funciones, utilidades o módulos reutilizables.
    - Generalmente JavaScript o TypeScript.
    - Ejemplos: `api.js`, `formatDate.js`.

11. `data/`
    - Almacena datos estáticos como archivos JSON, YAML o CSV usados en el proyecto.
    - Ejemplos: `products.json`, `config.yaml`.

12. `tests/` o `__tests__/`
    - Contiene archivos de pruebas unitarias o de integración.
    - Ejemplos: `app.test.js`, `component.spec.js`.
    - Común en proyectos con Jest, Mocha o Vitest.

13. `docs/`
    - Guarda documentación del proyecto, como guías, especificaciones o archivos Markdown.
    - Ejemplos: `API.md`, `setup.md`.

14. `node_modules/`
    - Generada automáticamente al instalar dependencias con npm o Yarn.
    - Contiene las librerías y paquetes externos.
    - No se sube a control de versiones (se ignora en `.gitignore`).

15. `vendor/`
    - Almacena librerías externas o de terceros no gestionadas por un administrador de paquetes.
    - Ejemplo: archivos de jQuery o Bootstrap descargados manualmente.
    - Poco común hoy en día.

16. `config/`
    - Contiene archivos de configuración para herramientas o frameworks.
    - Ejemplos: `webpack.config.js`, `vite.config.js`.

17. `content/`
    - Usada en generadores de sitios estáticos (como Hugo o Gatsby) para almacenar contenido en Markdown u otros formatos.
    - Ejemplos: `posts/`, `blog/`.

18. `layouts/` o `templates/`
    - Contiene plantillas reutilizables para generar páginas.
    - Común en generadores de sitios estáticos o CMS.
    - Ejemplos: `base.html`, `post-template.html`.


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

---

## Explicación detallada del JavaScript para las animaciones de entrada


1. `const sections = document.querySelectorAll('.section');`

   Selecciona todos los elementos con la clase `.section`, es decir, todos los bloques que queremos animar.  `sections` es un `NodeList`.

2. `new IntersectionObserver(...)` 

   `IntersectionObserver` es una API nativa de JavaScript que detecta cuando un elemento entra (o sale) del viewport.  
   En este caso, estamos diciendo: “cuando una sección entre al 20% de visibilidad (por `threshold: 0.2`), dispara una función”.

3. `entries.forEach((entry, index) => { ... })`  

   -    El `observer` nos da una lista de `entries`, que son los elementos observados. 

   -    `entry` contiene información de cada elemento: si es visible, su posición, etc.  

   -    `index` es su posición en esa lista actual (¡pero ojo! no es su índice global fijo, lo explico abajo).

4. `if (entry.isIntersecting)`

   Solo animamos si el elemento está actualmente intersectando el viewport (es decir, se está viendo al hacer scroll).

5. `el.style.transitionDelay = \${index * 150}ms\;`  
   
   Aquí aplicamos el delay en cascada:  
   - Primer elemento: `0ms`  
   - Segundo: `150ms`  
   - Tercero: `300ms`  
   - etc.  

   Esto hace que aparezcan uno tras otro en orden.

6. `el.classList.add('visible');`

   Agrega la clase `.visible` que activa la animación CSS (`opacity: 1` y `transform: none`).

7. **`observer.unobserve(el);`**  

   Dejamos de observar el elemento para que la animación no se repita cada vez que hagas scroll.

   > Si quieres que se repita al volver a aparecer, puedes quitar esta línea.

8. `sections.forEach(section => observer.observe(section));` 

   Finalmente, le decimos al `observer` que observe todos los elementos.


### Notas sobre el `index`

-   El `index` que usamos en el `.forEach` es del array `entries`, **no del DOM total**.  

-   Si quieres aplicar delays según el orden real en el HTML, habría que hacer algo como:

```javascript
const realIndex = Array.from(sections).indexOf(entry.target);
```

