# JavaScript Esencial para Aprender React

Este repositorio es una guía condensada y detallada de JavaScript, enfocada en los conceptos esenciales que necesitas dominar antes de sumergirte en React. React es una biblioteca de JavaScript para construir interfaces de usuario interactivas, y se basa fuertemente en características modernas de JavaScript (ES6+). Esta guía selecciona y adapta los temas clave de la guía completa *JavaScript Mastery: Desde lo Fundamental hasta lo Avanzado*, eliminando lo innecesario y enfatizando aspectos relevantes para React, como funciones flecha, desestructuración, manejo de arrays, promesas y modularidad.

Si eres principiante en JavaScript o quieres refrescar tus conocimientos específicamente para React, esta guía te proporcionará explicaciones detalladas, ejemplos prácticos y razones por las que cada concepto es crucial en el contexto de React. El objetivo es facilitar el aprendizaje paso a paso, con énfasis en la comprensión profunda para que puedas aplicar estos conceptos directamente en componentes React.

**Consejos para el aprendizaje**:
- Prueba todos los ejemplos en la consola del navegador (presiona F12 y ve a la pestaña "Console") o en herramientas en línea como CodeSandbox, que también soporta React.
- Entiende el "por qué" detrás de cada concepto: React premia el código limpio, inmutable y eficiente.
- Practica escribiendo pequeños snippets y modifícalos para ver qué pasa.
- Recuerda: JavaScript es el lenguaje base de React, así que dominarlo te ahorrará frustraciones al lidiar con estados, props y hooks.

