# JavaScript Mastery: Desde lo Fundamental hasta lo Avanzado

Este repositorio es una guía completa para aprender JavaScript, comenzando desde los fundamentos más básicos y avanzando hacia técnicas avanzadas. Ya sea que seas un principiante que recién comienza a programar o un desarrollador intermedio que busca perfeccionar sus habilidades, encontrarás lecciones y ejemplos prácticos para ayudarte a dominar JavaScript.

Este trabajo, *JavaScript Mastery: Desde lo Fundamental hasta lo Avanzado* (Dominando_JavaScript), se publica bajo una Licencia Creative Commons Atribución-NoComercial 4.0 Internacional por Matías Ignacio Paredes Márquez. Para obtener más información sobre la licencia, visita: Licencia. // MEJORA: Corregí "NoComercial" a "Atribución-NoComercial" para precisión en el nombre de la licencia.

**Consejo general**: Prueba los ejemplos en la consola del navegador (F12 &gt; Console) o herramientas en línea como JSFiddle o CodePen para ver resultados en tiempo real. Esto mejora el aprendizaje interactivo. // MEJORA: Agregado para mejorar usabilidad.

## 1. Variables y Tipos de Datos

JavaScript es un lenguaje de programación dinámico que te permite declarar variables utilizando tres palabras clave: `var`, `let`, y `const`. Estas tienen diferentes alcances y usos. En código moderno, se recomienda evitar `var` y preferir `let` o `const` para prevenir errores como hoisting inesperado. // MEJORA: Énfasis en mejores prácticas para JS moderno.

### `var`:

- Declara variables con ámbito de función o global.
- Pueden ser redeclaradas y actualizadas en cualquier lugar del ámbito.
- No respetan el ámbito de bloque, lo que puede causar filtraciones fuera de condicionales o bucles.

```javascript
var edad = 30;
```

### `let`:

- Declara variables con ámbito de bloque.
- No permite redeclaración en el mismo ámbito.
- Respeta el ámbito de bloque, evitando filtraciones.

```javascript
let nombre = "Juan";
```

### `const`:

- Declara variables con ámbito de bloque que no cambian su valor tras la asignación inicial.
- Deben asignarse al declararse y no pueden reasignarse.
- Respeta el ámbito de bloque, como `let`.

```javascript
const PI = 3.1416;
```

## 1.1 Scope de variables var, let y const

### Scope de `var`:

```javascript
function ejemploVar() {
  if (true) {
    var x = 10;
  }
  console.log(x); // x está disponible aquí
}

ejemploVar(); // Imprime 10
// console.log(x); // MEJORA: Comenté esta línea porque x no debería estar disponible globalmente en código moderno; evita confusiones.
```

Las variables declaradas con `var` dentro de un bloque `if` son accesibles fuera debido a su ámbito de función o global.

### Scope de `let`:

```javascript
function ejemploLet() {
  if (true) {
    let y = 20;
  }
  console.log(y); // y no está disponible aquí
}

ejemploLet(); // Genera un error: "y is not defined"
```

Con `let`, la variable `y` tiene ámbito de bloque, por lo que no es accesible fuera del bloque `if`, evitando fugas de variables.

### Scope de `const`:

```javascript
function ejemploConst() {
  if (true) {
    const z = 30;
  }
  console.log(z); // z no está disponible aquí
}

ejemploConst(); // Genera un error: "z is not defined"
```

El comportamiento de `const` es similar a `let` en cuanto a ámbito de bloque.

`var` tiene ámbito de función o global, mientras que `let` y `const` tienen ámbito de bloque. Usar `let` y `const` es preferible para código más seguro y predecible.

## 2. Operadores

JavaScript admite operadores para operaciones matemáticas, comparaciones y más.

