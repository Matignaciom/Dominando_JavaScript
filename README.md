### JavaScript Mastery: Desde lo Fundamental hasta lo Avanzado

Este repositorio es una guía completa para aprender JavaScript, comenzando desde los fundamentos más básicos y avanzando hacia técnicas avanzadas. Ya sea que seas un principiante que recién comienza a programar o un desarrollador intermedio que busca perfeccionar sus habilidades, encontrarás lecciones y ejemplos prácticos para ayudarte a dominar JavaScript.

### 1. Variables y Tipos de Datos

JavaScript es un lenguaje de programación dinámico que te permite declarar variables utilizando tres palabras clave: `var`, `let`, y `const`. Estas palabras clave tienen diferentes alcances y usos.

#### `var`:
- `var` se utiliza para declarar variables con ámbito de función o global.
- Las variables declaradas con `var` pueden ser redeclaradas y actualizadas en cualquier lugar del ámbito de la función o el script.
- No siguen el bloque de ámbito, lo que significa que pueden filtrarse fuera de las estructuras condicionales o bucles.

```javascript
var edad = 30;
```

#### `let`:
- `let` se utiliza para declarar variables con ámbito de bloque.
- Las variables declaradas con `let` no pueden ser redeclaradas en el mismo ámbito.
- Siguen el ámbito de bloque y no se filtran fuera de las estructuras condicionales o bucles en los que se definen.

```javascript
let nombre = "Juan";
```

#### `const`:
- `const` se utiliza para declarar variables con ámbito de bloque que no cambian su valor después de la asignación inicial.
- Deben asignarse un valor al declararse y no pueden ser reasignadas.
- Siguen el ámbito de bloque, al igual que `let`.

```javascript
const PI = 3.1416;
```
### 1.1 Scope de variables var, let y const

**Scope de `var`:**
```javascript
function ejemploVar() {
  if (true) {
    var x = 10;
  }
  console.log(x); // x está disponible aquí
}

ejemploVar(); // Imprime 10
console.log(x); // x está disponible fuera de la función
```

En el caso de `var`, la variable `x` declarada dentro del bloque `if` sigue siendo accesible fuera de ese bloque. Esto se debe a que las variables declaradas con `var` tienen un ámbito de función o ámbito global.

**Scope de `let`:**
```javascript
function ejemploLet() {
  if (true) {
    let y = 20;
  }
  console.log(y); // y no está disponible aquí
}

ejemploLet(); // Genera un error: "y is not defined"
```

Con `let`, la variable `y` declarada dentro del bloque `if` tiene un ámbito de bloque, lo que significa que no se puede acceder a ella fuera del bloque. Esto evita fugas de variables no deseadas y es una práctica más segura.

**Scope de `const`:**
```javascript
function ejemploConst() {
  if (true) {
    const z = 30;
  }
  console.log(z); // z no está disponible aquí
}

ejemploConst(); // Genera un error: "z is not defined"
```

El comportamiento de `const` es similar al de `let` en cuanto a ámbito de bloque. La variable `z` declarada dentro del bloque `if` no está disponible fuera de ese bloque.

`var` tiene un ámbito de función o global, `let` y `const` tienen un ámbito de bloque. Usar `let` y `const` es preferible en la mayoría de los casos, ya que ayudan a evitar problemas relacionados con la reasignación no deseada y facilitan la escritura de código más seguro y predecible.

### 2. Operadores

JavaScript admite varios operadores para realizar operaciones matemáticas, comparaciones y más.

```javascript
var numero1 = 10;
var numero2 = 5;

// Operadores aritméticos
var suma = numero1 + numero2; // suma = 15
var resta = numero1 - numero2; // resta = 5
var multiplicacion = numero1 * numero2; // multiplicación = 50
var division = numero1 / numero2; // división = 2
var modulo = numero1 % numero2; // módulo = 0 (resto de la división)

// Operadores de asignación
var resultado = 0;
resultado += numero1; // resultado = 10 (resultado = resultado + numero1)
resultado -= numero2; // resultado = 5 (resultado = resultado - numero2)
resultado *= numero1; // resultado = 50 (resultado = resultado * numero1)
resultado /= numero2; // resultado = 10 (resultado = resultado / numero2)

// Operadores de comparación
var igualdad = numero1 == numero2; // igualdad = false
var desigualdad = numero1 != numero2; // desigualdad = true
var mayorQue = numero1 > numero2; // mayorQue = true
var menorQue = numero1 < numero2; // menorQue = false
var mayorIgual = numero1 >= numero2; // mayorIgual = true
var menorIgual = numero1 <= numero2; // menorIgual = false

// Operadores lógicos
var condicion1 = true;
var condicion2 = false;
var yLogico = condicion1 && condicion2; // yLogico = false (AND lógico)
var oLogico = condicion1 || condicion2; // oLogico = true (OR lógico)
var noLogico = !condicion1; // noLogico = false (NOT lógico)
```

