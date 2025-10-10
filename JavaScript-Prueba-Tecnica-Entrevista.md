# Ejercicios Comunes de JavaScript para Pruebas Técnicas

Esta guía exhaustiva incluye 30 ejercicios de JavaScript frecuentemente utilizados en entrevistas técnicas para roles de desarrollo web. Basados en patrones comunes de plataformas como LeetCode, HackerRank y listas de preguntas de entrevistas (por ejemplo, de InterviewBit y GeeksforGeeks), estos ejercicios cubren temas esenciales como tipos de datos, operadores, scope, funciones, closures, asincronía y manipulación de datos. Cada ejercicio incluye un enunciado claro, una solución con código comentado y explicaciones detalladas en español para facilitar el aprendizaje.

Los ejercicios están categorizados por nivel de complejidad. Practica resolviéndolos antes de ver las soluciones. Usa un entorno como JSFiddle o Node.js para probar el código.

## Categoría 1: Fundamentos de Tipos y Operadores

Estos ejercicios evalúan el conocimiento básico para evitar errores comunes como la coerción implícita.

1. **Ejercicio: Identifica los tipos de datos en JavaScript.**  
   Enunciado: Enumera y describe los tipos de datos primitivos y no primitivos en JavaScript. Proporciona ejemplos y explica cómo verificar el tipo de una variable. Incluye un código que demuestre el uso de `typeof`.  
   Solución: Los tipos primitivos incluyen String, Number, BigInt, Boolean, Undefined, Null y Symbol. No primitivos: Object (arrays, funciones, objetos). `typeof` verifica tipos, pero `typeof null` es "object" por error histórico.  
   ```javascript:disable-run
   let str = "Hola"; // typeof str -> "string"
   let num = 42; // "number"
   let undef; // "undefined"
   let obj = {}; // "object"
   console.log(typeof null); // "object" (bug)
   ```  
   Explicación: Los primitivos son inmutables y pasados por valor; los objetos por referencia. Esto es clave en entrevistas para discutir memoria y mutabilidad.

2. **Ejercicio: Diferencia entre == y ===.**  
   Enunciado: Escribe un código que demuestre la diferencia entre los operadores == y ===. Incluye ejemplos con números, strings y booleanos, y explica la coerción implícita.  
   Solución: `==` coerce tipos (conversión automática), `===` no.  
   ```javascript
   console.log(5 == "5"); // true (coerción)
   console.log(5 === "5"); // false (tipos diferentes)
   console.log(true == 1); // true
   console.log(true === 1); // false
   ```  
   Explicación: La coerción puede llevar a bugs inesperados, como en comparaciones de inputs de usuario. En pruebas, a menudo piden ejemplos de falsy/truthy valores relacionados.

3. **Ejercicio: Maneja NaN en JavaScript.**  
   Enunciado: Explica qué es NaN y escribe una función que verifique si un valor es NaN usando isNaN y Number.isNaN. Demuestra diferencias.  
   Solución: NaN significa "Not a Number", resultado de operaciones inválidas como 0/0.  
   ```javascript
   function checkNaN(value) {
     return isNaN(value); // coerce
   }
   console.log(checkNaN("foo")); // true
   console.log(Number.isNaN("foo")); // false (no coerce)
   console.log(isNaN(NaN)); // true
   ```  
   Explicación: `isNaN` coerce, `Number.isNaN` es estricto. Útil en validaciones numéricas.

## Tabla de Comparación: Operadores de Igualdad y Coerción

| Operador | Descripción                  | Ejemplo     | Resultado | Notas                                      |
|----------|------------------------------|-------------|-----------|--------------------------------------------|
| ==      | Igualdad suelta con coerción | 5 == "5"   | true     | Convierte tipos automáticamente, riesgoso. |
| ===     | Igualdad estricta            | 5 === "5"  | false    | Compara valor y tipo, recomendado.         |
| !=      | Desigualdad suelta           | 5 != "5"   | false    | Similar a == pero negado.                  |
| !==     | Desigualdad estricta         | 5 !== "5"  | true     | Preferido en prácticas modernas.           |

## Categoría 2: Scope, Hoisting y Variables

Estos temas evalúan cómo JS maneja variables en runtime.

