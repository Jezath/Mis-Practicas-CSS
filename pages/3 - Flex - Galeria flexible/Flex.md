# Flex

Flex es una de las propiedades más potentes y usadas en CSS para alinear y distribuir elementos fácilmente en un contenedor.

## ¿Qué hace `display: flex?`

Convierte un contenedor en un flex container, lo que le da control sobre cómo se colocan sus hijos (flex items).

```css
.container {
  display: flex;
}
```

Ahora todos los elementos dentro de .container serán controlados por las reglas de Flexbox.

## Propiedades principales que se usan con `display: flex`

#### Dirección del eje

```css
flex-direction: row;        /* (por defecto) horizontal, de izquierda a derecha, row-reverse */
flex-direction: column;     /* vertical, de arriba hacia abajo, column-reverse */
```

#### Dirección de envoltura

```css
flex-wrap: wrap;         /* permite que los elementos bajen a otra línea si no caben, por defecto es no-wrap */
```

#### Distribución de espacio horizontal


```css
justify-content: flex-start;    /* al inicio del eje principal */
justify-content: center;        /* centrado en el eje principal */
justify-content: flex-end;      /* al final del eje principal */
justify-content: space-between; /* espacio entre elementos */
justify-content: space-around;  /* espacio alrededor */
... Hay algunas más
```

#### Distribución de espacio vertical

```css
align-items: flex-start;   /* arriba (si es columna) o a la izquierda (si es fila) */
align-items: center;       /* centrado verticalmente u horizontalmente */
align-items: stretch;      /* (por defecto) estira los elementos */
```

#### Distribución del espacio de los elementos hijos

```css
flex-grow: 0;       /* Cuánto puede crecer un item si hay espacio extra (0 = no crece) */
flex-shrink: 1;     /* Cuánto puede encogerse si no hay espacio (1 = se encoge si hace falta) */
flex-basis: auto;   /* Tamaño base antes de aplicar grow o shrink */
flex: 1;	        /* Atajo para combinar las tres de arriba (flex: 1 0 200px) */
align-self: auto;   /* Alineación vertical individual (sobrescribe align-items) */
order: 0;           /* Cambia el orden visual sin cambiar el orden en el HTML */
```
---

![](https://preview.redd.it/vd9dc7wfk9471.png?auto=webp&s=f6c78331f2c9fb2f8a13837e480a572d7c266752)