### 3. Condicionales

Puedes utilizar instrucciones condicionales para tomar decisiones en tu código.

```javascript
// Función para determinar si un número es par o impar
function esParOImpar(numero) {
    // Verificar si la entrada no es un número
    if (typeof numero !== 'number') {
        throw new Error('La entrada no es un número.');
    }

    // Comprobar si el número es par o impar
    if (numero % 2 === 0) {
        return 'El número es par.';
    } else {
        return 'El número es impar.';
    }
}

try {
    var entrada = 42;
    // Llamar a la función y capturar posibles errores
    var resultado = esParOImpar(entrada);
    console.log(resultado);
} catch (error) {
    console.error('Ocurrió un error: ' + error.message);
}

// Ejemplo de un switch statement para días de la semana
var diaDeLaSemana = 'lunes';

switch (diaDeLaSemana) {
    case 'lunes':
    case 'martes':
    case 'miércoles':
    case 'jueves':
    case 'viernes':
        console.log('Es un día laborable.');
        break;
    case 'sábado':
    case 'domingo':
        console.log('Es un fin de semana.');
        break;
    default:
        console.log('Día no válido.');
}

// Uso de operador ternario para determinar si un número es positivo o negativo
var numero = -5;
var esPositivo = (numero >= 0) ? 'positivo' : 'negativo';
console.log('El número es ' + esPositivo);
```
Este código muestra cómo se puede verificar si un número es par o impar, tomar decisiones basadas en el día de la semana y cómo utilizar el operador ternario para determinar si un número es positivo o negativo. También incluye manejo de excepciones para tratar errores potenciales.

### 4. Bucles

Los bucles permiten repetir un bloque de código varias veces.

```javascript
// Ejemplo de bucle 'for' para imprimir números del 1 al 5
for (let i = 1; i <= 5; i++) {
    console.log('Número:', i);
}

// Ejemplo de bucle 'while' que imprime números del 1 al 5
let j = 1;
while (j <= 5) {
    console.log('Número (while):', j);
    j++;
}

// Ejemplo de bucle 'do...while' que imprime números del 1 al 5
let k = 1;
do {
    console.log('Número (do...while):', k);
    k++;
} while (k <= 5);

// Crear un array de números
const numeros = [1, 2, 3, 4, 5];

// Iterar a través de un array usando 'for...of'
for (const numero of numeros) {
    console.log('Número del array:', numero);
}

// Crear un objeto con propiedades
const persona = {
    nombre: 'Juan',
    edad: 30,
    ciudad: 'Ejemploville'
};

// Iterar a través de las propiedades de un objeto usando 'for...in'
for (const propiedad in persona) {
    console.log(`Propiedad: ${propiedad}, Valor: ${persona[propiedad]}`);
}

// Ejemplo de control de bucle con 'break' y 'continue'
for (let x = 1; x <= 10; x++) {
    if (x % 2 === 0) {
        continue; // Salta a la próxima iteración si es par
    }
    console.log('Número impar:', x);
    if (x === 7) {
        break; // Sale del bucle cuando llega a 7
    }
}

// Bucle 'for' anidado para crear una matriz bidimensional
const matrizBidimensional = [];
for (let fila = 0; fila < 3; fila++) {
    matrizBidimensional[fila] = [];
    for (let columna = 0; columna < 3; columna++) {
        matrizBidimensional[fila][columna] = fila * 3 + columna + 1;
    }
}
console.log('Matriz bidimensional:', matrizBidimensional);

// Ejemplo de bucle que muestra cómo funciona la optimización de bucles
const start = new Date().getTime();
for (let i = 0; i < 1000000; i++) {
    // Realiza una tarea simple 1,000,000 de veces
}
const end = new Date().getTime();
console.log('Tiempo transcurrido:', end - start, 'milisegundos');

// Bucle asincrónico (simulado con setTimeout)
let contador = 0;
function bucleAsincronico() {
    setTimeout(() => {
        console.log('Iteración asincrónica:', contador);
        contador++;
        if (contador < 5) {
            bucleAsincronico(); // Llamada recursiva para simular iteraciones asincrónicas
        }
    }, 1000);
}

bucleAsincronico();
```
Este ejemplo abarca los conceptos de bucles for, while, do...while, iteración a través de arrays y objetos, control de bucles con break y continue, bucles anidados, optimización de bucles y bucles asincrónicos. Cada parte del código está acompañada de comentarios explicativos para ayudarte a comprender los conceptos de bucles en JavaScript.

