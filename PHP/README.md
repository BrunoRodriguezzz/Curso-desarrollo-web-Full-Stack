# PHP
Es un lenguaje de programación que se interpreta del lado del servidor, utilizado mas que nada para el desarrollo web.

Para empezar un proyecto creamos una carpeta en `htdoc` dentro de la carpeta de `xampp`.

### ¿Qué es PHP?
PHP (Hypertext Preprocessor) es un lenguaje de programación del lado del servidor, ampliamente utilizado para el desarrollo web. PHP se integra con HTML y es capaz de interactuar con bases de datos, manejar sesiones, y realizar muchas otras tareas del lado del servidor.

### ¿Cómo funciona PHP?
1. **Servidor Web**: PHP se ejecuta en un servidor web (como Apache o Nginx).
2. **Interpretación**: El código PHP es interpretado por el servidor y el resultado es enviado al navegador del cliente como HTML.
3. **Interacción con Bases de Datos**: PHP puede interactuar con bases de datos como MySQL para almacenar y recuperar datos.

### Sintaxis Básica de PHP
- **Etiquetas PHP**: El código PHP se escribe entre `<?php` y `?>`.
- **Variables**: Las variables en PHP comienzan con el símbolo `$`.
- **Estructuras de Control**: PHP soporta estructuras de control como `if`, `else`, `while`, `for`, etc.
- **Funciones**: PHP tiene una amplia gama de funciones integradas y también permite la creación de funciones personalizadas.

### Principales Funciones a Conocer
- **echo**: Imprime texto en la salida.
- **print**: Similar a `echo`, pero con una ligera diferencia en el comportamiento.
- **isset()**: Verifica si una variable está definida y no es `null`.
- **empty()**: Verifica si una variable está vacía.
- **include()** y **require()**: Incluyen y evalúan un archivo.
- **mysqli_connect()**: Conecta a una base de datos MySQL.
- **mysqli_query()**: Realiza una consulta a la base de datos.

### Ejemplo Útil
A continuación, un ejemplo básico de un script PHP que conecta a una base de datos MySQL y recupera datos:

```php
<?php
// Conexión a la base de datos
$servername = "localhost";
$username = "root";
$password = "";
$dbname = "mi_base_de_datos";

// Crear conexión
$conn = new mysqli($servername, $username, $password, $dbname);

// Verificar conexión
if ($conn->connect_error) {
    die("Conexión fallida: " . $conn->connect_error);
}

// Consulta SQL
$sql = "SELECT id, nombre, email FROM usuarios";
$result = $conn->query($sql);

if ($result->num_rows > 0) {
    // Salida de datos de cada fila
    while($row = $result->fetch_assoc()) {
        echo "id: " . $row["id"]. " - Nombre: " . $row["nombre"]. " - Email: " . $row["email"]. "<br>";
    }
} else {
    echo "0 resultados";
}
$conn->close();
?>
```
Explicación del Ejemplo
- **Conexión a la Base de Datos**: Se establecen los parámetros de conexión y se crea una instancia de `mysqli`.
- **Verificación de Conexión**: Se verifica si la conexión fue exitosa.
- **Consulta SQL**: Se realiza una consulta para seleccionar datos de la tabla `usuarios`.
- **Procesamiento de Resultados**: Se recorren los resultados y se imprimen en pantalla.
- **Cierre de Conexión**: Se cierra la conexión a la base de datos.

## MVC
Muy en resumen consiste en separar el código en funciones y responsabilidad formando "capas" que son **Modelo-Vista-Controlador**.

