# Grid

La propiedad display: grid en CSS es una forma de crear diseños en dos dimensiones (filas y columnas) de manera muy flexible y ordenada.

## ¿Qué es `display: grid`?
Cuando le das a un contenedor (como un `<div>`) la propiedad display: grid, estás diciéndole al navegador que ese contenedor va a comportarse como una rejilla (grid), y que sus elementos hijos se van a colocar dentro de esa rejilla, siguiendo las reglas que tú definas.


## Propiedades para el elemento padre

Las siguientes propiedades van en el elemento padre o contenedor. Con ellas controlaremos como se tienen que comportar los elementos hijos en conjunto.

```css
.container {
  display: grid; /* Activa el sistema de grid en el contenedor */
}
```

#### Dirección de los elementos

```css
grid-auto-flow: row; /* por defecto es row, pero tenemos: column, row-dense,  column-dense*/
```

#### Crear filas y columnas fijas

```css
/* podemos usar funciones como repeat() o minmax() para limitar o especificar la cantidad de celdas */
grid-template-columns: 100px 200px 1fr; /* cada valor repesenta una columna */
grid-template-rows: auto 100px 2fr;     /* cada valor repesenta una fila */
```

#### Tamaño de filas o columnas automáticas 

```css
grid-auto-rows: 100px;
grid-auto-columns: 200px;
```

#### Espacio entre filas y/o columnas

```css
row-gap: 20px;     /* arriba abajo */
column-gap: 10px;  /* izquierda derecha */
gap: 10px;         /* igual para filas y columnas */
```

#### Alineamiento grupal de los elementos

```css
justify-items: ;    /* start, end, center, stretch; -> Alinea los elementos hijos horizontalmente dentro de su celda. */
align-items: ;      /* Alinea los hijos verticalmente dentro de su celda. */
place-items: ;      /* Es atajo para align-items + justify-items. */


justify-content: ;  /* Alinea todo los elementos hijos horizontalmente */
align-content: ;    /* Alinea todo los elementos hijos verticalmente  */
place-content: ;    /* Atajo para align-content + justify-content. Controlan cómo se alinea todo el grid completo dentro del contenedor.*/
```

#### Grid área

```css
grid-template-areas:
  "header header"
  "sidebar main"
  "footer footer";
```

## Propiedades para los elementos hijos

Estas propiedades van directamente en los elementos hijos, de esta forma podemos indicar un comportamiento específico entre los demás.

#### Celdas irregulares

```cs
/* Indican en qué columna empieza y termina un elemento. */
grid-column-start: 1;
grid-column-end: 3;
grid-column: 1 / 3; /* atajo */
```

#### Grid área


```cs
grid-area: header;

/* row-start / column-start / row-end / column-end */
grid-area: 1 / 2 / 3 / 4; /* atajo */
```

#### Alineamiento individual de los elementos

Estas propiedades controlan cómo se alinea ese único elemento en su celda, igual que `justify-items` y `align-items`, pero solo para ese ítem.

```css
justify-self: ; /* alinea horizontalmente */
align-self: ;   /* alinea verticalemente */
place-self: ;   /* atajo */
```

---

![](https://preview.redd.it/phlaefsgoeb71.png?auto=webp&s=6c245020cd1512a7327dc7904b459a0774c0991b)