### 5. Funciones

Las funciones son bloques de código reutilizables que pueden recibir argumentos y devolver valores.

```javascript
// 1. Declaración de una función con parámetros y valor de retorno
function suma(a, b) {
    return a + b;
}

// 2. Llamada a la función y almacenamiento del resultado
var resultado = suma(2, 3);

// 3. Impresión del resultado en la consola
console.log("Resultado de la suma:", resultado); // Resultado de la suma: 5

// 4. Función sin valor de retorno
function saludar(nombre) {
    console.log("Hola, " + nombre + "!");
}

// 5. Llamada a la función sin valor de retorno
saludar("Juan"); // Imprime "Hola, Juan!"

// 6. Función con parámetros predeterminados (ES6+)
function calcularPrecio(precioBase, descuento = 0) {
    return precioBase - (precioBase * descuento);
}

var precioFinal1 = calcularPrecio(100, 0.1); // Con descuento del 10%
console.log("Precio final con descuento:", precioFinal1); // Precio final con descuento: 90

var precioFinal2 = calcularPrecio(75); // Sin descuento (descuento predeterminado)
console.log("Precio final sin descuento:", precioFinal2); // Precio final sin descuento: 75

// 7. Función anónima y asignación a una variable
var multiplicar = function (x, y) {
    return x * y;
};

var producto = multiplicar(4, 5);
console.log("Producto:", producto); // Producto: 20

// 8. Función flecha (ES6+)
const dividir = (a, b) => a / b;

const cociente = dividir(10, 2);
console.log("Cociente:", cociente); // Cociente: 5

// 9. Función recursiva (llamada a sí misma)
function factorial(n) {
    if (n === 0 || n === 1) {
        return 1;
    } else {
        return n * factorial(n - 1);
    }
}

var resultadoFactorial = factorial(5);
console.log("Factorial de 5:", resultadoFactorial); // Factorial de 5: 120

// 10. Función como argumento de otra función (callback)
function operacion(a, b, operador) {
    return operador(a, b);
}

function resta(x, y) {
    return x - y;
}

var resultadoOperacion = operacion(8, 3, resta);
console.log("Resultado de la resta:", resultadoOperacion); // Resultado de la resta: 5

// 11. Cierre (closure) y función interna
function contador() {
    var count = 0;

    function incrementar() {
        count++;
        console.log("Contador:", count);
    }

    return incrementar;
}

var incremento = contador();
incremento(); // Contador: 1
incremento(); // Contador: 2

// 12. Función como método de un objeto
var calculadora = {
    sumar: function (x, y) {
        return x + y;
    },
    restar: function (x, y) {
        return x - y;
    }
};

var sumaResult = calculadora.sumar(5, 3);
var restaResult = calculadora.restar(8, 2);

console.log("Suma:", sumaResult); // Suma: 8
console.log("Resta:", restaResult); // Resta: 6
```
Este ejemplo cubre los siguientes aspectos relacionados con funciones en JavaScript:

1. Declaración de funciones.
2. Llamada a funciones y retorno de valores.
3. Funciones sin valor de retorno.
4. Parámetros predeterminados (ES6+).
5. Funciones anónimas y asignación a variables.
6. Funciones flecha (ES6+).
7. Funciones recursivas.
8. Funciones como argumentos de otras funciones (callbacks).
9. Cierre (closure) y funciones internas.
10. Funciones como métodos de objetos.
    
Estos conceptos son fundamentales para comprender cómo trabajar con funciones en JavaScript y cómo pueden ser utilizados en diversos escenarios de programación.

### 6. Arreglos

Los arreglos almacenan conjuntos de valores en una sola variable.

