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
var edad = 18;

if (edad >= 18) {
  console.log("Eres mayor de edad");
} else {
  console.log("Eres menor de edad");
}
```

### 4. Bucles

Los bucles permiten repetir un bloque de código varias veces.

#### Bucle `for`:

```javascript
for (var i = 0; i < 5; i++) {
  console.log("Iteración " + i);
}
```

#### Bucle `while`:

```javascript
var contador = 0;
while (contador < 3) {
  console.log("Iteración " + contador);
  contador++;
}
```

### 5. Funciones

Las funciones son bloques de código reutilizables que pueden recibir argumentos y devolver valores.

```javascript
function suma(a, b) {
  return a + b;
}

var resultado = suma(2, 3);
console.log("Resultado: " + resultado); // Resultado: 5
```

### 6. Arreglos

Los arreglos almacenan conjuntos de valores en una sola variable.

```javascript
var frutas = ["manzana", "banana", "naranja"];
console.log(frutas[0]); // manzana

frutas.push("uva"); // Agregar un elemento al final
console.log(frutas); // ["manzana", "banana", "naranja", "uva"]
```

### 7. Objetos

Los objetos son estructuras de datos que almacenan propiedades y valores.

```javascript
var persona = {
  nombre: "Juan",
  edad: 30,
  ciudad: "México"
};

console.log(persona.nombre); // Juan
console.log(persona.edad);   // 30
```

### 8. Arreglos Multidimensionales

Los arreglos multidimensionales son arreglos que contienen otros arreglos, lo que permite representar datos en una estructura más compleja.

```javascript
var matriz = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];

console.log(matriz[0][1]); // Acceder al valor 2
```

### 9. Métodos de Arreglos

JavaScript proporciona una variedad de métodos incorporados para manipular arreglos, como `push`, `pop`, `shift`, `unshift`, `splice`, `forEach` y más.

```javascript
var frutas = ["manzana", "banana", "naranja"];
frutas.push("uva");   // Agregar al final
frutas.pop();         // Eliminar del final
frutas.shift();       // Eliminar del inicio
frutas.unshift("pera"); // Agregar al inicio
```

### 10. Iteración de Objetos

Puedes iterar sobre las propiedades de un objeto utilizando bucles `for...in` o métodos como `Object.keys`.

```javascript
var persona = {
  nombre: "Juan",
  edad: 30,
  ciudad: "México"
};

for (var propiedad in persona) {
  console.log(propiedad + ": " + persona[propiedad]);
}
```

### 11. Clases y Programación Orientada a Objetos

JavaScript admite la programación orientada a objetos (POO). Puedes crear clases y objetos para organizar tu código de manera más estructurada.

```javascript
class Persona {
  constructor(nombre, edad) {
    this.nombre = nombre;
    this.edad = edad;
  }

  saludar() {
    console.log(`Hola, soy ${this.nombre} y tengo ${this.edad} años.`);
  }
}

var juan = new Persona("Juan", 25);
juan.saludar(); // Hola, soy Juan y tengo 25 años.
```

### 12. Manejo de Eventos

JavaScript se utiliza ampliamente para manejar eventos en aplicaciones web. Puedes adjuntar funciones a eventos como clics de botón, cambios de entrada, etc.

```javascript
var boton = document.getElementById("miBoton");
boton.addEventListener("click", function() {
  alert("Hiciste clic en el botón.");
});
```

### 13. AJAX y Fetch

JavaScript permite realizar solicitudes de red asíncronas para obtener datos de servidores web. La API Fetch es comúnmente utilizada para este propósito.

```javascript
fetch('https://api.ejemplo.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error: ' + error));
```

Estos son algunos de los conceptos fundamentales que te ayudarán a comprender y utilizar JavaScript de manera efectiva. JavaScript es un lenguaje poderoso y versátil que se utiliza en una variedad de contextos, incluyendo desarrollo web, aplicaciones móviles y más. Practicar y trabajar en proyectos te ayudará a fortalecer tus habilidades en JavaScript.

## Agradecimientos

Hecho con ❤️ por Matias Ignacio - https://github.com/Matignaciom
