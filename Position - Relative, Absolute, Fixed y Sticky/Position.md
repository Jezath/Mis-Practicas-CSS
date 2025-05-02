# Position

La propiedad `position` se usa para controlar cómo se posiciona un elemento en la página web. Hay varias opciones de posicionamiento, y cada una se comporta de forma diferente. Aquí te explico las más importantes:

### ¿Cómo posicionar los elementos que tengan position?

La propiedad position define cómo se comporta un elemento en relación con su contenedor o la página. A partir de ahí, puedes moverlo con las propiedades:

- top
- right
- bottom
- left

## Static (por defecto)

Es el valor por defecto. El elemento se coloca en el flujo normal del documento.

- No se puede usar `top`, `right`, `bottom,` ni `left`.

## Relative

El elemento se posiciona relativo a su posición original.

- Puedes moverlo usando `top`, `right`, `bottom` o `left`, pero ocupa el mismo espacio que si no se hubiera movido.

```html
<div style="position: relative; top: 20px; left: 30px;">
  ¡Me moví 20px abajo y 30px a la derecha!
</div>
```

## Absolute

El elemento se posiciona de forma absoluta respecto al primer antecesor (elemnto padre) con position: `relative`, absolute, fixed o sticky.

- Sale del flujo del documento y no ocupa espacio.

- Si ve que su contenedor padre no tiene position `relative`, se posiciona respecto al html.

```html
<div style="position: relative;">
  <div style="position: absolute; top: 0; right: 0;">
    ¡Estoy en la esquina superior derecha de este contenedor!
  </div>
</div>
```

## Fixed

Se posiciona de forma fija respecto a la ventana del navegador.

- No se mueve aunque hagas scroll.

- Útil para menús o botones flotantes.

```html
<div style="position: fixed; bottom: 10px; right: 10px; background: red;">
  ¡Siempre estoy en la esquina inferior derecha!
</div>
```

## Sticky

Es una mezcla entre relative y fixed.

- El elemento se comporta como relative hasta que se alcanza un cierto punto del scroll, y ahí se "pega" como fixed.

- Muy útil para encabezados o menús que deben quedarse visibles mientras haces scroll.

```html
<header style="position: sticky; top: 0; background: yellow;">
  ¡Me quedo arriba cuando haces scroll!
</header>
```

### ¿Cómo usar top, left, etc.?

Estas propiedades solo funcionan si usas `relative`, `absolute`, `fixed` o `sticky`.

```css
/* Forma de fijar un elemento arriba */
.top-izquierda {
  position: absolute;
  top: 0;
  left: 0;
}

/* Forma de centrar un elemento */
.centro {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

### Resumen visual rápido:

| Valor     | Posicionado respecto a...         | ¿Sigue el flujo del documento? | ¿Se puede usar `top`, `left`, etc.? |
|-----------|-----------------------------------|-------------------------------|-------------------------------------|
| `static`  | Flujo normal                      | Sí                            | No                                  |
| `relative`| Su posición original              | Sí                            | Sí                                  |
| `absolute`| Antecesor posicionado (no `static`)| No                           | Sí                                  |
| `fixed`   | Ventana del navegador             | No                            | Sí                                  |
| `sticky`  | Su contenedor + scroll            | Sí (hasta cierto punto)       | Sí                                  |


---

![](https://miro.medium.com/v2/resize:fit:1200/1*x5xm9DVS6QouWCAeII9w8A.png)