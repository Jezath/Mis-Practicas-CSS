# :is( )

el pseudo-selector `:is()` en CSS sirve para agrupar múltiples selectores que comparten las mismas reglas, lo que ayuda a reducir repetición y hacer el código más limpio. Aquí te muestro cómo usarlo con ejemplos de distintos niveles:

####  1. Básico: Agrupar varios elementos

```css
:is(h1, h2, h3) {
  color: steelblue;
}
```

**Qué hace:** Aplica el mismo color steelblue a todos los encabezados `h1`, `h2` y `h3`.

#### 2. Medio: Combinar con clases e hijos

```css
:is(.card, .box) > p {
  font-size: 16px;
}
```

**Qué hace:** Establece el tamaño de fuente de los párrafos (`<p>`) que son hijos directos de elementos con clase `.card` o `.box`.

#### 3. Medio con :hover

```css
:is(button, a):hover {
  background-color: navy;
  color: white;
}
```


**Qué hace:** Cambia el color de fondo y texto cuando el usuario pasa el cursor sobre un `<button>` o un `<a>`.

#### 4. Avanzado: Estados interactivos y combinaciones

```css
.container :is(button.primary, a.cta):is(:hover, :active) {
  transform: scale(1.05);
  transition: transform 0.2s ease;
}
```

**Qué hace:**
Aplica una animación de "zoom" a botones con clase `.primary` y enlaces con clase `.cta` dentro de `.container`.
Solo ocurre cuando están en estado `:hover` o `:active`.

#### 5. Avanzado: Con combinadores y pseudo-elementos

```css
:is(section, article) > :is(h2, h3)::first-letter {
  font-size: 200%;
  color: crimson;
}
```

**Qué hace:**
Aplica estilos solo a la primera letra de h2 o h3 que estén dentro de un section o article.

> **Notas útiles:**
> `:is()` mejora el rendimiento porque evita repeticiones largas de selectores.
El selector más específico dentro de `:is()` dicta la especificidad total.
También puedes anidar `:is()` si necesitas agrupar grupos más complejos (aunque rara vez es necesario).

---

### Ejemplo de :is() para aplicar estilos comumes a varios elementos y clases

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Ejemplo con :is()</title>
  <style>
    :is(h1, h2, h3) {
      color: steelblue;
    }

    :is(.card, .box) > p {
      font-size: 16px;
    }

    :is(button, a):hover {
      background-color: navy;
      color: white;
    }

    .container :is(button.primary, a.cta):is(:hover, :active) {
      transform: scale(1.05);
      transition: transform 0.2s ease;
    }

    :is(section, article) > :is(h2, h3)::first-letter {
      font-size: 200%;
      color: crimson;
    }
  </style>
</head>
<body>

  <h1>Título Principal</h1>
  <div class="card"><p>Contenido de una tarjeta</p></div>
  <div class="box"><p>Contenido de una caja</p></div>

  <button>Botón Normal</button>
  <a href="#">Enlace Normal</a>

  <div class="container">
    <button class="primary">Botón Interactivo</button>
    <a href="#" class="cta">Llamada a la Acción</a>
  </div>

  <section>
    <h2>Subtítulo en Section</h2>
  </section>

  <article>
    <h3>Subtítulo en Article</h3>
  </article>

