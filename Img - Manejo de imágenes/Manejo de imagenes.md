# Manejo de imágenes

## Insertar imágen

Tenemos varias formas de insertar imágenes en una página web y cada una tiene un propósito especial.

- `<img>`:

Son las imágenes que forma parte importante del flujo de contenido de la página web. Podemos usarla dentro de un elemento contenedor, por ejemplo:

```html
<picture> <!-- width, height...  -->
  <img>   <!-- aspect-ratio, object-fit... -->
</picture>
```

- `background-image`: 

Esta forma se usa cuando las imágenes son más de aspecto decorativo o de fondos, por ejemplos en card, fondos de una sección.

```html
<div></div>
```

```css
div {
  background-color: red;
  background-image: url("gato.jpg");
  background-position: top center;
  background-size: cover;
  background-repeat: no-repeat;

  /* atajo */
  background: color image position / size repeat attachment origin clip; /* <- el / es importante va antes del tamaño de la imágen */
}
```

- `::before` o `after`:

Esta forma de insertar imágenes mediante pseudoelementos es muy específica ya que solo funciona con imágenes muy pequeñas como íconos, ademas es muy limitada en cuando al manejo de la misma.

---

## Uso de `aspect-ratio` en la imágen

En desarrollo web, cuando estás trabajando con un `<figure>` que contiene una `<img>` y quieres hacer que la imagen sea responsiva, lo ideal es poner la propiedad `aspect-ratio` en la imagen (`<img>`) directamente.

### ¿Por qué en `<img>` y no en `<figure>`?

Porque el elemento `<img>` es el que realmente contiene y representa el contenido visual con proporciones definidas (por ejemplo, 16:9, 4:3, etc.). Usar `aspect-ratio` en la imagen permite que:

1. Mantenga su relación de aspecto correcta al redimensionarse, especialmente si usas `width: 100%` o lo metes en un contenedor flexible.

2. Evites saltos de diseño al cargar la imagen (lo cual también ayuda con el cumulative layout shift en rendimiento web).

3. El `<figure>` solo actúa como contenedor semántico, no tiene por qué imponer una relación de aspecto a su contenido.

Ejemplo del uso del `aspect-ratio` directamente desde la etiqueta HTML:

```html
<figure>
  <img src="https://images6.alphacoders.com/310/310510.png" alt="Descripción" style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover;">
</figure>
```

Ejemplo desde archivo de CSS separado:

```html
<figure class="media">
  <img src="https://images6.alphacoders.com/310/310510.png" alt="Descripción de la imagen" />
  <figcaption>Texto descriptivo</figcaption>
</figure>
```

```css
.media img {
  width: 100%;
  aspect-ratio: 16 / 9;
  object-fit: cover; /* o contain, dependiendo del diseño */
  display: block;    /* elimina espacio debajo por línea base */
  height: auto;      /* opcional para evitar conflictos */
}
```

Esto hace que la imagen:

- Se ajuste al ancho del contenedor (figure).
- Mantenga su proporción 16:9.
- Recorte o ajuste la imagen con object-fit si es necesario.

---

## Uso de `<picture>` para imágenes adaptativas

Cuando quieras servir diferentes versiones de una imagen dependiendo del ancho de pantalla, usa `<picture>`:

```html
<figure class="media">
  <picture>
    <source srcset="foto-large.jpg" media="(min-width: 1024px)">
    <source srcset="foto-medium.jpg" media="(min-width: 600px)">
    <img src="foto-small.jpg" alt="Descripción" />
  </picture>
  <figcaption>Texto descriptivo</figcaption>
</figure>
```

Y puedes usar el mismo CSS de antes para controlar el estilo del `<img>` dentro de `<picture>`:

```css
.media img {
  width: 100%;
  aspect-ratio: 16 / 9;
  object-fit: cover;
  display: block;
}
```

Con esto logras:

- Una imagen visualmente estable (no salta),
- Que se adapte bien a distintos dispositivos,
- Carga optimizada con imágenes más pequeñas en móviles.

---

## Uso de `::pseudoelementos` para insertar imágenes

Cargar una imagen con pseudoelementos como `::before` o `::after` es una técnica útil para añadir decoraciones o íconos sin tocar el HTML directamente.

Ejemplo: Imagen con `::before` usando content HTML

```html
<div class="icono">Texto con ícono</div>
```

```css
.icono::before {
  content: url("icono.png");
  display: inline-block;
  margin-right: 8px;
  vertical-align: middle;
}
```

Resultado esperado:
Aparece la imagen icono.png antes del texto “Texto con ícono”.


**Notas importantes:**

- Funciona bien con imágenes pequeñas como íconos (PNG, SVG).
- No es compatible con imágenes de fondo (para eso, usa `background-image`).
- Si necesitas más control visual (tamaño, filtros, etc.), lo ideal es usar SVG o `background-image`.

---

### URL para cargar imágenes

#### Unsplash (source.unsplash.com)

Formato básico:

```code
https://source.unsplash.com/[ANCHO]x[ALTO]/?[PALABRA_CLAVE]
```

Ejemplos:

```code
Imagen 800x600 de naturaleza:

https://source.unsplash.com/800x600/?nature

Imagen 1200x800 de ciudad:

https://source.unsplash.com/1200x800/?city
```

Más trucos:

```code
Puedes combinar varias palabras clave:

https://source.unsplash.com/800x600/?nature,water

Imagen aleatoria (cada carga es distinta):

https://source.unsplash.com/random/800x600
```

#### Picsum Photos (picsum.photos)

Formato básico:

```code
https://picsum.photos/[ANCHO]/[ALTO]
```

Ejemplos:

```code
Imagen 600x400 aleatoria:

https://picsum.photos/600/400
```

Más trucos:

```code
Fijar la imagen con ID:

https://picsum.photos/id/237/600/400

Escala de grises:

https://picsum.photos/600/400?grayscale

Imagen borrosa:

https://picsum.photos/600/400?blur

Grayscale + blur juntos:

https://picsum.photos/600/400?grayscale&blur=2
```

#### Palet de colores pasteles

```css
  /* Paleta 1: Tonos suaves y frescos */
  background-color: #faced5; /* Rosa pastel suave */
  background-color: #d5f5e3; /* Verde menta pastel */
  background-color: #dceefc; /* Celeste muy claro */
  background-color: #ff9b8a; /* Coral suave (botón o detalles) */
  color: #333333; /* Gris oscuro para el texto */

  /* Paleta 2: Tonos románticos y elegantes */

  background-color: #faced5; /* Rosa pastel suave */
  background-color: #e6e0f8; /* Lavanda pastel */
  background-color: #dceefc; /* Celeste muy claro */
  background-color: #f6a5b0; /* Rosa coral (botón o detalles) */
  color: #4a4a4a; /* Gris oscuro o casi negro para el texto */

  /* Paleta 3: Tonos variados */
  background-color: #A2D2FF;
  background-color: #B5EAD7;
  background-color: #CDB4DB;
  background-color: #FFC8DD;
  background-color: #FFF1A6;
```