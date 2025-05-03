# Grid Areas

Una grid area es un nombre que le das a una zona específica de tu layout (rejilla) en CSS Grid. Esto te permite colocar elementos fácilmente sin tener que contar columnas o filas manualmente.

## ¿Cómo usar `grid-area` y `grid-template-areas`?

Primero, necesitas un contenedor con `display: grid`.

```css
.container {
  display: grid;
  grid-template-columns: 1fr 2fr;
  grid-template-rows: auto auto;
}
```

## Nombrar áreas con `grid-template-areas`

Aquí defines zonas usando comillas (" ") para cada fila y escribes los nombres de las áreas.

```css
.container {
  display: grid;
  grid-template-columns: 1fr 2fr;
  grid-template-rows: auto auto;
  grid-template-areas:
    "header header"
    "sidebar main";
}
```

En este ejemplo:

- La primera fila tiene dos columnas llamadas header.
- La segunda fila tiene sidebar a la izquierda y main a la derecha.

## Asignar áreas a los elementos con `grid-area`

Cada hijo del grid se asigna a su área por nombre:

```css
.header {
  grid-area: header;
}

.sidebar {
  grid-area: sidebar;
}

.main {
  grid-area: main;
}
```

HTML correspondiente:

```html
<div class="container">
  <div class="header">Encabezado</div>
  <div class="sidebar">Barra lateral</div>
  <div class="main">Contenido principal</div>
</div>
```

## Espacios vacíos

Puedes dejar espacios vacíos con un punto (.):

```css
grid-template-areas:
  "header header"
  ". main";
```

### Ventajas de usar grid-area:

- **Legibilidad:** Sabes qué es cada parte con solo leer los nombres.
- **Mantenimiento fácil:** Reorganizar el layout es tan simple como cambiar los nombres en grid-template-areas.
- Ideal para diseños de páginas completas (cabecera, contenido, pie, etc.).

---

![](https://miro.medium.com/v2/resize:fit:1200/1*ABgYntR1ZJbroJWeHcFr9w.png)