Este trabajo se publica bajo una Licencia Creative Commons Atribución-NoComercial 4.0 Internacional por Matías Ignacio Paredes Márquez. Para más información, visita: [Licencia Creative Commons](https://creativecommons.org/licenses/by-nc/4.0/).

## 1. Variables y Tipos de Datos

En JavaScript, las variables almacenan datos que puedes usar y manipular en tu código. En React, las variables son fundamentales para manejar estados (state), propiedades (props) y datos dinámicos en componentes. Usamos principalmente `let` y `const` porque promueven un código más seguro y predecible, evitando errores comunes como redeclaraciones accidentales o fugas de variables. Evita `var` en código moderno, ya que tiene un ámbito (scope) más amplio que puede causar bugs en aplicaciones complejas como las de React.

### Diferencias clave entre `let` y `const`:
- **`let`**: Permite declarar variables que pueden cambiar de valor. Útil para contadores o valores que se actualizan, como un estado en React que cambia con interacciones del usuario.
- **`const`**: Declara constantes que no se pueden reasignar después de su inicialización. Ideal para valores fijos, como configuraciones o props en componentes funcionales. Nota: Si `const` apunta a un objeto o array, puedes modificar sus propiedades internas, pero no reasignar la variable completa (esto fomenta la inmutabilidad, un principio clave en React para optimizar renderizados).

Ejemplo básico:
```javascript
let contador = 0; // Variable que puede cambiar
contador = 1; // OK, se actualiza
console.log(contador); // 1

const PI = 3.1416; // Constante, no cambia
// PI = 3.14; // Error: No se puede reasignar
console.log(PI); // 3.1416
```

### Ámbito (Scope) de las variables:
El ámbito define dónde una variable es accesible. `let` y `const` tienen ámbito de bloque, lo que significa que solo existen dentro de llaves `{}` (como en `if`, `for` o funciones). Esto previene "fugas" de variables, un problema común en apps React donde los componentes son funciones encapsuladas.

Ejemplo de ámbito:
```javascript
if (true) {
  let x = 10; // Solo accesible dentro del if
}
console.log(x); // Error: x is not defined (no accesible fuera)

const config = { apiUrl: 'https://api.example.com' }; // Constante con objeto
config.apiUrl = 'https://newapi.com'; // OK, modificamos propiedad interna
// config = {}; // Error: No se puede reasignar la variable
```

**Por qué es importante para React**: En React, usas `const` para declarar componentes funcionales (e.g., `const MiComponente = () => { ... }`) y estados iniciales. El ámbito de bloque ayuda a mantener el código modular y evita conflictos entre componentes.

**Ejercicio de práctica**: Crea una variable `let` para un contador y actualízala en un bucle. Luego, intenta accederla fuera del bucle y observa el error.

## 2. Funciones

Las funciones son bloques de código reutilizables que realizan tareas específicas. En React, las funciones son el corazón de los componentes funcionales (introducidos en React 16.8 con hooks). Aprende a escribir funciones limpias, ya que las usarás para manejar eventos, efectos secundarios y lógica de renderizado. Las funciones flecha son especialmente útiles porque no crean un nuevo contexto `this`, lo que evita problemas en callbacks.

### Funciones Flecha (Arrow Functions):
Son una sintaxis concisa de ES6+. No tienen su propio `this`, lo que las hace perfectas para handlers de eventos en React (e.g., `onClick={() => handleClick()}`).

Ejemplo:
```javascript
const sumar = (a, b) => a + b; // Función flecha simple
console.log(sumar(2, 3)); // 5

const saludar = nombre => `Hola, ${nombre}`; // Con un parámetro, sin paréntesis
console.log(saludar('React')); // Hola, React
```

Si la función tiene más de una línea, usa llaves y `return` explícito:
```javascript
const calcular = (a, b) => {
  const suma = a + b;
  return suma * 2;
};
console.log(calcular(1, 2)); // 6
```

### Funciones como Argumentos (Callbacks):
Las callbacks son funciones pasadas como argumentos a otras funciones. En React, las usas en hooks como `useEffect` o en métodos como `array.map`.

Ejemplo:
```javascript
function operacion(a, b, callback) {
  return callback(a, b); // Ejecuta la callback
}

const resultado = operacion(5, 3, (x, y) => x - y); // Callback flecha
console.log(resultado); // 2
```

### Parámetros Predeterminados:
Permiten valores por defecto si no se pasa un argumento. En React, útil para props opcionales en componentes.

Ejemplo:
```javascript
function greeting(nombre = 'Usuario') {
  return `Hola, ${nombre}`;
}
console.log(greeting()); // Hola, Usuario
console.log(greeting('Matías')); // Hola, Matías
```

**Por qué es importante para React**: Los componentes React son funciones que reciben props y retornan JSX. Las flechas simplifican la sintaxis, y las callbacks permiten manejar asincronía y efectos.

**Ejercicio de práctica**: Escribe una función flecha que tome un array y use una callback para filtrarlo. Prueba pasándole diferentes callbacks.

## 3. Arreglos y Métodos

Los arrays almacenan listas de datos. En React, los usas para renderizar listas dinámicas (e.g., con `map` para generar elementos `<li>`). Enfócate en métodos inmutables que retornan nuevos arrays, ya que React optimiza basándose en cambios detectables sin mutaciones directas.

### Declaración y Manipulación Básica:
Crea arrays con corchetes `[]`. Puedes agregar/eliminar elementos, pero en React prefiere métodos que no muten el original.

Ejemplo:
```javascript
let frutas = ['manzana', 'banana', 'naranja']; // Declaración
frutas.push('uva'); // Mutación: Agrega al final (evita en React si posible)
console.log(frutas); // ['manzana', 'banana', 'naranja', 'uva']

const nuevasFrutas = [...frutas, 'pera']; // Inmutable: Spread para nuevo array
console.log(nuevasFrutas); // ['manzana', 'banana', 'naranja', 'uva', 'pera']
```

### Métodos Clave:
- **`map`**: Transforma cada elemento y retorna un nuevo array. En React, usa para renderizar listas: `frutas.map(fruta => <li key={fruta}>{fruta}</li>)`.

Ejemplo:
```javascript
const numeros = [1, 2, 3];
const dobles = numeros.map(num => num * 2);
console.log(dobles); // [2, 4, 6] (nuevo array, original intacto)
```

- **`filter`**: Retorna un nuevo array con elementos que cumplan una condición. Útil para filtrar datos en estados React.

Ejemplo:
```javascript
const pares = numeros.filter(num => num % 2 === 0);
console.log(pares); // [2]
```

- **`reduce`**: Reduce el array a un solo valor acumulando. Ejemplo: Calcular sumas o objetos agregados.

Ejemplo:
```javascript
const suma = numeros.reduce((acc, num) => acc + num, 0); // acc inicia en 0
console.log(suma); // 6
```

**Por qué es importante para React**: Renderizar listas eficientemente con `map`, actualizar estados con `filter` o `reduce` sin mutar, y usar keys para optimización.

**Ejercicio de práctica**: Toma un array de objetos (e.g., [{id:1, nombre:'A'}]) y usa `map` para crear un nuevo array con nombres en mayúsculas. Luego, filtra por id par.

## 4. Objetos y Desestructuración

Los objetos almacenan datos en pares clave-valor. En React, representan props, estados y configuraciones. La desestructuración y spread operator facilitan el manejo sin repetición de código.

### Objetos Básicos:
Crea con llaves `{}`. Accede con punto `.` o corchetes `[]`.

Ejemplo:
```javascript
const persona = {
  nombre: 'Juan',
  edad: 30,
  ciudad: 'México'
};
console.log(persona.nombre); // Juan

persona.edad = 31; // Modificar (mutación, usa con cuidado en React)
console.log(persona.edad); // 31
```

### Desestructuración (Destructuring):
Extrae propiedades en variables. En React, común en props: `function MiComponente({ nombre, edad }) { ... }`.

Ejemplo:
```javascript
const { nombre, edad } = persona;
console.log(nombre); // Juan
console.log(edad); // 31
```

### Spread Operator (`...`):
Copia o combina objetos/arrays inmutablemente. En React, para actualizar estados: `setState({ ...prevState, newKey: value })`.

Ejemplo:
```javascript
const nuevaPersona = { ...persona, trabajo: 'Desarrollador' };
console.log(nuevaPersona); // { nombre: 'Juan', edad: 31, ciudad: 'México', trabajo: 'Desarrollador' }
```

**Por qué es importante para React**: Props son objetos; desestructuración limpia el código; spread mantiene inmutabilidad para hooks como `useState`.

**Ejercicio de práctica**: Desestructura un objeto anidado (e.g., { usuario: { nombre: 'A' } }) y usa spread para agregar una propiedad.

## 5. Clases (Básico)

Aunque React favorece componentes funcionales con hooks, entiende clases para componentes legacy o ciclos de vida. Las clases permiten herencia y métodos.

### Declaración Básica:
Usa `class` con constructor para inicializar.

Ejemplo:
```javascript
class Componente {
  constructor(props) {
    this.props = props;
  }
  render() {
    return `Hola, ${this.props.nombre}`;
  }
}

const miComponente = new Componente({ nombre: 'React' });
console.log(miComponente.render()); // Hola, React
```

### Herencia:
Extiende clases para reutilizar código.

Ejemplo:
```javascript
class Boton extends Componente {
  constructor(props) {
    super(props); // Llama al constructor padre
  }
  handleClick() {
    console.log('Clic en', this.props.nombre);
  }
}
```

**Por qué es importante para React**: Componentes de clase usan `this.state` y métodos como `componentDidMount`. Hooks los reemplazan, pero saber clases ayuda a leer código viejo.

**Ejercicio de práctica**: Crea una clase `Animal` y extiéndela a `Perro` con un método adicional.

## 6. Promesas y Async/Await

JavaScript es asíncrono para operaciones como fetches de API. En React, usa en `useEffect` para cargar datos.

### Promesas:
Representan un valor futuro. Maneja con `.then` y `.catch`.

Ejemplo:
```javascript
const miPromesa = new Promise((resolve, reject) => {
  setTimeout(() => resolve('Datos cargados'), 1000); // Simula delay
});

miPromesa
  .then(data => console.log(data)) // Datos cargados
  .catch(error => console.error(error));
```

### Async/Await:
Sintaxis más legible sobre promesas. Usa en funciones `async`.

Ejemplo:
```javascript
async function fetchData() {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/todos/1'); // API de prueba
    const data = await response.json();
    console.log(data); // { userId: 1, id: 1, title: '...', completed: false }
  } catch (error) {
    console.error('Error:', error);
  }
}

fetchData();
```

**Por qué es importante para React**: Carga datos asíncronos en componentes sin bloquear el renderizado. Integra con `useEffect(async () => { ... })`.

**Ejercicio de práctica**: Crea una función async que fetch un API real (como JSONPlaceholder) y maneja errores.

## 7. Módulos ES6

Divide código en archivos reutilizables con `import` y `export`. En React, cada componente es un módulo.

### Exportar:
```javascript
// math.js
export const suma = (a, b) => a + b;
export default function multiplicar(a, b) { return a * b; } // Export default
```

### Importar:
```javascript
// app.js
import { suma } from './math.js';
import multiplicar from './math.js'; // Para default

console.log(suma(2, 3)); // 5
console.log(multiplicar(4, 5)); // 20
```

**Por qué es importante para React**: Apps React son modulares; importas componentes, hooks y utils.

**Ejercicio de práctica**: Crea dos archivos (simula en consola) y exporta/importa funciones.

## 8. Manejo de Eventos y DOM Básico

Entiende cómo JavaScript interactúa con el DOM, aunque React lo abstrae con JSX.

Ejemplo en HTML/JS puro:
```html
<button id="miBoton">Clic</button>
<script>
  const boton = document.getElementById('miBoton');
  boton.addEventListener('click', () => console.log('Clic detectado'));
</script>
```

En React: `<button onClick={() => handleClick()}>Clic</button>`

**Por qué es importante para React**: Handlers de eventos usan funciones flecha para props como `onClick`.

**Ejercicio de práctica**: Agrega un event listener a un input para loggear cambios.

## 9. Plantillas Literales (Template Literals)

Strings dinámicos con backticks `` ` `` y `${}`. En React, para JSX interpolado.

Ejemplo:
```javascript
const nombre = 'React';
const mensaje = `¡Bienvenido a ${nombre}! Versión ${16 + 2}`;
console.log(mensaje); // ¡Bienvenido a React! Versión 18
```

**Por qué es importante para React**: JSX usa interpolación para variables en markup.

**Ejercicio de práctica**: Crea un string con variables y condicionales dentro (e.g., `${cond ? 'A' : 'B'}`).

## Consejos Finales para Transicionar a React

- **Inmutabilidad**: Siempre crea nuevos arrays/objetos en lugar de mutar. Usa spread, `map`, etc.
- **Practica en entornos React**: Usa Create React App o CodeSandbox para aplicar estos conceptos en componentes reales.
- **Siguiente paso**: Lee la documentación oficial de React (react.dev). Comienza con componentes funcionales y hooks como `useState` y `useEffect`.
- **Errores comunes**: Olvidar keys en listas `map`, mutar estados directamente, o no manejar asincronía correctamente.
- **Recursos adicionales**: MDN Web Docs para JS profundo, y tutoriales de React en español.

## Autor

- **Matías Ignacio Paredes Márquez** - [Perfil de GitHub](https://github.com/Matignaciom)

## Agradecimientos

Hecho con ❤️ por Matías Ignacio - https://github.com/Matignaciom

## Contacto

Si tienes preguntas o sugerencias, contáctame en mat.ignaciom95@gmail.com.

## Licencia

Este proyecto se distribuye bajo licencia de uso personal. Puedes usarlo con fines personales, pero no está permitido su uso comercial sin permiso del autor.