```javascript
// 1. Declaración de un arreglo
var frutas = ["manzana", "banana", "naranja"];

// 2. Acceder a elementos del arreglo por índice
console.log(frutas[0]); // manzana

// 3. Propiedad 'length' para obtener la cantidad de elementos
console.log("Cantidad de frutas:", frutas.length); // Cantidad de frutas: 3

// 4. Agregar un elemento al final del arreglo con 'push'
frutas.push("uva");
console.log("Frutas después de agregar uva:", frutas); // ["manzana", "banana", "naranja", "uva"]

// 5. Eliminar el último elemento del arreglo con 'pop'
var frutaEliminada = frutas.pop();
console.log("Fruta eliminada:", frutaEliminada); // Fruta eliminada: uva
console.log("Frutas después de eliminar la uva:", frutas); // ["manzana", "banana", "naranja"]

// 6. Agregar un elemento al principio del arreglo con 'unshift'
frutas.unshift("cereza");
console.log("Frutas después de agregar cereza al principio:", frutas); // ["cereza", "manzana", "banana", "naranja"]

// 7. Eliminar el primer elemento del arreglo con 'shift'
var primeraFruta = frutas.shift();
console.log("Primera fruta eliminada:", primeraFruta); // Primera fruta eliminada: cereza
console.log("Frutas después de eliminar la cereza:", frutas); // ["manzana", "banana", "naranja"]

// 8. Encontrar el índice de un elemento en el arreglo con 'indexOf'
var indiceNaranja = frutas.indexOf("naranja");
console.log("Índice de la naranja:", indiceNaranja); // Índice de la naranja: 2

// 9. Eliminar un elemento en una posición específica con 'splice'
frutas.splice(1, 1); // Elimina 1 elemento a partir del índice 1
console.log("Frutas después de eliminar la banana:", frutas); // ["manzana", "naranja"]

// 10. Copiar un arreglo (shallow copy) con 'slice'
var copiaFrutas = frutas.slice();
console.log("Copia de frutas:", copiaFrutas); // ["manzana", "naranja"]

// 11. Iterar a través de elementos del arreglo con 'for...of'
for (var fruta of frutas) {
    console.log("Fruta:", fruta);
}

// 12. Transformar un arreglo con 'map'
var numeros = [1, 2, 3, 4, 5];
var cuadrados = numeros.map(function(numero) {
    return numero * numero;
});
console.log("Cuadrados de números:", cuadrados); // [1, 4, 9, 16, 25]

// 13. Filtrar elementos de un arreglo con 'filter'
var numerosPares = numeros.filter(function(numero) {
    return numero % 2 === 0;
});
console.log("Números pares:", numerosPares); // [2, 4]

// 14. Reducir un arreglo a un solo valor con 'reduce'
var sumaTotal = numeros.reduce(function(acumulador, numero) {
    return acumulador + numero;
}, 0); // El 0 es el valor inicial del acumulador
console.log("Suma total de números:", sumaTotal); // Suma total de números: 15
```
Este ejemplo cubre los siguientes aspectos relacionados con arreglos en JavaScript:

1. Declaración de arreglos.
2. Acceso a elementos por índice.
3. Uso de la propiedad `length`.
4. Agregar elementos al final con `push`.
5. Eliminar el último elemento con `pop`.
6. Agregar elementos al principio con `unshift`.
7. Eliminar el primer elemento con `shift`.
8. Encontrar el índice de un elemento con `indexOf`.
9. Eliminar elementos específicos con `splice`.
10. Crear copias superficiales de arreglos con `slice`.
11. Iteración a través de elementos con `for...of`.
12. Transformación de arreglos con `map`.
13. Filtrado de elementos con `filter`.
14. Reducción de arreglos a un solo valor con `reduce`.

Estos conceptos son esenciales para trabajar con arreglos en JavaScript y te permitirán manipular y procesar datos de manera efectiva.

### 7. Objetos

En programación, los objetos son estructuras de datos que permiten organizar y almacenar información de una manera más compleja y significativa. Los objetos se utilizan para representar entidades del mundo real y sus atributos, y son una parte fundamental de la programación orientada a objetos (POO).

```javascript
// 1. Declaración de un objeto
var persona = {
    nombre: "Juan",
    edad: 30,
    ciudad: "México"
};

// 2. Acceso a propiedades del objeto por nombre
console.log("Nombre de la persona:", persona.nombre); // Nombre de la persona: Juan
console.log("Edad de la persona:", persona.edad); // Edad de la persona: 30

// 3. Modificar propiedades del objeto
persona.edad = 31;
console.log("Nueva edad de la persona:", persona.edad); // Nueva edad de la persona: 31

// 4. Agregar nuevas propiedades al objeto
persona.trabajo = "programador";
console.log("Trabajo de la persona:", persona.trabajo); // Trabajo de la persona: programador

// 5. Eliminar propiedades del objeto con 'delete'
delete persona.ciudad;
console.log("Ciudad de la persona (eliminada):", persona.ciudad); // Ciudad de la persona (eliminada): undefined

// 6. Verificar si una propiedad existe en el objeto
var tieneTrabajo = "trabajo" in persona;
console.log("¿La persona tiene trabajo?", tieneTrabajo); // ¿La persona tiene trabajo? true

// 7. Iteración a través de propiedades del objeto con 'for...in'
for (var propiedad in persona) {
    console.log("Propiedad:", propiedad, "Valor:", persona[propiedad]);
}

// 8. Crear objetos con funciones constructoras
function Producto(nombre, precio) {
    this.nombre = nombre;
    this.precio = precio;
}

var producto1 = new Producto("Camiseta", 20);
console.log("Producto 1:", producto1);

// 9. Agregar métodos a objetos
producto1.mostrarInfo = function () {
    console.log("Nombre:", this.nombre, "Precio:", this.precio);
};

producto1.mostrarInfo(); // Nombre: Camiseta Precio: 20

// 10. Prototipos y herencia
function Animal(nombre) {
    this.nombre = nombre;
}

Animal.prototype.hablar = function (sonido) {
    console.log(this.nombre + " hace " + sonido);
};

function Perro(nombre) {
    Animal.call(this, nombre);
}

Perro.prototype = Object.create(Animal.prototype);

var perro = new Perro("Firulais");
perro.hablar("ladrido"); // Firulais hace ladrido

// 11. Uso de objetos literales como estructuras de datos
var libro = {
    titulo: "La Odisea",
    autor: "Homero",
    publicado: 800 a.C.
};

console.log("Libro:", libro);

// 12. Desestructuración de objetos (ES6+)
var { titulo, autor } = libro;
console.log("Título:", titulo, "Autor:", autor);
```
Este ejemplo abarca los siguientes conceptos relacionados con objetos en JavaScript:

1. Declaración de objetos.
2. Acceso a propiedades del objeto por nombre.
3. Modificación de propiedades del objeto.
4. Agregar nuevas propiedades al objeto.
5. Eliminación de propiedades del objeto con `delete`.
6. Verificación de la existencia de propiedades en el objeto.
7. Iteración a través de propiedades del objeto con `for...in`.
8. Creación de objetos con funciones constructoras.
9. Agregación de métodos a objetos.
10. Uso de prototipos y herencia.
11. Uso de objetos literales como estructuras de datos.
12. Desestructuración de objetos (ES6+).

### 8. Arreglos Multidimensionales

Los arreglos multidimensionales son arreglos que contienen otros arreglos, lo que permite representar datos en una estructura más compleja.

```javascript
// 1. Declaración de un arreglo multidimensional (matriz)
var matriz = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

// 2. Acceder a un valor en la matriz usando índices
console.log("Valor en la fila 1, columna 2:", matriz[0][1]); // Valor en la fila 1, columna 2: 2

// 3. Modificar un valor en la matriz
matriz[2][2] = 10;
console.log("Valor modificado en la fila 3, columna 3:", matriz[2][2]); // Valor modificado en la fila 3, columna 3: 10

// 4. Iteración a través de una matriz multidimensional con bucles anidados
console.log("Iteración a través de la matriz:");
for (var fila = 0; fila < matriz.length; fila++) {
    for (var columna = 0; columna < matriz[fila].length; columna++) {
        console.log("Fila " + fila + ", Columna " + columna + ": " + matriz[fila][columna]);
    }
}

// 5. Creación de una matriz bidimensional vacía
var matrizVacia = new Array(3); // Crear un arreglo con 3 elementos (filas)
for (var i = 0; i < 3; i++) {
    matrizVacia[i] = new Array(3); // Cada elemento es un arreglo con 3 elementos (columnas)
}

matrizVacia[0][0] = 11;
console.log("Matriz con valor en la fila 1, columna 1:", matrizVacia[0][0]);

// 6. Matrices multidimensionales en objetos
var datosEstudiantes = [
    { nombre: "Juan", calificaciones: [90, 85, 88] },
    { nombre: "María", calificaciones: [78, 92, 87] },
    { nombre: "Pedro", calificaciones: [85, 90, 79] }
];

console.log("Calificación de María en la segunda materia:", datosEstudiantes[1].calificaciones[1]);

// 7. Creación de una matriz multidimensional con bucle
function crearMatriz(filas, columnas) {
    var matriz = new Array(filas);
    for (var i = 0; i < filas; i++) {
        matriz[i] = new Array(columnas);
    }
    return matriz;
}

var nuevaMatriz = crearMatriz(2, 3);
nuevaMatriz[0][1] = 42;
console.log("Valor en la fila 1, columna 2 de la nueva matriz:", nuevaMatriz[0][1]);
```
Este ejemplo cubre los siguientes conceptos relacionados con arreglos multidimensionales en JavaScript:

1. Declaración de arreglos multidimensionales (matrices).
2. Acceso y modificación de valores en una matriz.
3. Iteración a través de una matriz multidimensional con bucles anidados.
4. Creación de una matriz bidimensional vacía.
5. Uso de matrices multidimensionales en objetos.
6. Creación de una matriz multidimensional con un bucle. 

Los arreglos multidimensionales son útiles cuando se necesita representar datos en estructuras más complejas, como tablas, matrices, sistemas de coordenadas, y en situaciones donde los datos están organizados en filas y columnas o en estructuras anidadas.

### 9. Métodos de Arreglos

JavaScript proporciona una variedad de métodos incorporados para manipular arreglos, como `push`, `pop`, `shift`, `unshift`, `splice`, `forEach` y más.

