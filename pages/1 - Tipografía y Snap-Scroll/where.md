# :where()

Perfecto, ahora vamos con :where() en CSS. Es similar a :is(), pero con una diferencia clave súper importante: su especificidad siempre es cero, sin importar qué selectores tenga dentro.
Esto lo hace ideal para estilos genéricos, resets o utilidades que no deben ganar prioridad frente a estilos más específicos.

## ¿Para qué sirve `:where()`?

Agrupa múltiples selectores, igual que :is().
Siempre tiene especificidad 0, como si escribieras *.
Útil cuando quieres aplicar estilos sin interferir con reglas más específicas.

## Diferencia entre `:is()` y `:where()`

| Selector   | Agrupa selectores | Hereda especificidad | Ideal para...         |
|------------|-------------------|----------------------|------------------------|
| `:is()`    | Sí                | Sí                   | Agrupar sin repetir    |
| `:where()` | Sí                | No (es 0)            | Resets, defaults, utilidades   |


## Ejemplos de cómo y donde usar `:where()`

#### 1. Básico: Agrupar selectores sin especificidad

```css
:where(h1, h2, h3) {
  margin: 0;
  font-family: sans-serif;
}
```

**Explicación:** Elimina márgenes de todos los títulos, pero permite que otras reglas más específicas los sobrescriban fácilmente.

#### 2. Medio: Reset genérico para formularios

```css
:where(input, textarea, select) {
  font-family: inherit;
  font-size: 1rem;
  outline: none;
}
```

**Explicación:** Aplica estilos base a todos los campos de formulario sin afectar estilos más específicos definidos después.

#### 3. Medio: Estilos base dentro de componentes

```css
.card :where(h2, h3, p) {
  margin: 0;
  line-height: 1.5;
}
```

**Explicación:** Aplica estilos genéricos dentro de una .card sin tener que usar selectores con alta especificidad.

#### 4. Avanzado: Reset de márgenes globales

```css
:where(h1, h2, h3, h4, h5, h6, p, ul, ol) {
  margin: 0;
  padding: 0;
}

```
**Explicación:** Sirve como reset visual para toda la estructura del documento.

#### 5. Avanzado: Combinado con :is() para más control

```css
:is(nav, .menu) :where(a, button) {
  all: unset;
  padding: 8px 12px;
  cursor: pointer;
}
```

**Explicación:** Resetea completamente enlaces o botones dentro de menús, pero lo hace sin aumentar la especificidad.

#### 6. Extra: Tema oscuro sin sobrescribir otras reglas

```css
.dark :where(h1, h2, h3, p) {
  color: white;
}
```

**Explicación:** Aplica un tema oscuro sin que bloquee reglas específicas como .card h1 { color: red; }.

## Cuándo usar `:where()` en vez de `:is()`

- Cuando no quieres pelear con la especificidad.
- En estilos base, resets o utilidades.
- Si estás creando un framework CSS o sistema de diseño.

---

### Ejemplo HTML + CSS: Combinando `:where()` y `:is()`

Ejemplo completo en HTML + CSS, donde usamos :where() para estilos base/reset y :is() para estilos más específicos e interactivos.

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Ejemplo con :where() y :is()</title>
  <style>
    /* === RESET BASE usando :where() === */
    :where(h1, h2, h3, p, ul, ol, li, button, a) {
      margin: 0;
      padding: 0;
      font-family: system-ui, sans-serif;
      color: inherit;
      text-decoration: none;
      list-style: none;
    }

    :where(button, a) {
      border: none;
      background: none;
      cursor: pointer;
    }

    body {
      padding: 20px;
      background-color: #f9f9f9;
    }

    /* === Estilos compartidos con :is() === */
    :is(.btn-primary, .btn-secondary) {
      padding: 10px 20px;
      font-weight: bold;
      border-radius: 5px;
      transition: background-color 0.3s ease;
      color: white;
      display: inline-block;
      margin-right: 10px;
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

    /* === Secciones con títulos y párrafos resetados === */
    section {
      margin-top: 30px;
    }

    .card :where(h2, p) {
      margin-bottom: 10px;
      line-height: 1.4;
    }

    .card {
      background-color: white;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
      max-width: 400px;
    }
  </style>
</head>
<body>

  <h1>Bienvenido</h1>

  <button class="btn-primary">Acción Principal</button>
  <button class="btn-secondary">Acción Secundaria</button>

  <section class="card">
    <h2>Título de la tarjeta</h2>
    <p>Este es un texto dentro de una tarjeta. Gracias a <code>:where()</code>, el margen fue reseteado sin afectar otros estilos.</p>
  </section>

</body>
</html>
```

---

## ¿Qué se está mostrando aquí?

- `:where()` limpia márgenes/padding y aplica estilos base sin aumentar especificidad.

- `:is()` agrupa botones con estilos compartidos y permite personalizar hover sin repetir reglas.
Todo se mantiene modular y escalable, ideal si estás trabajando en un sistema de diseño o una UI más grande.
