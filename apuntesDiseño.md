# Apuntes de Diseño Web Ibrahim- CSS


## 1. CSS Grid Layout

El sistema de Grid es bidimensional, permitiendo controlar tanto filas como columnas.

### Contenedor (Padre)
*   **`display: grid;`**: Define el contenedor como una cuadrícula.
*   **`grid-template-columns`**: Define el número y ancho de las columnas.
    *   `repeat(3, 1fr)`: Crea 3 columnas de igual tamaño (1 fracción del espacio disponible cada una).
    *   `1fr 1fr 1fr 1fr`: 4 columnas iguales.
    *   `repeat(4, 200px)`: 4 columnas de 200px cada una.
*   **`grid-template-rows`**: Define el número y altura de las filas.
    *   `repeat(7, 1fr)`: 7 filas de igual altura.
*   **`grid-template-areas`**: Permite nombrar áreas de la cuadrícula para posicionar elementos fácilmente.
    ```css
    grid-template-areas:
        "header header header"
        "sidebar content content"
        "footer footer footer";
    ```
*   **`gap`**: Espacio entre celdas. Puede ser un solo valor (para filas y columnas) o dos (`fila columna`).
    *   `gap: 16px;`
    *   `gap: 3px 5px;` 

### Elementos (Hijos)
*   **`grid-area`**: Asigna un elemento a un área nombrada en `grid-template-areas`.
    *   `grid-area: casa1;`

## 2. Flexbox (Flexible Box Layout)

Sistema unidimensional para distribuir espacio y alinear contenido.

### Contenedor (Padre)
*   **`display: flex;`**: Activa Flexbox.
*   **`flex-direction`**: Dirección de los elementos.
    *   `row` (por defecto): Fila horizontal.
    *   `column`: Columna vertical.
*   **`flex-wrap`**: Controla si los elementos saltan a la siguiente línea si no caben.
    *   `wrap`: Saltan de línea.
    *   `nowrap` (por defecto): Se ajustan en una sola línea.
*   **`flex-flow`**: Atajo para `flex-direction` y `flex-wrap`.
    *   `flex-flow: row wrap;`
*   **`justify-content`**: Alineación en el eje principal (horizontal si es `row`).
    *   `space-between`: Distribuye el espacio entre los elementos (primero al inicio, último al final).
    *   `space-around`: Espacio igual alrededor de cada elemento.
    *   `center`: Centra los elementos.
*   **`align-items`**: Alineación en el eje transversal (vertical si es `row`).
    *   `center`: Centra verticalmente.
    *   `flex-start`: Alinea arriba.
    *   `flex-end`: Alinea abajo.

### Elementos (Hijos)
*   **`flex`**: Atajo para `flex-grow`, `flex-shrink` y `flex-basis`.
    *   `flex: 1;`: El elemento crecerá para ocupar el espacio disponible.
*   **`flex-grow`**: Factor de crecimiento. Si es 1, crece para llenar espacio.
*   **`flex-shrink`**: Factor de encogimiento.
*   **`flex-basis`**: Tamaño inicial del elemento antes de distribuir espacio.
*   **`align-self`**: Alineación individual de un elemento (sobreescribe `align-items`).
    *   `align-self: center;`
*   **`order`**: Cambia el orden visual de los elementos.
    *   `order: 1;`, `order: -1;`

## 3. Transiciones y Transformaciones

Para dar dinamismo e interactividad.

### Transiciones (`transition`)
Suavizan el cambio de propiedades CSS.
*   **Sintaxis**: `transition: propiedad duración función-tiempo;`
    *   `transition: background-color 1s linear;`
    *   `transition: transform 1s;`
    *   `transition: all 0.5s ease-in-out;`
*   **Funciones de tiempo**: `linear`, `ease`, `ease-in` (lento al inicio), `ease-out` (lento al final), `ease-in-out`.

### Transformaciones (`transform`)
Modifican la forma, tamaño o posición.
*   **`rotate(Xdeg)`**: Rota el elemento X grados.
    *   `transform: rotateY(180deg);`
*   **`rotateX(Xdeg)`**: Rota en el eje X (efecto 3D).
*   **`translate(x, y)`**: Mueve el elemento.
    *   `translate(150%, 100%)`