```javascript
// 1. Declaración de un arreglo
var frutas = ["manzana", "banana", "naranja"];

// 2. Agregar un elemento al final del arreglo con 'push'
frutas.push("uva");
console.log("Arreglo después de agregar uva:", frutas); // ["manzana", "banana", "naranja", "uva"]

// 3. Eliminar el último elemento del arreglo con 'pop'
var frutaEliminada = frutas.pop();
console.log("Fruta eliminada:", frutaEliminada); // Fruta eliminada: uva
console.log("Arreglo después de eliminar la uva:", frutas); // ["manzana", "banana", "naranja"]

// 4. Eliminar el primer elemento del arreglo con 'shift'
var primeraFruta = frutas.shift();
console.log("Primera fruta eliminada:", primeraFruta); // Primera fruta eliminada: manzana
console.log("Arreglo después de eliminar la manzana:", frutas); // ["banana", "naranja"]

// 5. Agregar un elemento al principio del arreglo con 'unshift'
frutas.unshift("pera");
console.log("Arreglo después de agregar pera al principio:", frutas); // ["pera", "banana", "naranja"]

// 6. Encontrar el índice de un elemento en el arreglo con 'indexOf'
var indiceNaranja = frutas.indexOf("naranja");
console.log("Índice de la naranja:", indiceNaranja); // Índice de la naranja: 2

// 7. Eliminar un elemento en una posición específica con 'splice'
frutas.splice(1, 1); // Elimina 1 elemento a partir del índice 1
console.log("Arreglo después de eliminar la banana:", frutas); // ["pera", "naranja"]

// 8. Iterar a través de elementos del arreglo con 'forEach'
console.log("Iteración a través del arreglo:");
frutas.forEach(function (fruta, indice) {
    console.log("Índice " + indice + ": " + fruta);
});

// 9. Filtrar elementos de un arreglo con 'filter'
var frutasFiltradas = frutas.filter(function (fruta) {
    return fruta.length > 5;
});
console.log("Frutas con nombres largos:", frutasFiltradas); // ["naranja"]

// 10. Transformar un arreglo con 'map'
var frutasEnMayusculas = frutas.map(function (fruta) {
    return fruta.toUpperCase();
});
console.log("Frutas en mayúsculas:", frutasEnMayusculas); // ["PERA", "NARANJA"]

// 11. Reducir un arreglo a un solo valor con 'reduce'
var sumaDeLongitudes = frutas.reduce(function (acumulador, fruta) {
    return acumulador + fruta.length;
}, 0); // El 0 es el valor inicial del acumulador
console.log("Suma de longitudes de frutas:", sumaDeLongitudes); // Suma de longitudes de frutas: 12
```
Este ejemplo cubre los siguientes métodos de arreglos en JavaScript:

1. `push`: Agregar elementos al final del arreglo.
2. `pop`: Eliminar el último elemento del arreglo.
3. `shift`: Eliminar el primer elemento del arreglo.
4. `unshift`: Agregar elementos al principio del arreglo.
5. `indexOf`: Encontrar el índice de un elemento en el arreglo.
6. `splice`: Eliminar elementos en una posición específica.
7. `forEach`: Iterar a través de elementos del arreglo.
8. `filter`: Filtrar elementos basados en una condición.
9. `map`: Transformar elementos del arreglo.
10. `reduce`: Reducir un arreglo a un solo valor.

Estos métodos son herramientas poderosas para manipular y procesar arreglos en JavaScript, lo que te permite realizar una amplia variedad de tareas de forma eficiente.

### 10. Iteración de Objetos

Puedes iterar sobre las propiedades de un objeto utilizando bucles `for...in` o métodos como `Object.keys`.