```javascript
const numero1 = 10; // MEJORA: Cambié a const para variables inmutables.
const numero2 = 5;

// Operadores aritméticos
const suma = numero1 + numero2; // suma = 15
const resta = numero1 - numero2; // resta = 5
const multiplicacion = numero1 * numero2; // multiplicación = 50
const division = numero1 / numero2; // división = 2
const modulo = numero1 % numero2; // módulo = 0 (resto de la división)

// Operadores de asignación
let resultado = 0;
resultado += numero1; // resultado = 10
resultado -= numero2; // resultado = 5
resultado *= numero1; // resultado = 50
resultado /= numero2; // resultado = 10

// Operadores de comparación
const igualdad = numero1 == numero2; // igualdad = false
const desigualdad = numero1 != numero2; // desigualdad = true
const mayorQue = numero1 > numero2; // mayorQue = true
const menorQue = numero1 < numero2; // menorQue = false
const mayorIgual = numero1 >= numero2; // mayorIgual = true
const menorIgual = numero1 <= numero2; // menorIgual = false

// Operadores lógicos
const condicion1 = true;
const condicion2 = false;
const yLogico = condicion1 && condicion2; // yLogico = false (AND lógico)
const oLogico = condicion1 || condicion2; // oLogico = true (OR lógico)
const noLogico = !condicion1; // noLogico = false (NOT lógico)
```

## 3. Condicionales

Las instrucciones condicionales permiten tomar decisiones en el código.

```javascript
// Función para determinar si un número es par o impar
function esParOImpar(numero) {
    if (typeof numero !== 'number') {
        throw new Error('La entrada no es un número.');
    }
    if (numero % 2 === 0) {
        return 'El número es par.';
    } else {
        return 'El número es impar.';
    }
}

try {
    const entrada = 42; // MEJORA: Usé const para variables inmutables.
    const resultado = esParOImpar(entrada);
    console.log(resultado);
} catch (error) {
    console.error('Ocurrió un error: ' + error.message);
}

// Ejemplo de un switch statement para días de la semana
const diaDeLaSemana = 'lunes'; // MEJORA: Usé const.

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
const numero = -5; // MEJORA: Usé const.
const esPositivo = (numero >= 0) ? 'positivo' : 'negativo';
console.log('El número es ' + esPositivo);
```

Este código muestra cómo verificar si un número es par o impar, tomar decisiones basadas en el día de la semana y usar el operador ternario para determinar si un número es positivo o negativo, con manejo de excepciones.

## 4. Bucles

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
            bucleAsincronico(); // Llamada recursiva
        }
    }, 1000);
}

bucleAsincronico();
```

Este ejemplo abarca bucles `for`, `while`, `do...while`, iteración de arrays y objetos, control con `break` y `continue`, bucles anidados, optimización de bucles y bucles asincrónicos.

## 5. Funciones

Las funciones son bloques de código reutilizables que pueden recibir argumentos y devolver valores.

```javascript
// 1. Declaración de una función con parámetros y valor de retorno
function suma(a, b) {
    return a + b;
}

// 2. Llamada a la función y almacenamiento del resultado
const resultado = suma(2, 3); // MEJORA: Usé const.

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

const precioFinal1 = calcularPrecio(100, 0.1); // Con descuento del 10%
console.log("Precio final con descuento:", precioFinal1); // Precio final con descuento: 90

const precioFinal2 = calcularPrecio(75); // Sin descuento
console.log("Precio final sin descuento:", precioFinal2); // Precio final sin descuento: 75

// 7. Función anónima y asignación a una variable
const multiplicar = function (x, y) { // MEJORA: Usé const.
    return x * y;
};

const producto = multiplicar(4, 5);
console.log("Producto:", producto); // Producto: 20

// 8. Función flecha (ES6+)
const dividir = (a, b) => a / b;

const cociente = dividir(10, 2);
console.log("Cociente:", cociente); // Cociente: 5

// 9. Función recursiva
function factorial(n) {
    if (n === 0 || n === 1) {
        return 1;
    } else {
        return n * factorial(n - 1);
    }
}

const resultadoFactorial = factorial(5);
console.log("Factorial de 5:", resultadoFactorial); // Factorial de 5: 120

// 10. Función como argumento de otra función (callback)
function operacion(a, b, operador) {
    return operador(a, b);
}

function resta(x, y) {
    return x - y;
}

const resultadoOperacion = operacion(8, 3, resta);
console.log("Resultado de la resta:", resultadoOperacion); // Resultado de la resta: 5

// 11. Cierre (closure) y función interna
function contador() {
    let count = 0; // MEJORA: Cambié a let.
    function incrementar() {
        count++;
        console.log("Contador:", count);
    }
    return incrementar;
}

const incremento = contador();
incremento(); // Contador: 1
incremento(); // Contador: 2

// 12. Función como método de un objeto
const calculadora = { // MEJORA: Usé const.
    sumar: function (x, y) {
        return x + y;
    },
    restar: function (x, y) {
        return x - y;
    }
};