</body>
</html>
```

--- 
## Ejemplos útiles de `is:( )`
¡Claro! Aquí tienes una lista de ejemplos útiles y prácticos donde :is() mejora la limpieza del código y te ahorra trabajo. Todos están explicados para que puedas aplicarlos directamente:

#### 1. Listas estilizadas

```css
:is(ul, ol) > li {
  margin-bottom: 8px;
}
```

**Usos comunes:** Aplica espacio entre ítems de listas ordenadas (ol) y no ordenadas (ul), sin repetir reglas.

#### 2. Formularios unificados

```css
form :is(input, select, textarea) {
  border: 1px solid #ccc;
  padding: 10px;
  font-size: 14px;
}
```

**Usos comunes:** Aplica estilos consistentes a todos los campos de un formulario.

#### 3. Resaltar elementos activos o seleccionados

```css
:is(.tab, .menu-item):is(.active, :hover) {
  background-color: #f0f0f0;
  font-weight: bold;
}
```

**Usos comunes:** Estiliza pestañas o ítems de menú que estén activos o bajo el cursor.

#### 4. Aplicar estilos a componentes con distintas clases

```css
:is(.btn-primary, .btn-secondary, .btn-danger) {
  padding: 12px 20px;
  border-radius: 4px;
}
```

**Usos comunes:** Cuando tienes muchos tipos de botones pero comparten estilos base.

#### 5. Evitar repeticiones con combinadores

```css
:is(header, footer) nav a {
  color: white;
  text-decoration: none;
}
```

**Usos comunes:** Aplica los mismos estilos a enlaces dentro del nav del header y del footer.

#### 6. Reiniciar márgenes de títulos dentro de distintas secciones

```css
:is(section, article, aside) :is(h1, h2, h3) {
  margin-top: 0;
}
```

**Usos comunes:** Unifica los márgenes de encabezados dentro de varios bloques semánticos.

#### 7. Evitar duplicación con múltiples selectores anidados

```css
:is(.modal, .dialog) :is(button, a):hover {
  opacity: 0.8;
  cursor: pointer;
}
```

**Usos comunes:** Aplica comportamiento interactivo en modales o diálogos, tanto para botones como para enlaces.

#### 8. Media queries y :is()

```css
@media (max-width: 768px) {
  :is(header, .sidebar) {
    display: none;
  }
}
```

**Usos comunes:** Oculta múltiples secciones en vista móvil sin repetir código dentro del media query.

#### 9. Iconos dentro de distintos botones

```css
:is(.btn, .link) > svg {
  margin-right: 6px;
}
```

**Usos comunes:** Aplica espacio a los íconos dentro de botones y enlaces estilizados como botones.

#### 10. Combinar elementos con clases y estados

```css
:is(button, .btn):is(:hover, :focus, :active) {
  background-color: darkslateblue;
  color: white;
}
```

**Usos comunes:** Una sola regla que cubre todos los estados interactivos de distintos tipos de botones.

---

## Casos de usos

### Seleccionar dos clases distintas

En este caso, sí puedes usar `:is()`, pero para este tipo de escenario, una mejor práctica sería usar clases base + modificadores, tipo BEM, o bien utilizar variables CSS.
Aquí van tres formas de lograrlo:

#### Opción 1: Con `:is()` + selector más específico

```css
:is(.btn-primary, .btn-secondary) {
  padding: 10px 20px;
  border: none;
  color: white;
  font-weight: bold;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btn-primary {
  background-color: royalblue;
}

.btn-primary:hover {
  background-color: mediumblue;
}

.btn-secondary {
  background-color: seagreen;
}

.btn-secondary:hover {
  background-color: darkgreen;
}
```

- **Ventajas:** Agrupa lo común y separa lo que cambia. 
- **Desventajas:** No ahorra tanto si tienes muchos tipos de botones.

#### Opción 2: Clases base + modificadoras (estilo BEM)

```css
.btn {
  padding: 10px 20px;
  border: none;
  color: white;
  font-weight: bold;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btn--primary {
  background-color: royalblue;
}

.btn--primary:hover {
  background-color: mediumblue;
}

.btn--secondary {
  background-color: seagreen;
}

.btn--secondary:hover {
  background-color: darkgreen;
}
```

Uso en HTML:

```html
<button class="btn btn--primary">Botón Azul</button>
<button class="btn btn--secondary">Botón Verde</button>
```

- **Ventajas:** Súper escalable, limpio y modular. 
- **Desventajas:** Tienes que recordar usar ambas clases.

#### Opción 3: Usando variables CSS para personalizar

```css
.btn {
  --bg: royalblue;
  --bg-hover: mediumblue;

  padding: 10px 20px;
  border: none;
  color: white;
  font-weight: bold;
  border-radius: 4px;
  cursor: pointer;
  background-color: var(--bg);
  transition: background-color 0.3s ease;
}

.btn:hover {
  background-color: var(--bg-hover);
}

.btn-secondary {
  --bg: seagreen;
  --bg-hover: darkgreen;
}
```

Uso en HTML:

```html
<button class="btn">Primario</button>
<button class="btn btn-secondary">Secundario</button>
```

- **Ventajas:** Súper DRY (Don't Repeat Yourself), flexible, ideal si usas muchos colores. 
- **Desventajas:** Requiere que navegadores soporten variables CSS (lo hacen casi todos hoy en día).

---

## Conclusión:
Usa `:is()` cuando quieras agrupar reglas comunes rápidamente.
Para mantener el código limpio y escalable, lo ideal es usar una clase base (.btn) con modificadores o variables CSS.