4. **Ejercicio: Explica el hoisting.**  
   Enunciado: Escribe un código que muestre hoisting con variables (var) y funciones. Explica por qué no afecta a let/const.  
   Solución: Hoisting eleva declaraciones al tope.  
   ```javascript
   console.log(x); // undefined (hoisted pero no inicializado)
   var x = 10;
   hoistedFunc(); // "Funciona"
   function hoistedFunc() { console.log("Funciona"); }
   // console.log(y); // Error (TDZ para let)
   let y = 20;
   ```  
   Explicación: Solo declaraciones se hoistean; inicializaciones no. let/const tienen TDZ para prevenir accesos prematuros.

5. **Ejercicio: Diferencia entre var, let y const.**  
   Enunciado: Implementa un código que demuestre scope y reasignación. Incluye TDZ.  
   Solución:  
   ```javascript
   if (true) {
     var a = 1; // accesible fuera
     let b = 2; // solo en bloque
   }
   console.log(a); // 1
   // console.log(b); // Error
   ```  
   Explicación: `var` permite hoisting completo y scope function/global. `let` block-scope, actualizable. `const` inmutable (pero objetos internos sí). En loops, `var` causa bugs por scope amplio.

6. **Ejercicio: Valores truthy y falsy.**  
   Enunciado: Escribe una función que clasifique valores como truthy o falsy. Lista ejemplos comunes.  
   Solución: Falsy: false, 0, "", null, undefined, NaN. Truthy: resto.  
   ```javascript
   function isTruthy(val) {
     return !!val; // doble negación para boolean
   }
   console.log(isTruthy("")); // false
   console.log(isTruthy("hola")); // true
   ```  
   Explicación: Crucial para condicionales if/while.

## Tabla de Comparación: var vs let vs const

| Característica | var            | let            | const          |
|----------------|----------------|----------------|----------------|
| Scope         | Function/global| Block          | Block          |
| Hoisting      | Sí (undefined) | Sí (TDZ)       | Sí (TDZ)       |
| Reasignación  | Sí             | Sí             | No             |
| Redeclaración | Sí             | No             | No             |
| Ejemplo común | Bucles legacy  | Bucles modernos| Constantes como PI |

## Categoría 3: Funciones Avanzadas y Asincronía

Estos ejercicios simulan problemas en apps web.

7. **Ejercicio: Closures en JavaScript.**  
   Enunciado: Crea una closure que mantenga un contador privado. Explica su utilidad.  
   Solución:  
   ```javascript
   function contador() {
     let count = 0;
     return function() { return ++count; };
   }
   let inc = contador();
   console.log(inc()); // 1
   console.log(inc()); // 2
   ```  
   Explicación: Closures retienen variables del scope padre post-ejecución. Útil para encapsulación.

8. **Ejercicio: Funciones callback.**  
   Enunciado: Implementa una función que acepte un callback para procesar un array.  
   Solución:  
   ```javascript
   function procesar(arr, cb) {
     arr.forEach(cb);
   }
   procesar([1,2,3], num => console.log(num * 2)); // 2,4,6
   ```  
   Explicación: Callbacks permiten asincronía básica.

9. **Ejercicio: Promises.**  
   Enunciado: Crea una promise que resuelva o rechace basado en un condicional.  
   Solución:  
   ```javascript
   let prom = new Promise((resolve, reject) => {
     let success = true;
     if (success) resolve("Éxito");
     else reject("Error");
   });
   prom.then(res => console.log(res)).catch(err => console.log(err));
   ```  
   Explicación: Maneja asincronía mejor que callbacks.

10. **Ejercicio: Async/await.**  
    Enunciado: Reescribe una promise con async/await.  
    Solución:  
    ```javascript
    async function fetchData() {
      try {
        let res = await new Promise(r => setTimeout(() => r("Datos"), 1000));
        console.log(res);
      } catch (err) { console.log(err); }
    }
    fetchData();
    ```  
    Explicación: Hace código asíncrono más legible.

11. **Ejercicio: setTimeout.**  
    Enunciado: Usa setTimeout para delayar una función. Explica closures implícitos.  
    Solución:  
    ```javascript
    setTimeout(() => console.log("Delayed"), 2000);
    ```  
    Explicación: No bloquea el thread principal.

