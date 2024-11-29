# PHP
Es un lenguaje de programación que se interpreta del lado del servidor, utilizado mas que nada para el desarrollo web. [Información sobre MySQLi](https://www.php.net/manual/es/book.mysqli.php)

Para empezar un proyecto creamos una carpeta en `htdoc` dentro de la carpeta de `xampp`.

- [PHP](#php)
    - [¿Qué es PHP?](#qué-es-php)
    - [¿Cómo funciona PHP?](#cómo-funciona-php)
    - [Sintaxis Básica de PHP](#sintaxis-básica-de-php)
    - [Principales Funciones a Conocer](#principales-funciones-a-conocer)
  - [MySQLi](#mysqli)
    - [Conexión](#conexión)
  - [empty() vs isset()](#empty-vs-isset)
    - [Cuándo usar cada una](#cuándo-usar-cada-una)
    - [Ejemplo Útil](#ejemplo-útil)
  - [MVC](#mvc)

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
- **echo**: Es un contructor de lenguaje, que **inyecta** código que sabe interpretar el navegador.
- **isset()**: Verifica si una variable está definida y no es `null`.
- **empty()**: Verifica si una variable está vacía.
- **include()** y **require()**: Incluyen y evalúan un archivo.
- **mysqli_connect()**: Conecta a una base de datos MySQL.
- **mysqli_query()**: Realiza una consulta a la base de datos.
- **foreach**: Sirve para iterar un array. La variable `$array` tiene que ser el array pero el resto sirven solo dentro del `foreach`.
```php
foreach($array as $elementoDelArray){
  //Hago algo con cada elemento del array.
}

foreach($array as $clave => $elementoDelArray){
  //Es lo mismo que antes solo que ahora cuento también con la clave de ese elemento.
}
```

## MySQLi
Es una extensión incorporada a PHP que nos permitira trabajar con nuestra base de datos.

### Conexión
Para empezar deberiamos establecer una conexión con la base de datos.
```php
mysqli_connect("host", "user", "password", "dataBaseName");
```
- `"host"`: Esta variable representa el nombre del servidor donde se encuentra la base de datos. Puede ser una dirección IP (por ejemplo, `127.0.0.1` para localhost) o un nombre de dominio (por ejemplo, `mi-servidor.com`).

- `"user"`: Esta variable es el nombre de usuario que se utiliza para conectarse a la base de datos. Este usuario debe tener los permisos necesarios para acceder y manipular la base de datos especificada.

- `"password"`: Esta variable es la contraseña correspondiente al usuario que se está utilizando para la conexión. Es importante mantener esta información segura y no compartirla públicamente.

- `"dataBaseName"`: Esta variable es el nombre de la base de datos a la que se desea conectar. Debe ser una base de datos existente en el servidor especificado.

Podemos usar `mysqli_connect_error()` para comprobar si la conexión fue exitosa.

## empty() vs isset()
Las funciones `isset()` y `empty()` en PHP se utilizan para verificar el estado de una variable, pero tienen propósitos diferentes:

**isset()**
- Propósito: Determina si una variable está definida y no es `null`.
- Uso: Se utiliza para verificar si una variable ha sido declarada y tiene un valor que no sea `null`.

Ejemplo:
```php
<?php
$var = "Hola";
if (isset($var)) {
    echo "La variable está definida y no es null.";
}
```

**empty()**
- Propósito: Determina si una variable está vacía.
- Uso: Se utiliza para verificar si una variable es considerada vacía. Una variable se considera vacía si no está definida, es `null`, es una cadena vacía (`""`), es `0`, es `0.0`, es una cadena `"0"`, es un array vacío, o es false.
  
Ejemplo:
```php
<?php
$var = "";
if (empty($var)) {
    echo "La variable está vacía.";
}
```
### Cuándo usar cada una
Usa `isset()` cuando necesitas verificar si una variable ha sido declarada y tiene un valor que no sea `null`.
Usa `empty()` cuando necesitas verificar si una variable está vacía según la definición de PHP (no definida, `null`, cadena vacía, `0`, `0.0`, cadena `"0"`, array vacío, o false).

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

