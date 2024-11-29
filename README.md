# Curso-desarrollo-web-Full-Stack
... y algunos conceptos importantes:

## Modelo de capas MVC
Es una propuesta de arquitectura de software utilizada para separar el código por sus distintas responsabilidades, manteniendo capas muy distintas que se encargan de una tarea muy concreta. En este caso las tres capas del modelo MVC son: Modelos, Vistas y Controladores.

Ventajas:
- Buena separación de intereses (concerns)
- Reusabilidad de vistas y controladores
- Flexibilidad

Desventajas
- Mayor complejidad
- Demasiado trabajo para apps con Vistas “Simples”
- Más difícil de Testear

<div style="display: flex; align-content: center; justify-content:center;">
    <img src="./Fotos/MVC.jpeg">
    <img src="./Fotos/MVC Funcionamiento.jpeg">
</div>


## Bootstrap
Es un framework de CSS, que nos da herramientas para que creemos página web siguiendo la estrategia mobile first. [Página de Bootstrap](https://getbootstrap.com/), tiene distintas plantillas para poder utilizar. **Básicamente distribuye la página en 12 rejillas** las cuales muestran el contenido de forma flexible.

En general lo que se suele hacer es copiar y pegar el código de estas plantillas, seria la ""mala manera de hacerlo"". Lo que debería hacerse es utilizar las herramientas (que suelen ser clases) y crear mi propio contenido. Para poder utilizarlo hay que vincular en nuestro HTML el archivo CSS y el de Javascript. Hay que tener cuidado ya que al inlcluir el css, puede provocar cambios en nuestra página ya que agrega estilos por defecto.

<img style="display: flex; align-items: center;" src="./Fotos/Bootstrap.jpeg">

### Laravel
“Laravel es un framework de aplicación web con una sintaxis elegante y expresiva. Un framework web proporciona una estructura y un punto de partida para crear su aplicación, lo que le permite concentrarse en crear algo sorprendente mientras nosotros nos preocupamos por los detalles” [Laravel Docs - Web - 2021]
Básicamente nos va a dar la estructura sobre la cual vamos a trabajar.

### Composer
“Composer es una herramienta para la gestión de dependencias en PHP. Le permite declarar las bibliotecas de las que depende su proyecto y las administrará (instalará / actualizará) por usted” [Composer Docs - Web - 2021]