12. **Ejercicio: Elimina duplicados de un array.**  
    Enunciado: Escribe una función para remover duplicados.  
    Solución:  
    ```javascript
    function removeDuplicates(arr) {
      return [...new Set(arr)];
    }
    console.log(removeDuplicates([1,2,2,3])); // [1,2,3]
    ```  
    Explicación: Set elimina uniques automáticamente.

13. **Ejercicio: Keyword 'this'.**  
    Enunciado: Explica 'this' en diferentes contextos con código.  
    Solución:  
    ```javascript
    const obj = { name: "Juan", greet: function() { console.log(this.name); } };
    obj.greet(); // "Juan"
    ```  
    Explicación: 'this' refiere al objeto invocador.

14. **Ejercicio: Call, apply, bind.**  
    Enunciado: Usa estos métodos para cambiar 'this'.  
    Solución:  
    ```javascript
    function greet() { console.log(this.name); }
    let person = { name: "Ana" };
    greet.call(person); // "Ana"
    greet.apply(person); // "Ana" (args en array)
    let bound = greet.bind(person);
    bound(); // "Ana"
    ```  
    Explicación: Controlan contexto de ejecución.

15. **Ejercicio: IIFE (Immediately Invoked Function Expression).**  
    Enunciado: Crea una IIFE para encapsular variables.  
    Solución:  
    ```javascript
    (function() {
      let private = "Secreto";
      console.log(private);
    })();
    ```  
    Explicación: Ejecuta inmediatamente, útil para scopes privados.

16. **Ejercicio: Higher-order functions.**  
    Enunciado: Crea una función que retorne otra función.  
    Solución:  
    ```javascript
    function multiplier(factor) {
      return num => num * factor;
    }
    let double = multiplier(2);
    console.log(double(5)); // 10
    ```  
    Explicación: Funciones como valores de primera clase.

17. **Ejercicio: Passed by value vs reference.**  
    Enunciado: Demuestra con código.  
    Solución:  
    ```javascript
    let num = 10;
    let copy = num;
    num = 20;
    console.log(copy); // 10 (value)
    let obj = { val: 10 };
    let ref = obj;
    obj.val = 20;
    console.log(ref.val); // 20 (reference)
    ```  
    Explicación: Primitivos por valor, objetos por referencia.

18. **Ejercicio: Strict mode.**  
    Enunciado: Activa strict mode y muestra un error común.  
    Solución:  
    ```javascript
    "use strict";
    // x = 10; // Error: undeclared
    ```  
    Explicación: Evita errores silenciosos.

19. **Ejercicio: Coerción implícita.**  
    Enunciado: Explica con ejemplos como 3 + 2 + "7".  
    Solución: Resultado: "57". Explicación: + con strings concatena.

20. **Ejercicio: Null vs Undefined.**  
    Enunciado: Diferencia con código.  
    Solución: Undefined: no asignado. Null: asignado intencionalmente como vacío.  
    ```javascript
    let undef;
    console.log(undef); // undefined
    let nul = null;
    console.log(nul); // null
    ```  
    Explicación: Null para "sin valor", undefined para "no inicializado".

## Categoría 4: Ejercicios Adicionales Avanzados

Estos 10 ejercicios adicionales se centran en temas como manipulación de arrays, objetos, eventos y optimización, comunes en entrevistas intermedias/avanzadas.

21. **Ejercicio: Flatten un array anidado.**  
    Enunciado: Escribe una función que aplane un array multidimensional.  
    Solución:  
    ```javascript
    function flatten(arr) {
      return arr.reduce((acc, val) => Array.isArray(val) ? acc.concat(flatten(val)) : acc.concat(val), []);
    }
    console.log(flatten([1, [2, [3]], 4])); // [1,2,3,4]
    ```  
    Explicación: Usa recursión con reduce para manejar anidamientos arbitrarios. Común en procesamiento de datos.

22. **Ejercicio: Implementa debounce.**  
    Enunciado: Crea una función debounce para limitar ejecuciones frecuentes (ej: en eventos de scroll).  
    Solución:  
    ```javascript
    function debounce(func, delay) {
      let timeout;
      return (...args) => {
        clearTimeout(timeout);
        timeout = setTimeout(() => func(...args), delay);
      };
    }
    const debouncedLog = debounce(() => console.log("Ejecutado"), 300);
    ```  
    Explicación: Previene llamadas excesivas, útil en optimización de UI.

