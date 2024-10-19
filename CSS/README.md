# CSS
CSS (Cascading Style Sheets) es un lenguaje para controlar el aspecto o presentación de los elementos HTML. Es un archivo de texto con extensión `.css` y se pueden crear tantos como sean necesarios y cada página HTML puede enlazar tantos archivos CSS como necesite. [Lista completa de referencias](https://www.w3schools.com/cssref/index.php)

## Estructura básica
![Imagen de la estructura básica](./Fotos/Captura%20de%20pantalla_19-10-2024_103023_labsistemas.frba.utn.edu.ar.jpeg)
La estructura básica del código CSS está compuesta por:
- Regla: Cada uno de los estilos que componen una hoja de estilos CSS. Comienza con un selector y entre llaves, una declaración.
- Selector: Indica el elemento o los elementos a los que se aplica la regla CSS. **"A quién hay que hacérselo"**.
- Declaración: Especifica los estilos que se aplican, es decir la/s propiedades. **"Qué hay que hacer"**.
- Propiedad: La característica que se modifica.
- Valor: El nuevo valor que toma esa característica.

## Trabajar en forma "INLINE"
Básicamente consiste en poner el código CSS dentro del código HTML usando el atributo `style` o la etiqueta `<style>` (la diferencia es que al usar la etiqueta estamos colocando código en CSS) además de ser el código con mayor prioridad. Entre cada declaración se coloca un ; para separarlas. Por ejemplo:
```HTML
<h1 style="color: blue;">Este es un Título azul</h1> <!-- Se podría haber usado:"color:rgb(0,0,255);" (rojo, verde, azul)-->
<h2 style="color: red; background-color: rgba(255,255,255,0.5);">Subtítulo</h2>
<!--En este caso el 4 componente (0.5) indica la opacidad del color y va desde 0 a 1-->
```
```HTML
<style>
    body {
        font-family: Arial, sans-serif;
    }
    h1 {
        color: blue;
    }
    h2 {
        color: red;
        background-color: rgba(255, 255, 255, 0.5);
    }
</style>
```

## Enlazar archivos CSS a página HTML
Se coloca en el head (no es necesario que este ahi, pero semanticamente debería estar ahi) la siguiente etiqueta:
```HTML
<link rel="stylesheet" type="text/css" href="path-archivo"/>
```
- rel: Indica el tipo de relación, que en este caso siempre es `"stylesheet"`
- type: Indica el tipo de recurso, que para CSS siempre es `"text/css"`
- href: La URL del archivo

## Selectores
Hay tres tipos de selectores (ordenados por especifidad):
- Selector por ID: Selecciona un elemento con el ID dado (debería ser solo uno) y se usa un `#`. `#ID{código}`
- Selector por Clase: Selecciona los elementos de una clase y se usa un `.`. `.clase1.clase2.clase3{código}`
- Selector por etiqueta: Selecciona una etiqueta como por ejemplo `h1`. `etiqueta{código}`
- Selector universal: Slecciona todos los elementos y se usa un `*`. `*{código}`.
Se pueden **combinar** es decir que puedo aplicar lo mismo a diversas etiquetas, clases o ID. Ejemplo: 
```css
h1, p, #pepe, .caja {
    color: red;
}
```
En este caso esto diciendo que `h1`, `p`, `#pepe`, `.caja` son de color rojo.

### Algunas combinaciones de selectores
Se pueden combinar los selectores, algunos ejemplos:
- Selectores descendentes: Selecciona aquellos hijos de otra etiqueta/clase/ID (no necesariamente tienen que ser hijos directos). Ejemplo: `article h3 {}` estaria seleccionando a los `h3` que sean hijos de un `article`. Otro ejemplo: `.cuadrado p {}` estoy seleccionando a los `p` hijos de la clase `cuadrado`.
- Selectores por hijos: Es lo mismo que el descendente pero en este caso solo aplica a los hijos directos y **se agrega** un `>`. Ejemplo: `section > p {}`
- Selectores adyacentes: En este caso estamos seleccionando elementos que esten pegados a otro elemento y **se agrega** un `+`. Siempre se selecciona el elemento de la derecha. Ejemplo: `h3 + p {}` estoy seleccionando todos los `p` que esten al lado de un `h3`.
- Selector por atributos: Puedo seleccionar elementos que tengan un atributo específico y **se usa** `[]`. Ejemplo: `[href] {}`, en este caso estoy sleccionando a todos los elementos que tengan el atributo `href`.
  - Puedo seleccionar aquellos con un valor en específico `[attr=valor]`. Ejemplo: `[href = "pepe.com"] {}`
  - Puedo seleccionar aquellos que empiecen con un valor `[attr^=valor]`. Ejemplo: `[href ^= "pepe"] {}`
  - Puedo seleccionar aquellos que terminen con un valor `[attr$=valor]`. Ejemplo: `[href $= ".com"] {}`

### Pseudo clases
Son varias pero sirven para ser mas específico al momento de seleccionar un elemento y se usa `:`. [Lista completa](https://developer.mozilla.org/es/docs/Web/CSS/Pseudo-classes). Ejemplo:
```css
ul > li:first-child{color: red;}
```
Lo que estoy seleccionando en este caso es el primer item de una lista desordenada. Si colacara `ul:first-child` esto solo se aplicaria a la primer lista desordenada que encuentre. Otro ejemplo:
```css
ul > li:nth-child(2n) {color: white;}
```
En este caso estoy pintando de blanco todos los elementos pares.
La pseudo clase que **mas vamos a usar** es `hover` que sirve para cuando pasamos por arriba con el mouse de ese elemento. Ejemplo:
```css
div.opcion-servicio.fondo-blanco:hover {
    color: rgba(179, 179, 179)
}
```
En este caso lo que estoy haciendo es que cuando a un `div` con las clases `opcion-servicio` y `fondo-blanco` le pase por arriba con el mouse el color pase a ser gris.

## Prioridades
En caso de que tengamos distintas reglas para un mismo elemento, CSS tiene una prioridad basada en dos conceptos:
- Especifidad: Cuanto más específica sea una regla mayor prioridad tiene. Ejemplo: Es más prioritario el selector por ID que el universal.
- Cascada: Cuanto más abajo este el código mas importancia va a tener. Aplica tanto para el propio código en el archivo CSS como en el orden en el que linkeamos los archivos CSS en código HTML.

## Herencia
ALgunas propiedades se pueden heradad como la fuente o el tamaño de letra. Ejemplo:
```HTML
<div class="text-container">
    <span>Un texto</span>
    <span>Otro texto</span>
    <a>Un link</a>
</div>
```
```css
.text-conteiner{
    font-size: 48px;
}
```
En este ejemplo todas las etiquetas `<span>` y la etiqueta `<a>` heredan el tamaño de letra del `<div>`