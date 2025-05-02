# Scroll-driven animation

El módulo de Scroll-driven Animations de CSS es uno de los avances más emocionantes en animaciones modernas: permite que los elementos se animen directamente al hacer scroll, sin usar JavaScript.

## ¿Qué es el módulo de Scroll-driven Animations?

Es una especificación de CSS que introduce nuevas herramientas para vincular animaciones al desplazamiento (`scroll`) del usuario.

Te permite animar elementos de forma fluida en función de:

- Cuánto se ha scrolleado un elemento o la página.
- Si un elemento entra o sale del viewport.
- El progreso visual de un elemento al desplazarse.

### Componentes clave del módulo

1. scroll-timeline
2. animation-timeline
3. animation-range
4. view-timeline (experimental)

---

## ¿Qué es scroll-timeline?

Define una línea de tiempo basada en el scroll.

```css
.mi-contenedor {
  scroll-timeline: nombre-del-timeline vertical;
}
```

## ¿Qué es animation-timeline?

animation-timeline permite vincular una animación a un "timeline" personalizado, en lugar de usar el timeline tradicional basado en el tiempo.

**Los valores más comunes:**

- `scroll()` o `scroll`(`<elemento>`): Usa el desplazamiento de un elemento como línea de tiempo.

- `scroll(root)`: Usa el scroll del documento (`<html>` o `<body>`).

- `view()`: Usa el progreso del elemento dentro del viewport (como intersection observer, pero en CSS).

```css
.mi-elemento {
  animation: miAnimacion linear;
  /* O usar scroll(root) para el scroll global. */
  animation-timeline: scroll(nombre-del-timeline); 
}
```

## ¿Qué es animation-range?

Define en qué punto del scroll debe empezar y terminar la animación. Se especifica como un rango de progreso del scroll.

Sintaxis: 

- `animation-range`: `<start>` `<end>`;

**Ejemplos de valores:**

- `0 300px` → empieza la animación cuando has hecho 0px de scroll, y la termina a los 300px.

- `entry 0% entry 100% ` → animación desde que el elemento entra al viewport hasta que está completamente dentro.


**Ejemplo completo:**

```css
@keyframes aparecer {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.boton {
  animation: aparecer linear; /* nombre de la animción / tipo de animación */
  animation-timeline: scroll(root);
  animation-range: 0 300px;
  animation-fill-mode: both;
}
```

#### Explicación:

- `animation-timeline: scroll(root)`: La animación avanza conforme haces scroll vertical en la página.

- `animation-range: 0 300px`: La animación empieza cuando el scroll está en 0px y termina a los 300px.

- `animation-fill-mode`: `both` -> Aplica los estilos del inicio y fin según corresponda.


#### Otros ejemplos de timeline personalizados

Puedes crear un timeline de scroll para un contenedor específico:

```css
.mi-contenedor {
  scroll-timeline: scroll-contenido y;
}

.objeto {
  animation-timeline: scroll-contenido;
  animation-range: entry 0% entry 100%;
}
```

`scroll-timeline`: scroll-contenido y; crea un timeline basado en el eje Y del scroll del contenedor.

`entry 0% entry 100%`: usa la posición del elemento dentro del viewport como referencia.


### Conclusión

- `animation-timeline` te da control total sobre cuándo y cómo una animación ocurre basada en el scroll.

- `animation-range` te permite definir el inicio y fin de esa animación dentro del progreso del scroll.

- Son ideales para efectos modernos y fluidos sin JS.

---

## La propiead `backdrop-filter: blur(5px);`

La propiedad `backdrop-filter: blur(5px);` en CSS se usa para aplicar **efectos gráficos** (como desenfoque o cambio de color) a **lo que está detrás de un elemento**, es decir, a su "fondo", pero no al fondo del propio elemento, sino a lo que está *visual y físicamente detrás* de él en la página.

### ¿Qué hace específicamente `blur(5px)`?

`blur(5px)` aplica un **desenfoque gaussiano** de 5 píxeles al fondo detrás del elemento. Es como mirar a través de un vidrio esmerilado: se ve el contenido detrás, pero difuminado.

### ¿Dónde se puede usar?

Para que `backdrop-filter` funcione correctamente:

1. **El elemento debe tener algún nivel de transparencia**, ya sea con `background-color: rgba(...)`, `background: transparent` o `opacity`.
2. Suele usarse en:
   - **Modales (ventanas emergentes)**.
   - **Barras de navegación flotantes**.
   - **Tarjetas con diseño tipo "glassmorphism"** (vidrio esmerilado moderno).
   - Fondos de menús o diálogos que quieren resaltar el primer plano y desenfocar el fondo.


### Ejemplo práctico:

```css
.card {
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(5px);
  padding: 20px;
  border-radius: 10px;
}
```

```html
<div class="card">
  Esto se ve sobre un fondo difuminado.
</div>
```

### Consideraciones:

- **Compatibilidad**: Funciona en la mayoría de los navegadores modernos, pero no en todos. En algunos casos puede necesitar prefijo:
  ```css
  -webkit-backdrop-filter: blur(5px);
  ```
- **Rendimiento**: Puede afectar la performance en dispositivos más lentos, especialmente si se usa mucho.

