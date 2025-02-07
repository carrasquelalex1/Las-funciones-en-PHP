# Las-funciones-en-PHP
Definición, cómo llamarlas, el uso de parámetros y el alcance de las variables
Esta es una guía para comprender las funciones en PHP, desde su definición hasta su uso avanzado, incluyendo parámetros, valores de retorno, y alcance de variables.

## Contenido

*   [¿Qué es una Función?](#qué-es-una-función)
*   [Definición de una Función](#definición-de-una-función)
*   [Llamada a una Función](#llamada-a-una-función)
*   [Parámetros de una Función](#parámetros-de-una-función)
    *   [Parámetros Requeridos](#parámetros-requeridos)
    *   [Parámetros Opcionales](#parámetros-opcionales)
    *   [Múltiples Parámetros](#múltiples-parámetros)
*   [Valores de Retorno](#valores-de-retorno)
*   [Alcance de las Variables](#alcance-de-las-variables)
    *   [Variables Locales](#variables-locales)
    *   [Variables Globales](#variables-globales)
*   [Ejemplo Completo](#ejemplo-completo)
*   [Ejemplos de Código](#ejemplos-de-código)
*   [Licencia](#licencia)

## ¿Qué es una Función?

Una función es un bloque de código reutilizable que realiza una tarea específica. Imagina que tienes una receta para hacer un pastel. La receta es como una función: tiene una serie de pasos que, cuando se siguen, dan como resultado un pastel. En programación, las funciones nos ayudan a organizar el código, evitar la repetición y hacerlo más fácil de leer y mantener.

## Definición de una Función

En PHP, definimos una función usando la palabra clave `function`, seguida del nombre de la función, paréntesis `()` para los parámetros (si los hay) y llaves `{}` para el bloque de código que contiene la función.


function saludar($nombre) {
  echo "¡Hola, " . $nombre . "!";
}

function: Palabra clave que indica que estamos definiendo una función.

saludar: El nombre de la función. Debe ser descriptivo y seguir las convenciones de nomenclatura de PHP (generalmente snake_case).

($nombre): La lista de parámetros que la función acepta. En este caso, la función saludar espera un parámetro llamado $nombre. Los parámetros son como variables que recibimos cuando llamamos a la función.

{ ... }: El cuerpo de la función. Aquí va el código que se ejecutará cuando llamemos a la función.

## Llamada a una Función

Para ejecutar el código dentro de una función, necesitamos llamarla. Esto se hace escribiendo el nombre de la función seguido de paréntesis () y, si la función requiere parámetros, pasando los valores correspondientes entre los paréntesis.

## Parámetros de una Función

Como vimos en el ejemplo anterior, las funciones pueden aceptar parámetros. Los parámetros son como variables que le damos a la función para que pueda trabajar con ellas.

## Parámetros Requeridos

Son los parámetros que la función debe recibir para funcionar correctamente. Si no se proporcionan al llamar a la función, PHP generalmente generará un error.

## Parámetros Opcionales

Podemos hacer que un parámetro sea opcional asignándole un valor por defecto en la definición de la función. Si no se proporciona un valor al llamar a la función, se usará el valor por defecto.

function saludar($nombre, $saludo = "Hola") {
  echo $saludo . ", " . $nombre . "!";
}

saludar("Alexander"); // Mostrará "Hola, Alexander!" (usa el valor por defecto para $saludo)
saludar("Gabriela", "Buenos días"); // Mostrará "Buenos días, Ana!"

## Múltiples Parámetros
Las funciones pueden aceptar varios parámetros. Simplemente sepáralos por comas en la definición de la función y al llamarla.

function sumar($a, $b) {
  return $a + $b;
}

$resultado = sumar(5, 6); // $resultado valdrá 11

## Valores de Retorno
Las funciones también pueden retornar un valor. Esto significa que la función puede calcular algo y devolver el resultado para que se use en otra parte del código. Usamos la palabra clave return para especificar el valor que la función debe retornar.

function multiplicar($a, $b) {
  return $a * $b;
}

$producto = multiplicar(5, 6); // $producto valdrá 30
echo $producto; // Mostrará 30

Si una función no tiene una declaración return, retornará NULL por defecto.

## Alcance de las Variables
El "alcance" de una variable se refiere a las partes del código donde esa variable es accesible (donde se puede usar). En PHP, hay principalmente dos tipos de alcance:

### Variables Locales
Una variable definida dentro de una función es una variable local. Solo se puede acceder a ella dentro de esa función. No se puede acceder a ella desde fuera de la función.

function miFuncion() {
  $variableLocal = "Soy local";
  echo $variableLocal; // Esto funciona
}

miFuncion(); // Mostrará "Soy local"

// echo $variableLocal; // Esto causaría un error porque $variableLocal no está definida fuera de la función

### Variables Globales
Una variable definida fuera de cualquier función es una variable global. Por defecto, no se puede acceder a una variable global directamente dentro de una función. Para usar una variable global dentro de una función, debes declararla como global dentro de la función.

$variableGlobal = "Soy global";

function otraFuncion() {
  global $variableGlobal; // Declara que vamos a usar la variable global $variableGlobal
  echo $variableGlobal; // Esto funciona
}

otraFuncion(); // Mostrará "Soy global"

Importante sobre global: El uso excesivo de variables globales puede hacer que el código sea más difícil de entender y mantener. Generalmente, es mejor pasar datos a las funciones como parámetros y retornarlos como valores si es necesario, en lugar de depender demasiado de las variables globales.


## Ejemplo Completo
Aquí tienes un ejemplo que combina varios de los conceptos que hemos cubierto:


## <?php
// Función para calcular el ahorro de Alexander al cabo de 30 días cada día ahorra 5 monedas
function calcularAhorro($unidades, $dias) {
$ahorro = $unidades * $dias;
return $ahorro;
}

// Variable global (evita usarla directamente dentro de la función si puedes)
$unidad = "monedas";

// Función que usa la función calcularAhorro y una variable global (con precaución)
function mostrarAhorro($unidades, $dias) {
global $unidad;
$ahorroCalculado = calcularAhorro($unidades, $dias);
echo "El ahorro luego de 30 días es: " . $ahorroCalculado . " " . $unidad . "<br>";
}

// Llamamos a las funciones
mostrarAhorro(5, 30); // Mostrará "El ahorro luego de 30 días es: 150 monedas"
$otroAhorro = calcularAhorro(5, 20);
echo "El ahorro para 20 días es: " . $otroAhorro . "<br>"; // Mostrará "El ahorro para 20 días es: 100"
## ?>



## Licencia
Este proyecto está licenciado bajo la MIT License.

Copyright (c) 2025 AlexanderJosé Carrasquel Burgos