```javascript
// 1. Declaración de un objeto
var persona = {
    nombre: "Juan",
    edad: 30,
    ciudad: "México"
};

// 2. Iteración a través de propiedades del objeto con 'for...in'
console.log("Iteración a través de propiedades del objeto:");
for (var propiedad in persona) {
    if (persona.hasOwnProperty(propiedad)) { // Verificar si la propiedad es propia (no heredada)
        console.log(propiedad + ": " + persona[propiedad]);
    }
}

// 3. Obtener un arreglo de las propiedades del objeto con 'Object.keys'
var propiedades = Object.keys(persona);
console.log("Propiedades del objeto como arreglo:", propiedades); // ["nombre", "edad", "ciudad"]

// 4. Iteración a través de propiedades del objeto usando 'Object.keys'
console.log("Iteración a través de propiedades con 'Object.keys':");
propiedades.forEach(function (propiedad) {
    console.log(propiedad + ": " + persona[propiedad]);
});

// 5. Iteración a través de propiedades y valores con 'Object.entries' (ES6+)
console.log("Iteración a través de propiedades y valores con 'Object.entries' (ES6+):");
for (var [clave, valor] of Object.entries(persona)) {
    console.log(clave + ": " + valor);
}

// 6. Uso de métodos para verificar propiedades en un objeto
console.log("¿El objeto tiene la propiedad 'nombre'?", persona.hasOwnProperty("nombre")); // true
console.log("¿El objeto tiene la propiedad 'trabajo'?", persona.hasOwnProperty("trabajo")); // false

// 7. Copia superficial de un objeto
var copiaPersona = { ...persona }; // ES6+
console.log("Copia superficial del objeto:", copiaPersona);

// 8. Iteración a través de propiedades de un objeto heredado
var personaHeredada = Object.create(persona);
personaHeredada.trabajo = "programador";

console.log("Iteración a través de propiedades heredadas:");
for (var propiedad in personaHeredada) {
    if (personaHeredada.hasOwnProperty(propiedad)) {
        console.log(propiedad + ": " + personaHeredada[propiedad]);
    }
}
```
Este ejemplo cubre los siguientes conceptos relacionados con la iteración de objetos en JavaScript:

1. Declaración de un objeto.
2. Iteración a través de propiedades del objeto con `for...in`.
3. Uso de `hasOwnProperty` para verificar si una propiedad es propia del objeto.
4. Obtención de un arreglo de las propiedades del objeto con `Object.keys`.
5. Iteración a través de propiedades del objeto utilizando `Object.keys`.
6. Iteración a través de propiedades y valores con `Object.entries` (ES6+).
7. Uso de métodos para verificar la existencia de propiedades en un objeto.
8. Copia superficial de un objeto (ES6+).
9. Iteración a través de propiedades de un objeto heredado.

Estos conceptos te permitirán trabajar con objetos de manera efectiva, ya sea para procesar propiedades propias o heredadas, iterar a través de ellas y manipular datos en tus aplicaciones.

### 11. Clases y Programación Orientada a Objetos

JavaScript admite la programación orientada a objetos (POO). Puedes crear clases y objetos para organizar tu código de manera más estructurada.

```javascript
// 1. Declaración de una clase 'Persona'
class Persona {
    // 2. Constructor para inicializar propiedades
    constructor(nombre, edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    // 3. Método de instancia para saludar
    saludar() {
        console.log(`Hola, soy ${this.nombre} y tengo ${this.edad} años.`);
    }
}

// 4. Creación de objetos (instancias) de la clase 'Persona'
var juan = new Persona("Juan", 25);
var maria = new Persona("Maria", 30);

// 5. Llamada a métodos de instancia
juan.saludar(); // Hola, soy Juan y tengo 25 años.
maria.saludar(); // Hola, soy Maria y tengo 30 años.

// 6. Herencia: Creación de una subclase 'Estudiante' que extiende de 'Persona'
class Estudiante extends Persona {
    constructor(nombre, edad, curso) {
        super(nombre, edad); // Llamar al constructor de la clase padre
        this.curso = curso;
    }

    // 7. Sobrescribir un método de la clase padre
    saludar() {
        console.log(`Hola, soy ${this.nombre}, tengo ${this.edad} años y estudio ${this.curso}.`);
    }
}

// 8. Creación de objetos de la subclase 'Estudiante'
var estudiante1 = new Estudiante("Laura", 22, "Matemáticas");
var estudiante2 = new Estudiante("Carlos", 28, "Historia");

// 9. Llamada a métodos de instancia de la subclase
estudiante1.saludar(); // Hola, soy Laura, tengo 22 años y estudio Matemáticas.
estudiante2.saludar(); // Hola, soy Carlos, tengo 28 años y estudio Historia.
```
Este ejemplo cubre los siguientes conceptos relacionados con clases y programación orientada a objetos (POO) en JavaScript:

1. Declaración de una clase `Persona`.
2. Uso de un constructor para inicializar propiedades en una clase.
3. Definición de métodos de instancia en una clase.
4. Creación de objetos (instancias) de la clase `Persona`.
5. Llamada a métodos de instancia en objetos.
6. Herencia: Creación de una subclase `Estudiante` que extiende de `Persona`.
7. Sobrescritura de un método de la clase padre en la subclase.
8. Creación de objetos de la subclase `Estudiante`.
9. Llamada a métodos de instancia de la subclase.

Estos conceptos son fundamentales para aplicar la programación orientada a objetos en JavaScript y crear estructuras de código más organizadas y reutilizables.

### 12. Manejo de Eventos