*   **`scale(n)`**: Escala el elemento (1 es tamaño original, 1.5 es 50% más grande).
*   **`skew(Xdeg)`**: Sesga o inclina el elemento.
*   **Combinación**: Se pueden combinar varias transformaciones.
    *   `transform: translate(...) scale(...) skew(...);`
    *   `transform-style: preserve-3d`
    *    `backface-visibility: hidden`

## 4. Propiedades Generales y Útiles

### Modelo de Caja y Posicionamiento
*   **`box-sizing: border-box;`**: Fundamental. Hace que el `padding` y `border` se incluyan en el ancho/alto total, evitando cálculos complejos.
*   **`margin: 0 auto;`**: Centra un bloque horizontalmente (requiere ancho definido).
*   **`position`**:
    *   `relative`: Posición normal, pero permite usar `top`, `left`, `z-index` y sirve de referencia para hijos absolutos.
    *   `absolute`: Se posiciona respecto al padre posicionado más cercano (o el body). Se saca del flujo normal.
    *   `fixed`: Se fija a la ventana del navegador (no se mueve al hacer scroll).
*   **`display`**:
    *   `block`: Ocupa todo el ancho.
    *   `inline`: Ocupa solo lo necesario, no acepta ancho/alto.
    *   `inline-block`: Como inline pero acepta ancho/alto.
    *   `none`: Oculta el elemento.
*   **`z-index`**: Controla el apilamiento (qué elemento está encima de otro). Requiere `position` (no static).

### Imágenes y Multimedia
*   **`object-fit: cover;`**: Hace que la imagen cubra todo el contenedor sin deformarse (recorta si es necesario). Muy útil en Grids y tarjetas.
*   **`background-image`**:
    *   `url(...)`: Imagen de fondo.
    *   `linear-gradient(...)`: Degradados de color.
*   **`background-size: cover;`**: El fondo cubre todo el elemento.
*   **`background-position: center;`**: Centra la imagen de fondo.

### Texto y Fuentes
*   **`font-family`**: Define la tipografía.
*   **`text-decoration: none;`**: Quita el subrayado a los enlaces.
*   **`text-align: center;`**: Centra el texto.
*   **`line-height`**: Altura de línea. Si es igual a la altura del contenedor, centra el texto verticalmente (truco antiguo, mejor usar Flexbox).

### Efectos Visuales
*   **`clip-path`**: Recorta el elemento con formas.
    *   `polygon(...)`, `circle(...)`, `ellipse(...)`.
*   **`box-shadow`**: Sombra de caja.
*   **`opacity`**: Transparencia (0 a 1).
*   **Pseudo-elementos `::after` / `::before`**: Para crear elementos decorativos (como líneas subrayadas) sin añadir HTML extra. Requieren `content: "";`.
*   **Pseudo-clase `:hover`**: Estilos que se aplican al pasar el ratón por encima.

### Responsive Design (@media)
*   Permite cambiar estilos según el tamaño de la pantalla.
    ```css
    @media screen and (max-width: 500px) {
        .proyectos {
            grid-template-columns: 1fr; /* Cambia a 1 columna en móviles */
        }
    }
    ```

## 5. Animaciones y Efectos Avanzados

### Animaciones (@keyframes)
Permiten crear animaciones complejas definiendo estados intermedios.
*   **`@keyframes nombre`**: Define la secuencia de la animación.
    ```css
    @keyframes mover {
        0% { transform: translateX(0); }
        50% { transform: translateX(100px); }
        100% { transform: translateX(0); }
    }
    ```
*   **`animation`**: Aplica la animación definida.
    *   **Sintaxis**: `animation: nombre duración función-tiempo retardo iteraciones dirección estado-final;`
    *   `animation: mover 2s infinite;`

### Efectos Webkit 
*   **`-webkit-box-reflect`**: Crea un reflejo del elemento (como un espejo).
    *   `below`: Reflejo abajo.
    *   `right`: Reflejo a la derecha.
    *   `offset`: Separación entre elemento y reflejo (ej: `10px`).
    *   `mask`: Máscara para desvanecer (ej: `linear-gradient(...)`).
    *   Ejemplo: `-webkit-box-reflect: below 0px linear-gradient(to bottom, transparent, rgba(255,255,255,0.5));`
    *    background: linear-gradient(to right, colores);
        `-webkit-background-clip: text;`
        `background-clip: text;`
        `color: transparent;`

