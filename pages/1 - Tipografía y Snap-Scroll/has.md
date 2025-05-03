# :has( )

`:has()` es uno de los pseudo-selectores más poderosos de CSS, porque nos permite seleccionar un elemento padre si contiene un hijo específico, lo cual no era posible en CSS puro hasta ahora.

## ¿Qué es `:has()` en CSS?

Permite seleccionar un elemento que contiene otro elemento específico dentro de él.

Es lo más parecido a "CSS con lógica condicional".
Piensa en esto como: “Selecciona este elemento SI tiene dentro tal cosa”.

Requiere navegadores modernos (ya soportado por Chrome, Safari, Edge, Firefox desde 2023).

### Sintaxis básica

```css
elemento:has(descendiente) {
  /* reglas */
}
```

## Ejemplos de uso desde simples a avanzados

#### 1. Básico: Resaltar tarjetas que contienen imágenes

```css
.card:has(img) {
  border: 2px solid teal;
}
```
**Qué hace:** Agrega borde a .card solo si tiene una imagen dentro.

#### 2. Medio: Estilizar campos requeridos con su label

```css
label:has(input:required) {
  font-weight: bold;
  color: crimson;
}
```

**Qué hace:** Aplica estilo al <label> solo si contiene un <input> requerido.

#### 3. Medio: Mostrar mensaje si hay error en un campo

```css
.form-group:has(.error-message) {
  background-color: #ffe5e5;
  border: 1px solid red;
}
```

**Qué hace:** Estiliza el contenedor .form-group solo si hay un mensaje de error dentro.

#### 4. Avanzado: Estilo condicional basado en checkbox

```css
.card:has(input[type="checkbox"]:checked) {
  background-color: #e0f7fa;
  border-color: #26c6da;
}
```

**Qué hace:** Cambia el fondo de .card solo si contiene un checkbox marcado.

#### 5. Avanzado: Mostrar botón solo si hay texto en textare (form reactivo)

```css
.form:has(textarea:not(:placeholder-shown)) button {
  opacity: 1;
  pointer-events: auto;
}

.form button {
  opacity: 0.5;
  pointer-events: none;
}
```

**Qué hace:** El botón dentro del formulario solo es clickeable cuando el textarea no está vacío (gracias a :not(:placeholder-shown)).

#### 6. Muy Avanzado: Diseño adaptable según contenido

```css
.section:has(> h2 + p) {
  display: grid;
  grid-template-columns: 1fr 2fr;
}
```

**Qué hace:** Aplica un diseño de columnas solo si la sección tiene un h2 seguido de un párrafo.

#### 7. Extra: Estilizar un menú activo desde el contenedor padre

```css
nav:has(a.active) {
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}
```

**Qué hace:** Le da un estilo al <nav> solo si uno de sus enlaces tiene la clase .active.

## Casos de uso útiles de :has()

- Formularios dinámicos (validación visual).
- Composición de componentes (como .card, .modal, .tabs).
- Alternativas CSS a algunos scripts de JavaScript.
- Menús, navegación y layouts condicionales.

---

#### Ejemplo de menú lateral usando `:has()`

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Menú Fullscreen con :has()</title>
  <!-- Incluir Font Awesome para iconos -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">

  <style>
    /* Reset global */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: sans-serif;
      transition: all 0.3s ease;
    }

    .layout {
      position: relative;
    }

    /* Checkbox oculto */
    #toggle-menu {
      display: none;
    }

    /* Botones (abrir/cerrar) en la parte superior derecha */
    .top-buttons {
      position: fixed;
      top: 20px;
      right: 20px;
      z-index: 30;
      display: flex;
      gap: 10px;
      transition: all 0.3s ease;
    }

    .btn {
      background-color: royalblue;
      color: white;
      padding: 12px;
      border-radius: 5px;
      cursor: pointer;
      font-size: 24px;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.3s ease;
    }

    .btn.close {
      background-color: crimson;
    }

    /* Menú fullscreen oculto */
    .side-menu {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      background-color: #222;
      color: white;
      padding: 80px 30px 30px;
      box-sizing: border-box;
      transform: translateX(100%);
      transition: transform 0.4s ease;
      z-index: 20;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }

    /* Mostrar menú cuando está activado */
    .layout:has(#toggle-menu:checked) .side-menu {
      transform: translateX(0);
    }

    /* Deshabilitar scroll en el body cuando el menú está abierto */
    .layout:has(#toggle-menu:checked) body {
      overflow: hidden;
    }

    /* Enlaces del menú */
    .side-menu a {
      color: white;
      text-decoration: none;
      margin: 15px 0;
      font-size: 24px;
      transition: color 0.2s;
    }

    .side-menu a:hover {
      color: lightblue;
    }

    /* Ocultar botón abrir cuando el menú está abierto */
    .layout:has(#toggle-menu:checked) .btn.open {
      display: none;
    }

    /* Ocultar botón cerrar cuando el menú está cerrado */
    .layout:not(:has(#toggle-menu:checked)) .btn.close {
      display: none;
    }

    /* Media Queries para hacerlo responsive */
    @media (max-width: 768px) {
      .side-menu a {
        font-size: 20px;
      }

      .top-buttons {
        top: 10px;
        right: 10px;
      }

      .btn {
        font-size: 18px;
        padding: 10px;
      }
    }

    @media (max-width: 480px) {
      .side-menu {
        padding: 60px 20px 20px;
      }

      .side-menu a {
        font-size: 18px;
      }

      .btn {
        font-size: 14px;
        padding: 8px;
      }
    }

    /* Secciones */
    section {
      padding: 50px;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 36px;
      color: white;
      background-color: #333;
      margin-bottom: 20px;
    }

    #inicio {
      background-color: #4CAF50;
    }

    #acerca {
      background-color: #FF5722;
    }

    #servicios {
      background-color: #2196F3;
    }

    #contacto {
      background-color: #FFC107;
    }

  </style>
</head>
<body>

  <div class="layout">
    <!-- Checkbox controlador -->
    <input type="checkbox" id="toggle-menu">

    <!-- Botones en esquina superior derecha -->
    <div class="top-buttons">
      <!-- Icono para abrir el menú -->
      <label for="toggle-menu" class="btn open">
        <i class="fas fa-bars"></i> <!-- Icono de menú -->
      </label>

      <!-- Icono para cerrar el menú -->
      <label for="toggle-menu" class="btn close">
        <i class="fas fa-times"></i> <!-- Icono de cerrar -->
      </label>
    </div>

    <!-- Menú fullscreen -->
    <nav class="side-menu">
      <a href="#inicio">Inicio</a>
      <a href="#acerca">Acerca de</a>
      <a href="#servicios">Servicios</a>
      <a href="#contacto">Contacto</a>
    </nav>
  </div>

  <!-- Secciones -->
  <section id="inicio">
    <div>Bienvenido a la sección Inicio</div>
  </section>
  
  <section id="acerca">
    <div>Esta es la sección Acerca de</div>
  </section>
  
  <section id="servicios">
    <div>Aquí encontrarás nuestros Servicios</div>
  </section>
  
  <section id="contacto">
    <div>Contáctanos a través de esta sección</div>
  </section>

</body>
</html>
```