JavaScript se utiliza ampliamente para manejar eventos en aplicaciones web. Puedes adjuntar funciones a eventos como clics de botón, cambios de entrada, etc.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Manejo de Eventos en JavaScript</title>
</head>
<body>
    <button id="miBoton">Haz clic en mí</button>
    <input type="text" id="entradaTexto">
    <div id="resultado"></div>

    <script>
        // 1. Seleccionar un elemento del DOM por su ID
        var boton = document.getElementById("miBoton");
        var entradaTexto = document.getElementById("entradaTexto");
        var resultado = document.getElementById("resultado");

        // 2. Adjuntar un controlador de eventos a un elemento
        boton.addEventListener("click", function() {
            // 3. Manejar el evento (en este caso, mostrar una alerta)
            alert("Hiciste clic en el botón.");
        });

        // 4. Adjuntar un controlador de eventos a un campo de entrada de texto
        entradaTexto.addEventListener("input", function() {
            // 5. Obtener el valor del campo de entrada de texto
            var texto = entradaTexto.value;
            
            // 6. Actualizar el contenido de un elemento HTML
            resultado.innerHTML = "Texto ingresado: " + texto;
        });

        // 7. Adjuntar un controlador de eventos para el evento 'mouseover'
        boton.addEventListener("mouseover", function() {
            boton.style.backgroundColor = "lightblue";
        });

        // 8. Adjuntar un controlador de eventos para el evento 'mouseout'
        boton.addEventListener("mouseout", function() {
            boton.style.backgroundColor = "";
        });
    </script>
</body>
</html>
```
Este ejemplo cubre los siguientes conceptos relacionados con el manejo de eventos en JavaScript:

1. Seleccionar un elemento del DOM por su ID.
2. Adjuntar un controlador de eventos a un elemento.
3. Manejar eventos, en este caso, mostrando una alerta al hacer clic en un botón.
4. Adjuntar un controlador de eventos a un campo de entrada de texto.
5. Obtener el valor del campo de entrada de texto.
6. Actualizar el contenido de un elemento HTML con el valor del campo de entrada de texto.
7. Adjuntar controladores de eventos para los eventos 'mouseover' (al pasar el ratón sobre el botón) y 'mouseout' (al quitar el ratón del botón).
8. Cambiar el estilo de un elemento en respuesta a eventos ('mouseover' y 'mouseout' cambian el fondo del botón).

Estos conceptos son fundamentales para interactuar con elementos del DOM y responder a eventos en aplicaciones web.

### 13. AJAX y Fetch

AJAX (Asynchronous JavaScript and XML) y Fetch son dos tecnologías utilizadas en desarrollo web para realizar solicitudes de red asíncronas y obtener datos de servidores web. Aunque AJAX fue ampliamente utilizado en el pasado, Fetch es una API más moderna que ha simplificado la forma en que se realizan estas solicitudes.

JavaScript permite realizar solicitudes de red asíncronas para obtener datos de servidores web. La API Fetch es comúnmente utilizada para este propósito.

```javascript
// 1. Realizar una solicitud AJAX usando la API Fetch
fetch('https://api.ejemplo.com/data')
    .then(response => {
        // 2. Verificar el estado de la respuesta HTTP
        if (!response.ok) {
            throw new Error('Error en la solicitud: ' + response.status);
        }
        // 3. Parsear la respuesta como JSON
        return response.json();
    })
    .then(data => {
        // 4. Utilizar los datos recibidos
        console.log('Datos recibidos:', data);
    })
    .catch(error => {
        // 5. Capturar errores de red o errores en la solicitud
        console.error('Error: ' + error);
    });
```
Este ejemplo cubre los siguientes conceptos relacionados con AJAX y Fetch en JavaScript:

1. Realizar una solicitud AJAX utilizando la API Fetch.
2. Verificar el estado de la respuesta HTTP para detectar errores en la solicitud.
3. Parsear la respuesta como JSON para trabajar con los datos recibidos.
4. Utilizar los datos obtenidos en la respuesta de la solicitud.
5. Capturar y manejar errores, ya sea errores de red o errores en la solicitud.

El uso de Fetch es una técnica común en el desarrollo web para realizar solicitudes de red asíncronas y obtener datos de servidores web, lo que permite interactuar con APIs y recuperar información dinámica para su uso en aplicaciones web.

Estos son algunos de los conceptos fundamentales que te ayudarán a comprender y utilizar JavaScript de manera efectiva. JavaScript es un lenguaje poderoso y versátil que se utiliza en una variedad de contextos, incluyendo desarrollo web, aplicaciones móviles y más. Practicar y trabajar en proyectos te ayudará a fortalecer tus habilidades en JavaScript.

## Agradecimientos

Hecho con ❤️ por Matias Ignacio - https://github.com/Matignaciom