const sumaResult = calculadora.sumar(5, 3);
const restaResult = calculadora.restar(8, 2);

console.log("Suma:", sumaResult); // Suma: 8
console.log("Resta:", restaResult); // Resta: 6
```

Este ejemplo cubre:

 1. Declaración de funciones.
 2. Llamada a funciones y retorno de valores.
 3. Funciones sin valor de retorno.
 4. Parámetros predeterminados (ES6+).
 5. Funciones anónimas y asignación a variables.
 6. Funciones flecha (ES6+).
 7. Funciones recursivas.
 8. Funciones como argumentos (callbacks).
 9. Cierres y funciones internas.
10. Funciones como métodos de objetos.

## 6. Arreglos

Los arreglos almacenan conjuntos de valores en una sola variable.

```javascript
// 1. Declaración de un arreglo
let frutas = ["manzana", "banana", "naranja"]; // MEJORA: Usé let porque el arreglo será mutado.

// 2. Acceder a elementos del arreglo por índice
console.log(frutas[0]); // manzana

// 3. Propiedad 'length' para obtener la cantidad de elementos
console.log("Cantidad de frutas:", frutas.length); // Cantidad de frutas: 3

// 4. Agregar un elemento al final del arreglo con 'push'
frutas.push("uva");
console.log("Frutas después de agregar uva:", frutas); // ["manzana", "banana", "naranja", "uva"]

// 5. Eliminar el último elemento del arreglo con 'pop'
const frutaEliminada = frutas.pop(); // MEJORA: Usé const.
console.log("Fruta eliminada:", frutaEliminada); // Fruta eliminada: uva
console.log("Frutas después de eliminar la uva:", frutas); // ["manzana", "banana", "naranja"]

// 6. Agregar un elemento al principio del arreglo con 'unshift'
frutas.unshift("cereza");
console.log("Frutas después de agregar cereza al principio:", frutas); // ["cereza", "manzana", "banana", "naranja"]

// 7. Eliminar el primer elemento del arreglo con 'shift'
const primeraFruta = frutas.shift(); // MEJORA: Usé const.
console.log("Primera fruta eliminada:", primeraFruta); // Primera fruta eliminada: cereza
console.log("Frutas después de eliminar la cereza:", frutas); // ["manzana", "banana", "naranja"]

// 8. Encontrar el índice de un elemento en el arreglo con 'indexOf'
const indiceNaranja = frutas.indexOf("naranja"); // MEJORA: Usé const.
console.log("Índice de la naranja:", indiceNaranja); // Índice de la naranja: 2

// 9. Eliminar un elemento en una posición específica con 'splice'
frutas.splice(1, 1); // Elimina 1 elemento a partir del índice 1
console.log("Frutas después de eliminar la banana:", frutas); // ["manzana", "naranja"]

// 10. Copiar un arreglo (shallow copy) con 'slice'
const copiaFrutas = frutas.slice(); // MEJORA: Usé const.
console.log("Copia de frutas:", copiaFrutas); // ["manzana", "naranja"]

// 11. Iterar a través de elementos del arreglo con 'for...of'
for (const fruta of frutas) {
    console.log("Fruta:", fruta);
}

// 12. Transformar un arreglo con 'map'
const numeros = [1, 2, 3, 4, 5];
const cuadrados = numeros.map(numero => numero * numero); // MEJORA: Usé arrow function para consistencia con ES6+.
console.log("Cuadrados de números:", cuadrados); // [1, 4, 9, 16, 25]

// 13. Filtrar elementos de un arreglo con 'filter'
const numerosPares = numeros.filter(numero => numero % 2 === 0); // MEJORA: Usé arrow function.
console.log("Números pares:", numerosPares); // [2, 4]

