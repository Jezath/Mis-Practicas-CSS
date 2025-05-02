# @media 

## ¿Qué son las media queries en CSS?

Las media queries son una herramienta en CSS que te permite aplicar estilos de manera condicional, según las características del dispositivo (como el tamaño de pantalla, la resolución, la orientación, etc.).

Esto es clave para el diseño responsive, es decir, hacer que tu sitio web se vea bien en computadoras, tablets y celulares.

### ¿Cómo se usan?

```css
@media (condición) {
  /* Estilos que se aplican si se cumple la condición */
}
```

Por ejemplo, si quieres cambiar el fondo del body cuando el ancho de la pantalla sea menor a 768px (típico en móviles):

```css
@media (max-width: 768px) {
  body {
    background-color: lightgray;
  }
}
```

Varios ejemplos útiles:

1. Responsive para móviles:

```css
@media (max-width: 600px) {
  .menu {
    display: none;
  }
}
```

2. Estilo especial al imprimir:

```css
@media print {
  body {
    background: white;
    color: black;
  }
}
```

3. Modo oscuro automático según preferencias del usuario:

```css
@media (prefers-color-scheme: dark) {
  body {
    background: #111;
    color: #eee;
  }
}
```

### Range syntax

Claro, aquí tienes un ejemplo de media queries usando media feature ranges (sintaxis moderna y limpia) para cubrir:

```css
/* Móviles (pantallas pequeñas hasta 600px) */
@media (width <= 600px) {
  body {
    background-color: #f0f8ff;
    font-size: 14px;
  }
}
```

```css
/* Tablets y laptops pequeñas (601px hasta 1024px) */
@media (601px <= width <= 1024px) {
  body {
    background-color: #e6f7ff;
    font-size: 16px;
  }
}
```

```css
/* Desktops (mayor a 1024px) */
@media (width > 1024px) {
  body {
    background-color: #d0eaff;
    font-size: 18px;
  }
}
```

---

## @media y @media screen

En CSS, la diferencia entre @media y @media screen radica en el tipo de medio (media type) al que se está aplicando la regla.

### @media 

Esto es una regla general que puede incluir diferentes tipos de medios, como screen, print, all, etc. Ejemplo:

```css
@media (max-width: 600px) {
  body {
    background: lightblue;
  }
}
```

Aquí no se especifica el tipo de medio, por lo tanto se asume all, lo que significa que se aplica a todos los tipos de dispositivos (pantallas, impresoras, etc.) siempre que se cumpla la condición (en este caso, un ancho máximo de 600px).

### @media screen

Esto restringe la regla al tipo de medio screen, que se refiere a pantallas: computadoras, tabletas, móviles, etc.

```css
@media screen and (max-width: 600px) {
  body {
    background: lightgreen;
  }
}
```

Esto no se aplicará al imprimir o en otros medios como proyectores.

### ¿Cuándo usar cada uno?

- Usa @media (sin tipo) cuando quieres que la regla aplique en todos los contextos donde la condición se cumpla.
- Usa @media screen si quieres excluir impresoras u otros medios que no sean pantalla.