23. **Ejercicio: Curry una función.**  
    Enunciado: Implementa currying para una función que suma tres números.  
    Solución:  
    ```javascript
    function currySum(a) {
      return (b) => (c) => a + b + c;
    }
    console.log(currySum(1)(2)(3)); // 6
    ```  
    Explicación: Transforma funciones en secuencias de funciones unarias, común en programación funcional.

24. **Ejercicio: Detecta palíndromos.**  
    Enunciado: Escribe una función que verifique si una string es un palíndromo, ignorando mayúsculas y espacios.  
    Solución:  
    ```javascript
    function isPalindrome(str) {
      const cleaned = str.toLowerCase().replace(/\s/g, '');
      return cleaned === cleaned.split('').reverse().join('');
    }
    console.log(isPalindrome("A man a plan a canal Panama")); // true
    ```  
    Explicación: Manipulación de strings, frecuente en algoritmos básicos.

25. **Ejercicio: Merge dos objetos.**  
    Enunciado: Implementa una función para mergear objetos, priorizando el segundo.  
    Solución:  
    ```javascript
    function mergeObjects(obj1, obj2) {
      return { ...obj1, ...obj2 };
    }
    console.log(mergeObjects({a:1}, {b:2, a:3})); // {a:3, b:2}
    ```  
    Explicación: Usa spread operator para fusión shallow; discute deep merge si es necesario.

26. **Ejercicio: Event bubbling vs capturing.**  
    Enunciado: Explica la diferencia y demuestra con addEventListener.  
    Solución: Bubbling: de hijo a padre; Capturing: de padre a hijo.  
    ```javascript
    document.getElementById('child').addEventListener('click', () => console.log('Child'), true); // capturing
    ```  
    Explicación: El tercer parámetro de addEventListener controla la fase. Crucial para manejo de eventos DOM.

27. **Ejercicio: Implementa un throttle.**  
    Enunciado: Crea una función throttle para ejecutar a intervalos fijos.  
    Solución:  
    ```javascript
    function throttle(func, limit) {
      let lastCall = 0;
      return (...args) => {
        const now = Date.now();
        if (now - lastCall >= limit) {
          func(...args);
          lastCall = now;
        }
      };
    }
    const throttledLog = throttle(() => console.log("Ejecutado"), 1000);
    ```  
    Explicación: Similar a debounce, pero asegura ejecuciones periódicas.

28. **Ejercicio: Reverse un array sin mutarlo.**  
    Enunciado: Invierte un array sin modificar el original.  
    Solución:  
    ```javascript
    function reverseArray(arr) {
      return [...arr].reverse();
    }
    const original = [1,2,3];
    console.log(reverseArray(original)); // [3,2,1]
    console.log(original); // [1,2,3]
    ```  
    Explicación: Usa spread para copia inmutable, buena práctica en React/Redux.

29. **Ejercicio: Fetch API básica.**  
    Enunciado: Escribe una función asíncrona para fetch data de una API.  
    Solución:  
    ```javascript
    async function fetchData(url) {
      try {
        const response = await fetch(url);
        return await response.json();
      } catch (error) {
        console.error(error);
      }
    }
    fetchData('https://api.example.com/data').then(data => console.log(data));
    ```  
    Explicación: Manejo de APIs, común en frontend moderno.

30. **Ejercicio: Memoización.**  
    Enunciado: Implementa memoización para una función costosa como Fibonacci.  
    Solución:  
    ```javascript
    function memoize(fn) {
      const cache = {};
      return (n) => {
        if (n in cache) return cache[n];
        return cache[n] = fn(n);
      };
    }
    const fib = memoize(n => n <= 1 ? n : fib(n-1) + fib(n-2));
    console.log(fib(10)); // 55
    ```  
    Explicación: Cachea resultados para optimizar llamadas recursivas.

## Recursos Recomendados
- Practica en plataformas como LeetCode o freeCodeCamp.
- Para más profundidad, consulta MDN Web Docs para referencias oficiales.
```