// 14. Reducir un arreglo a un solo valor con 'reduce'
const sumaTotal = numeros.reduce((acumulador, numero) => acumulador + numero, 0); // MEJORA: Usé arrow function.
console.log("Suma total de números:", sumaTotal); // Suma total de números: 15
```

Este ejemplo cubre:

1. Declaración de arreglos.
2. Acceso a elementos por índice.
3. Uso de `length`.
4. Métodos `push`, `pop`, `unshift`, `shift`, `indexOf`, `splice`, `slice`, `for...of`, `map`, `filter`, `reduce`.

## 7. Objetos

Los objetos son estructuras de datos que representan entidades del mundo real y sus atributos, fundamentales en programación orientada a objetos (POO).

```javascript
// 1. Declaración de un objeto
const persona = { // MEJORA: Usé const.
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
console.log("Ciudad de la persona (eliminada):", persona.ciudad); // undefined

// 6. Verificar si una propiedad existe en el objeto
const tieneTrabajo = "trabajo" in persona; // MEJORA: Usé const.
console.log("¿La persona tiene trabajo?", tieneTrabajo); // true

// 7. Iteración a través de propiedades del objeto con 'for...in'
for (const propiedad in persona) {
    console.log("Propiedad:", propiedad, "Valor:", persona[propiedad]);
}

// 8. Crear objetos con funciones constructoras
function Producto(nombre, precio) {
    this.nombre = nombre;
    this.precio = precio;
}

const producto1 = new Producto("Camiseta", 20); // MEJORA: Usé const.
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

const perro = new Perro("Firulais"); // MEJORA: Usé const.
perro.hablar("ladrido"); // Firulais hace ladrido

// 11. Uso de objetos literales como estructuras de datos
const libro = {
    titulo: "La Odisea",
    autor: "Homero",
    publicado: '800 a.C.' // MEJORA: Cambié a cadena para corregir error de sintaxis (original causaba error).
};

console.log("Libro:", libro);

// 12. Desestructuración de objetos (ES6+)
const { titulo, autor } = libro; // MEJORA: Usé const.
console.log("Título:", titulo, "Autor:", autor);
```

Este ejemplo cubre:

1. Declaración de objetos.
2. Acceso, modificación, adición y eliminación de propiedades.
3. Verificación de propiedades con `in`.
4. Iteración con `for...in`.
5. Funciones constructoras, métodos, prototipos, herencia y desestructuración.

## 8. Arreglos Multidimensionales

Los arreglos multidimensionales contienen otros arreglos, ideales para estructuras complejas como matrices.

```javascript
// 1. Declaración de un arreglo multidimensional (matriz)
let matriz = [ // MEJORA: Usé let por mutabilidad.
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

// 2. Acceder a un valor en la matriz usando índices
console.log("Valor en la fila 1, columna 2:", matriz[0][1]); // 2

// 3. Modificar un valor en la matriz
matriz[2][2] = 10;
console.log("Valor modificado en la fila 3, columna 3:", matriz[2][2]); // 10

// 4. Iteración a través de una matriz multidimensional con bucles anidados
console.log("Iteración a través de la matriz:");
for (let fila = 0; fila < matriz.length; fila++) { // MEJORA: Usé let.
    for (let columna = 0; columna < matriz[fila].length; columna++) {
        console.log("Fila " + fila + ", Columna " + columna + ": " + matriz[fila][columna]);
    }
}

// 5. Creación de una matriz bidimensional vacía
let matrizVacia = new Array(3); // MEJORA: Usé let.
for (let i = 0; i < 3; i++) {
    matrizVacia[i] = new Array(3);
}

matrizVacia[0][0] = 11;
console.log("Matriz con valor en la fila 1, columna 1:", matrizVacia[0][0]);

// 6. Matrices multidimensionales en objetos
const datosEstudiantes = [
    { nombre: "Juan", calificaciones: [90, 85, 88] },
    { nombre: "María", calificaciones: [78, 92, 87] },
    { nombre: "Pedro", calificaciones: [85, 90, 79] }
];

console.log("Calificación de María en la segunda materia:", datosEstudiantes[1].calificaciones[1]);

// 7. Creación de una matriz multidimensional con bucle
function crearMatriz(filas, columnas) {
    let matriz = new Array(filas); // MEJORA: Usé let.
    for (let i = 0; i < filas; i++) {
        matriz[i] = new Array(columnas);
    }
    return matriz;
}

const nuevaMatriz = crearMatriz(2, 3); // MEJORA: Usé const.
nuevaMatriz[0][1] = 42;
console.log("Valor en la fila 1, columna 2 de la nueva matriz:", nuevaMatriz[0][1]);
```

Este ejemplo cubre:

1. Declaración, acceso y modificación de matrices.
2. Iteración con bucles anidados.
3. Creación de matrices vacías y en objetos.
4. Creación de matrices con funciones.

## 9. Métodos de Arreglos

JavaScript ofrece métodos para manipular arreglos de forma eficiente.

```javascript
// 1. Declaración de un arreglo
let frutas = ["manzana", "banana", "naranja"]; // MEJORA: Usé let por mutabilidad.

// 2. Agregar un elemento al final del arreglo con 'push'
frutas.push("uva");
console.log("Arreglo después de agregar uva:", frutas); // ["manzana", "banana", "naranja", "uva"]

// 3. Eliminar el último elemento del arreglo con 'pop'
const frutaEliminada = frutas.pop(); // MEJORA: Usé const.
console.log("Fruta eliminada:", frutaEliminada); // Fruta eliminada: uva
console.log("Arreglo después de eliminar la uva:", frutas); // ["manzana", "banana", "naranja"]

// 4. Eliminar el primer elemento del arreglo con 'shift'
const primeraFruta = frutas.shift(); // MEJORA: Usé const.
console.log("Primera fruta eliminada:", primeraFruta); // Primera fruta eliminada: manzana
console.log("Arreglo después de eliminar la manzana:", frutas); // ["banana", "naranja"]

// 5. Agregar un elemento al principio del arreglo con 'unshift'
frutas.unshift("pera");
console.log("Arreglo después de agregar pera al principio:", frutas); // ["pera", "banana", "naranja"]

// 6. Encontrar el índice de un elemento en el arreglo con 'indexOf'
const indiceNaranja = frutas.indexOf("naranja"); // MEJORA: Usé const.
console.log("Índice de la naranja:", indiceNaranja); // Índice de la naranja: 2

// 7. Eliminar un elemento en una posición específica con 'splice'
frutas.splice(1, 1); // Elimina 1 elemento a partir del índice 1
console.log("Arreglo después de eliminar la banana:", frutas); // ["pera", "naranja"]

// 8. Iterar a través de elementos del arreglo con 'forEach'
console.log("Iteración a través del arreglo:");
frutas.forEach((fruta, indice) => { // MEJORA: Usé arrow function.
    console.log("Índice " + indice + ": " + fruta);
});

// 9. Filtrar elementos de un arreglo con 'filter'
const frutasFiltradas = frutas.filter(fruta => fruta.length > 5); // MEJORA: Usé arrow function.
console.log("Frutas con nombres largos:", frutasFiltradas); // ["naranja"]

// 10. Transformar un arreglo con 'map'
const frutasEnMayusculas = frutas.map(fruta => fruta.toUpperCase()); // MEJORA: Usé arrow function.
console.log("Frutas en mayúsculas:", frutasEnMayusculas); // ["PERA", "NARANJA"]

// 11. Reducir un arreglo a un solo valor con 'reduce'
const sumaDeLongitudes = frutas.reduce((acumulador, fruta) => acumulador + fruta.length, 0); // MEJORA: Usé arrow function.
console.log("Suma de longitudes de frutas:", sumaDeLongitudes); // Suma de longitudes de frutas: 12
```

Este ejemplo cubre métodos como `push`, `pop`, `shift`, `unshift`, `indexOf`, `splice`, `forEach`, `filter`, `map` y `reduce`.

## 10. Iteración de Objetos

Puedes iterar sobre propiedades de un objeto con `for...in` o métodos como `Object.keys`.

```javascript
// 1. Declaración de un objeto
const persona = { // MEJORA: Usé const.
    nombre: "Juan",
    edad: 30,
    ciudad: "México"
};

// 2. Iteración a través de propiedades del objeto con 'for...in'
console.log("Iteración a través de propiedades del objeto:");
for (const propiedad in persona) { // MEJORA: Usé const.
    if (persona.hasOwnProperty(propiedad)) {
        console.log(propiedad + ": " + persona[propiedad]);
    }
}

// 3. Obtener un arreglo de las propiedades del objeto con 'Object.keys'
const propiedades = Object.keys(persona); // MEJORA: Usé const.
console.log("Propiedades del objeto como arreglo:", propiedades); // ["nombre", "edad", "ciudad"]

// 4. Iteración a través de propiedades del objeto usando 'Object.keys'
console.log("Iteración a través de propiedades con 'Object.keys':");
propiedades.forEach((propiedad) => { // MEJORA: Usé arrow function.
    console.log(propiedad + ": " + persona[propiedad]);
});

// 5. Iteración a través de propiedades y valores con 'Object.entries' (ES6+)
console.log("Iteración a través de propiedades y valores con 'Object.entries' (ES6+):");
for (const [clave, valor] of Object.entries(persona)) { // MEJORA: Usé const.
    console.log(clave + ": " + valor);
}

// 6. Uso de métodos para verificar propiedades en un objeto
console.log("¿El objeto tiene la propiedad 'nombre'?", persona.hasOwnProperty("nombre")); // true
console.log("¿El objeto tiene la propiedad 'trabajo'?", persona.hasOwnProperty("trabajo")); // false

// 7. Copia superficial de un objeto
const copiaPersona = { ...persona }; // MEJORA: Usé const.
console.log("Copia superficial del objeto:", copiaPersona);

// 8. Iteración a través de propiedades de un objeto heredado
const personaHeredada = Object.create(persona); // MEJORA: Usé const.
personaHeredada.trabajo = "programador";

console.log("Iteración a través de propiedades heredadas:");
for (const propiedad in personaHeredada) { // MEJORA: Usé const.
    if (personaHeredada.hasOwnProperty(propiedad)) {
        console.log(propiedad + ": " + personaHeredada[propiedad]);
    }
}
```

Este ejemplo cubre:

1. Iteración con `for...in`, `Object.keys`, `Object.entries`.
2. Verificación con `hasOwnProperty`.
3. Copias superficiales y manejo de herencia.

## 11. Clases y Programación Orientada a Objetos

JavaScript admite POO con clases para un código estructurado.

```javascript
// 1. Declaración de una clase 'Persona'
class Persona {
    constructor(nombre, edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    saludar() {
        console.log(`Hola, soy ${this.nombre} y tengo ${this.edad} años.`);
    }
}

// 2. Creación de objetos (instancias) de la clase 'Persona'
const juan = new Persona("Juan", 25); // MEJORA: Usé const.
const maria = new Persona("Maria", 30); // MEJORA: Usé const.

// 3. Llamada a métodos de instancia
juan.saludar(); // Hola, soy Juan y tengo 25 años.
maria.saludar(); // Hola, soy Maria y tengo 30 años.

// 4. Herencia: Creación de una subclase 'Estudiante'
class Estudiante extends Persona {
    constructor(nombre, edad, curso) {
        super(nombre, edad);
        this.curso = curso;
    }

    saludar() {
        console.log(`Hola, soy ${this.nombre}, tengo ${this.edad} años y estudio ${this.curso}.`);
    }
}

// 5. Creación de objetos de la subclase 'Estudiante'
const estudiante1 = new Estudiante("Laura", 22, "Matemáticas"); // MEJORA: Usé const.
const estudiante2 = new Estudiante("Carlos", 28, "Historia"); // MEJORA: Usé const.

// 6. Llamada a métodos de instancia de la subclase
estudiante1.saludar(); // Hola, soy Laura, tengo 22 años y estudio Matemáticas.
estudiante2.saludar(); // Hola, soy Carlos, tengo 28 años y estudio Historia.
```

Este ejemplo cubre:

1. Declaración de clases, constructores, métodos.
2. Herencia y sobrescritura de métodos.

## 12. Manejo de Eventos

JavaScript permite manejar eventos en aplicaciones web, como clics o cambios en entradas.

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
        const boton = document.getElementById("miBoton"); // MEJORA: Usé const.
        const entradaTexto = document.getElementById("entradaTexto"); // MEJORA: Usé const.
        const resultado = document.getElementById("resultado"); // MEJORA: Usé const.

        // 2. Adjuntar un controlador de eventos a un elemento
        boton.addEventListener("click", () => { // MEJORA: Usé arrow function.
            alert("Hiciste clic en el botón.");
        });

        // 3. Adjuntar un controlador de eventos a un campo de entrada de texto
        entradaTexto.addEventListener("input", () => { // MEJORA: Usé arrow function.
            const texto = entradaTexto.value; // MEJORA: Usé const.
            resultado.innerHTML = "Texto ingresado: " + texto;
        });

        // 4. Adjuntar un controlador de eventos para el evento 'mouseover'
        boton.addEventListener("mouseover", () => { // MEJORA: Usé arrow function.
            boton.style.backgroundColor = "lightblue";
        });

        // 5. Adjuntar un controlador de eventos para el evento 'mouseout'
        boton.addEventListener("mouseout", () => { // MEJORA: Usé arrow function.
            boton.style.backgroundColor = "";
        });
    </script>
</body>
</html>
```

Este ejemplo cubre:

1. Selección de elementos del DOM.
2. Manejo de eventos (`click`, `input`, `mouseover`, `mouseout`).
3. Actualización del DOM en respuesta a eventos.

## 13. AJAX y Fetch

Fetch es una API moderna para solicitudes de red asíncronas, reemplazando a XMLHttpRequest por su simplicidad. // MEJORA: Explicación sobre ventajas de Fetch.

```javascript
// 1. Realizar una solicitud AJAX usando la API Fetch
fetch('https://api.ejemplo.com/data')
    .then(response => {
        if (!response.ok) {
            throw new Error('Error en la solicitud: ' + response.status);
        }
        return response.json();
    })
    .then(data => {
        console.log('Datos recibidos:', data);
    })
    .catch(error => {
        console.error('Error: ' + error);
    });
```

Este ejemplo cubre:

1. Solicitudes con Fetch.
2. Verificación de respuestas HTTP.
3. Parseo de JSON y manejo de errores.

## 14. Promesas

Las promesas representan el éxito o fracaso de operaciones asíncronas, como solicitudes de red. // MEJORA: Agregada para complementar Fetch y preparar para async/await.

```javascript
// 1. Crear una promesa
const miPromesa = new Promise((resolve, reject) => {
    setTimeout(() => {
        const exito = true; // Cambia a false para simular error
        if (exito) {
            resolve('Operación exitosa');
        } else {
            reject('Error en la operación');
        }
    }, 2000);
});

// 2. Manejar la promesa
miPromesa
    .then(resultado => {
        console.log(resultado); // 'Operación exitosa'
    })
    .catch(error => {
        console.error(error); // 'Error en la operación'
    })
    .finally(() => {
        console.log('Promesa finalizada'); // Siempre se ejecuta
    });
```

Este ejemplo muestra creación y manejo de promesas con `.then`, `.catch` y `.finally`.

## 15. Async/Await

Async/await es azúcar sintáctico sobre promesas, haciendo el código asíncrono más legible. // MEJORA: Agregada para mostrar un enfoque moderno a asincronía.

```javascript
// 1. Función async que usa await
async function obtenerDatos() {
    try {
        const response = await fetch('https://api.ejemplo.com/data');
        if (!response.ok) {
            throw new Error('Error en la solicitud');
        }
        const data = await response.json();
        console.log('Datos:', data);
    } catch (error) {
        console.error('Error:', error);
    }
}

// 2. Llamar a la función async
obtenerDatos();
```

Este ejemplo integra Fetch con async/await, mejorando legibilidad y manejo de errores.

## 16. Módulos ES6

Los módulos organizan código en archivos separados usando `import`/`export`, promoviendo reutilización. // MEJORA: Agregada para cubrir modularidad en proyectos grandes.

```javascript
// Archivo: math.js
export const suma = (a, b) => a + b;
export const PI = 3.1416;

// Archivo: main.js
import { suma, PI } from './math.js';

console.log(suma(2, 3)); // 5
console.log(PI); // 3.1416
```

Ejecuta con `<script type="module">` en HTML o Node.js (.mjs).

## 17. Manejo de Errores Avanzado

Errores personalizados mejoran la depuración en aplicaciones robustas. // MEJORA: Agregada para expandir manejo de errores.

```javascript
// 1. Error personalizado
class ErrorPersonalizado extends Error {
    constructor(mensaje) {
        super(mensaje);
        this.name = 'ErrorPersonalizado';
    }
}

// 2. Lanzar y capturar
function validarEntrada(entrada) {
    if (typeof entrada !== 'number') {
        throw new ErrorPersonalizado('Entrada no es número');
    }
    return entrada * 2;
}

try {
    console.log(validarEntrada('texto')); // Lanza error
} catch (error) {
    if (error instanceof ErrorPersonalizado) {
        console.error('Error específico:', error.message);
    } else {
        console.error('Error general:', error);
    }
}
```

Este ejemplo muestra errores tipados y manejo condicional.

## Autor

- **Matias Ignacio Paredes Marquez** - Perfil de GitHub

## Agradecimientos

Hecho con ❤️ por Matias Ignacio - https://github.com/Matignaciom

## Contacto

Si tienes preguntas o sugerencias, contáctame en mat.ignaciom95@gmail.com.

## Licencia

Este proyecto se distribuye bajo licencia de uso personal. Puedes usarlo con fines personales, pero no está permitido su uso comercial sin permiso del autor.
