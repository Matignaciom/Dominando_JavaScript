# 🚀 Guía Completa de TypeScript con React - De Cero a Master

## 🎯 Introducción

TypeScript es un superset de JavaScript que añade tipado estático opcional, lo que permite detectar errores en tiempo de desarrollo y mejorar la experiencia de desarrollo. Cuando se combina con React, TypeScript proporciona una base sólida para construir aplicaciones escalables y mantenibles con mejor autocompletado, refactoring seguro y documentación automática del código.

### ¿Qué aprenderás?
- ✅ Fundamentos de TypeScript desde cero
- ✅ Configuración de TypeScript con React
- ✅ Tipado de componentes, props y state
- ✅ Hooks tipados (useState, useEffect, useContext, etc.)
- ✅ Manejo de eventos y formularios con tipos
- ✅ Context API y Redux con TypeScript
- ✅ Patrones avanzados y mejores prácticas
- ✅ Testing con TypeScript y React
- ✅ Migración de JavaScript a TypeScript

### ¿Por qué TypeScript con React?
- 🛡️ **Detección temprana de errores**: Encuentra bugs antes de ejecutar el código
- 🔧 **Mejor experiencia de desarrollo**: Autocompletado inteligente y refactoring seguro
- 📚 **Documentación automática**: Los tipos sirven como documentación viva
- 🏗️ **Escalabilidad**: Facilita el mantenimiento de aplicaciones grandes
- 🤝 **Mejor colaboración**: Los tipos hacen el código más legible para el equipo

---

## 🚀 Configuración Inicial

### Prerrequisitos
- Node.js (versión 16 o superior)
- npm, yarn o pnpm
- Editor de código (VS Code altamente recomendado)
- Conocimientos básicos de JavaScript y React

### Crear un Nuevo Proyecto React con TypeScript

```bash
# Opción 1: Create React App con TypeScript
npx create-react-app mi-app-typescript --template typescript
cd mi-app-typescript
npm start

# Opción 2: Vite con TypeScript (más rápido)
npm create vite@latest mi-app-typescript -- --template react-ts
cd mi-app-typescript
npm install
npm run dev

# Opción 3: Next.js con TypeScript
npx create-next-app@latest mi-app-typescript --typescript
cd mi-app-typescript
npm run dev
```

### Agregar TypeScript a un Proyecto React Existente

```bash
# Instalar TypeScript y tipos
npm install --save-dev typescript @types/node @types/react @types/react-dom

# Crear archivo de configuración
npx tsc --init

# Renombrar archivos .js a .tsx/.ts
# App.js → App.tsx
# index.js → index.tsx
```

### Estructura de Proyecto Recomendada

```
mi-app-typescript/
├── public/
│   ├── index.html
│   └── favicon.ico
├── src/
│   ├── components/
│   │   ├── Header/
│   │   │   ├── Header.tsx
│   │   │   ├── Header.types.ts
│   │   │   └── index.ts
│   │   └── Button/
│   │       ├── Button.tsx
│   │       ├── Button.types.ts
│   │       └── index.ts
│   ├── pages/
│   │   ├── Home/
│   │   │   ├── Home.tsx
│   │   │   └── index.ts
│   │   └── About/
│   │       ├── About.tsx
│   │       └── index.ts
│   ├── hooks/
│   │   ├── useLocalStorage.ts
│   │   └── useApi.ts
│   ├── types/
│   │   ├── api.types.ts
│   │   ├── user.types.ts
│   │   └── index.ts
│   ├── utils/
│   │   ├── helpers.ts
│   │   └── constants.ts
│   ├── App.tsx
│   ├── App.css
│   ├── index.tsx
│   └── react-app-env.d.ts
├── tsconfig.json
├── package.json
└── README.md
```

### Configuración de tsconfig.json

```json
{
  "compilerOptions": {
    "target": "es5",
    "lib": [
      "dom",
      "dom.iterable",
      "es6"
    ],
    "allowJs": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "noFallthroughCasesInSwitch": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx",
    "baseUrl": "src",
    "paths": {
      "@components/*": ["components/*"],
      "@pages/*": ["pages/*"],
      "@types/*": ["types/*"],
      "@utils/*": ["utils/*"],
      "@hooks/*": ["hooks/*"]
    }
  },
  "include": [
    "src"
  ]
}
```

### Extensiones de VS Code Recomendadas
- TypeScript Importer
- ES7+ React/Redux/React-Native snippets
- TypeScript Hero
- Auto Rename Tag
- Prettier - Code formatter
- ESLint
- Bracket Pair Colorizer

---

## 📋 Tabla de Contenidos

1. [Fundamentos de TypeScript](#fundamentos-de-typescript)
2. [Tipos Básicos](#tipos-básicos)
3. [Interfaces y Types](#interfaces-y-types)
4. [Generics](#generics)
5. [Componentes Tipados](#componentes-tipados)
6. [Props con TypeScript](#props-con-typescript)
7. [State y Hooks Tipados](#state-y-hooks-tipados)
8. [Eventos y Formularios](#eventos-y-formularios)
9. [Context API con TypeScript](#context-api-con-typescript)
10. [Redux con TypeScript](#redux-con-typescript)
11. [Patrones Avanzados](#patrones-avanzados)
12. [Testing con TypeScript](#testing-con-typescript)
13. [Migración de JS a TS](#migración-de-js-a-ts)
14. [Ejercicios Prácticos](#ejercicios-prácticos)
15. [Troubleshooting](#troubleshooting)

---

## 🔧 Configuración Avanzada e Integración

### Configuración de tsconfig.json para React

```json
{
  "compilerOptions": {
    // Configuración básica
    "target": "ES2020",
    "lib": ["DOM", "DOM.Iterable", "ES6"],
    "allowJs": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "noFallthroughCasesInSwitch": true,
    
    // Configuración para React
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx",
    
    // Configuración de paths
    "baseUrl": "src",
    "paths": {
      "@/*": ["*"],
      "@components/*": ["components/*"],
      "@utils/*": ["utils/*"],
      "@types/*": ["types/*"],
      "@hooks/*": ["hooks/*"],
      "@services/*": ["services/*"]
    },
    
    // Configuración estricta adicional
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noImplicitReturns": true,
    "noImplicitAny": true,
    "strictNullChecks": true,
    "strictFunctionTypes": true,
    "strictBindCallApply": true,
    "strictPropertyInitialization": true,
    "noImplicitThis": true,
    "useUnknownInCatchVariables": true,
    "exactOptionalPropertyTypes": true,
    "noImplicitOverride": true,
    "noPropertyAccessFromIndexSignature": true,
    "noUncheckedIndexedAccess": true
  },
  "include": [
    "src/**/*",
    "src/**/*.tsx",
    "src/**/*.ts"
  ],
  "exclude": [
    "node_modules",
    "build",
    "dist",
    "**/*.test.ts",
    "**/*.test.tsx"
  ]
}
```

### Configuración de Vite con TypeScript

```typescript
// vite.config.ts
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import path from 'path'

export default defineConfig({
  plugins: [react()],
  resolve: {
    alias: {
      '@': path.resolve(__dirname, './src'),
      '@components': path.resolve(__dirname, './src/components'),
      '@utils': path.resolve(__dirname, './src/utils'),
      '@types': path.resolve(__dirname, './src/types'),
      '@hooks': path.resolve(__dirname, './src/hooks'),
      '@services': path.resolve(__dirname, './src/services'),
      '@assets': path.resolve(__dirname, './src/assets')
    }
  },
  server: {
    port: 3000,
    open: true
  },
  build: {
    outDir: 'dist',
    sourcemap: true,
    rollupOptions: {
      output: {
        manualChunks: {
          vendor: ['react', 'react-dom'],
          utils: ['lodash', 'date-fns']
        }
      }
    }
  }
})
```

### Configuración de ESLint y Prettier

```json
// .eslintrc.json
{
  "env": {
    "browser": true,
    "es2021": true
  },
  "extends": [
    "eslint:recommended",
    "@typescript-eslint/recommended",
    "plugin:react/recommended",
    "plugin:react-hooks/recommended",
    "plugin:@typescript-eslint/recommended-requiring-type-checking"
  ],
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "ecmaFeatures": {
      "jsx": true
    },
    "ecmaVersion": "latest",
    "sourceType": "module",
    "project": "./tsconfig.json"
  },
  "plugins": [
    "react",
    "@typescript-eslint",
    "react-hooks"
  ],
  "rules": {
    "react/react-in-jsx-scope": "off",
    "@typescript-eslint/no-unused-vars": "error",
    "@typescript-eslint/explicit-function-return-type": "warn",
    "@typescript-eslint/no-explicit-any": "error",
    "@typescript-eslint/prefer-const": "error",
    "react-hooks/rules-of-hooks": "error",
    "react-hooks/exhaustive-deps": "warn"
  },
  "settings": {
    "react": {
      "version": "detect"
    }
  }
}
```

```json
// .prettierrc
{
  "semi": true,
  "trailingComma": "es5",
  "singleQuote": true,
  "printWidth": 80,
  "tabWidth": 2,
  "useTabs": false,
  "bracketSpacing": true,
  "arrowParens": "avoid",
  "endOfLine": "lf"
}
```

---

## 🔤 Fundamentos de TypeScript

TypeScript es un superset de JavaScript desarrollado por Microsoft que añade tipado estático opcional. Se compila a JavaScript puro y puede ejecutarse en cualquier lugar donde JavaScript funcione.

### 1. ¿Qué es TypeScript?

**Características principales:**
- **Tipado estático**: Define tipos en tiempo de desarrollo
- **Compatibilidad**: Todo código JavaScript válido es TypeScript válido
- **Compilación**: Se transpila a JavaScript estándar
- **Herramientas**: Mejor soporte en IDEs y editores

```typescript
// JavaScript tradicional
function saludar(nombre) {
  return "Hola, " + nombre;
}

saludar(123); // Funciona pero puede no ser lo esperado

// TypeScript
function saludarTS(nombre: string): string {
  return "Hola, " + nombre;
}

saludarTS(123); // Error: Argument of type 'number' is not assignable to parameter of type 'string'
saludarTS("Ana"); // ✅ Correcto
```

### 2. Ventajas de TypeScript

- **Detección temprana de errores**: Los errores se detectan en tiempo de compilación, no en runtime
- **Mejor IntelliSense**: Autocompletado más preciso y sugerencias inteligentes
- **Refactoring seguro**: Cambios de código más confiables con menos riesgo de errores
- **Documentación viva**: Los tipos sirven como documentación del código
- **Escalabilidad**: Ideal para proyectos grandes y equipos de desarrollo
- **Mejor experiencia de desarrollo**: Navegación de código y debugging mejorados

```typescript
// Autocompletado inteligente
interface Usuario {
  id: number;
  nombre: string;
  email: string;
  activo: boolean;
}

function procesarUsuario(usuario: Usuario) {
  // El editor sugiere automáticamente: id, nombre, email, activo
  console.log(usuario.); // Autocompletado disponible
}

// Refactoring seguro
function cambiarNombreUsuario(usuario: Usuario, nuevoNombre: string) {
  usuario.nombre = nuevoNombre; // Si cambias 'nombre' por 'name' en la interfaz,
                                // TypeScript te avisará de todos los lugares que necesitas actualizar
}
```

### 3. Compilación de TypeScript

```bash
# Instalar TypeScript globalmente
npm install -g typescript

# Compilar un archivo específico
tsc archivo.ts

# Compilar en modo watch (observa cambios)
tsc --watch archivo.ts

# Compilar todo el proyecto
tsc

# Compilar con configuración específica
tsc --project tsconfig.json

# Compilar y ejecutar directamente
npx ts-node archivo.ts
```

---

## 🎨 Tipos Básicos

TypeScript incluye todos los tipos de JavaScript más algunos adicionales.

### 1. Tipos Primitivos

```typescript
// String
let nombre: string = "Ana";
let apellido: string = 'García';
let nombreCompleto: string = `${nombre} ${apellido}`;

// Number
let edad: number = 25;
let precio: number = 99.99;
let hexadecimal: number = 0xf00d;

// Boolean
let activo: boolean = true;
let completado: boolean = false;

// Undefined y Null
let indefinido: undefined = undefined;
let nulo: null = null;

// Any (evitar cuando sea posible)
let cualquierCosa: any = 42;
cualquierCosa = "ahora soy string";
cualquierCosa = true;
```

### 2. Arrays

```typescript
// Array de números
let numeros: number[] = [1, 2, 3, 4, 5];
let numerosAlt: Array<number> = [1, 2, 3, 4, 5];

// Array de strings
let frutas: string[] = ["manzana", "banana", "naranja"];

// Array mixto con union types
let mixto: (string | number)[] = ["texto", 42, "más texto"];

// Array de objetos
interface Producto {
  id: number;
  nombre: string;
  precio: number;
}

let productos: Producto[] = [
  { id: 1, nombre: "Laptop", precio: 999 },
  { id: 2, nombre: "Mouse", precio: 25 }
];
```

### 3. Objetos

```typescript
// Objeto simple
let persona: {
  nombre: string;
  edad: number;
  activo: boolean;
} = {
  nombre: "Carlos",
  edad: 30,
  activo: true
};

// Propiedades opcionales
let configuracion: {
  tema: string;
  idioma?: string; // Opcional
  notificaciones: boolean;
} = {
  tema: "oscuro",
  notificaciones: true
  // idioma es opcional, no es necesario incluirlo
};

// Propiedades readonly
let usuario: {
  readonly id: number;
  nombre: string;
} = {
  id: 1,
  nombre: "María"
};

// usuario.id = 2; // Error: Cannot assign to 'id' because it is a read-only property
usuario.nombre = "María José"; // ✅ Permitido
```

### 4. Union Types

```typescript
// Tipo que puede ser string o number
let id: string | number;
id = "abc123";
id = 123;
// id = true; // Error

// Función con union types
function formatearId(id: string | number): string {
  if (typeof id === "string") {
    return id.toUpperCase();
  }
  return id.toString();
}

// Union con tipos literales
type Estado = "cargando" | "exitoso" | "error";
let estadoActual: Estado = "cargando";
// estadoActual = "completado"; // Error: Type '"completado"' is not assignable to type 'Estado'
```

### 5. Literal Types

```typescript
// String literals
type Direccion = "norte" | "sur" | "este" | "oeste";
let direccion: Direccion = "norte";

// Number literals
type DadoValor = 1 | 2 | 3 | 4 | 5 | 6;
let resultado: DadoValor = 4;

// Boolean literals
type Confirmacion = true;
let confirmado: Confirmacion = true;
// let confirmado: Confirmacion = false; // Error
```

### 6. Enums

```typescript
// Enum numérico
enum Color {
  Rojo,    // 0
  Verde,   // 1
  Azul     // 2
}

let colorFavorito: Color = Color.Verde;
console.log(colorFavorito); // 1

// Enum con valores personalizados
enum EstadoHTTP {
  OK = 200,
  NotFound = 404,
  InternalServerError = 500
}

// Enum de strings
enum Tema {
  Claro = "light",
  Oscuro = "dark",
  Auto = "auto"
}

let temaActual: Tema = Tema.Oscuro;
console.log(temaActual); // "dark"
```

### 7. Tuple

```typescript
// Tuple básico
let coordenada: [number, number] = [10, 20];

// Tuple con diferentes tipos
let usuario: [string, number, boolean] = ["Ana", 25, true];

// Destructuring de tuples
let [nombre, edad, activo] = usuario;

// Tuple con elementos opcionales
let punto: [number, number, number?] = [1, 2]; // z es opcional

// Tuple con rest elements
let numeros: [number, ...string[]] = [1, "a", "b", "c"];
```

---

## 🏗️ Interfaces y Types

Las interfaces y types permiten definir la forma de los objetos y crear tipos reutilizables.

### 1. Interfaces Básicas

```typescript
// Interface simple
interface Persona {
  nombre: string;
  edad: number;
  email: string;
}

// Uso de la interface
const usuario: Persona = {
  nombre: "Laura",
  edad: 28,
  email: "laura@email.com"
};

// Interface con propiedades opcionales
interface Configuracion {
  tema: string;
  idioma?: string;
  notificaciones?: boolean;
}

const config: Configuracion = {
  tema: "oscuro"
  // idioma y notificaciones son opcionales
};
```

### 2. Propiedades Readonly

```typescript
interface Producto {
  readonly id: number;
  nombre: string;
  precio: number;
  readonly fechaCreacion: Date;
}

const producto: Producto = {
  id: 1,
  nombre: "Laptop",
  precio: 999,
  fechaCreacion: new Date()
};

// producto.id = 2; // Error: Cannot assign to 'id' because it is a read-only property
producto.precio = 899; // ✅ Permitido
```

### 3. Métodos en Interfaces

```typescript
interface Calculadora {
  sumar(a: number, b: number): number;
  restar(a: number, b: number): number;
  multiplicar?: (a: number, b: number) => number; // Método opcional
}

const miCalculadora: Calculadora = {
  sumar(a, b) {
    return a + b;
  },
  restar: (a, b) => a - b
  // multiplicar es opcional
};
```

### 4. Extending Interfaces

```typescript
interface Animal {
  nombre: string;
  edad: number;
}

interface Perro extends Animal {
  raza: string;
  ladrar(): void;
}

interface Gato extends Animal {
  color: string;
  maullar(): void;
}

const miPerro: Perro = {
  nombre: "Max",
  edad: 3,
  raza: "Labrador",
  ladrar() {
    console.log("¡Guau!");
  }
};
```

### 5. Index Signatures

```typescript
// Interface con index signature
interface Diccionario {
  [key: string]: string;
}

const traducciones: Diccionario = {
  "hello": "hola",
  "goodbye": "adiós",
  "thank you": "gracias"
};

// Interface más específica con index signature
interface UsuarioPorId {
  [id: number]: {
    nombre: string;
    email: string;
  };
}

const usuarios: UsuarioPorId = {
  1: { nombre: "Ana", email: "ana@email.com" },
  2: { nombre: "Carlos", email: "carlos@email.com" }
};
```

### 6. Type Aliases

```typescript
// Type alias básico
type ID = string | number;
type Usuario = {
  id: ID;
  nombre: string;
  email: string;
};

// Type alias con union
type Estado = "idle" | "loading" | "success" | "error";

// Type alias para funciones
type EventHandler = (event: Event) => void;
type Callback<T> = (data: T) => void;

// Type alias con generics
type ApiResponse<T> = {
  data: T;
  status: number;
  message: string;
};

type UsuarioResponse = ApiResponse<Usuario>;
```

### 7. Diferencias entre Interface y Type

```typescript
// Interface - puede ser extendida y implementada
interface InterfaceUsuario {
  nombre: string;
}

interface InterfaceUsuario {
  // Declaration merging - se combina con la anterior
  edad: number;
}

// Type - más flexible para unions y primitivos
type TypeUsuario = {
  nombre: string;
} & {
  edad: number;
};

// Type con union
type StringOrNumber = string | number;

// Type con conditional types
type NonNullable<T> = T extends null | undefined ? never : T;
```

### 8. Utility Types

```typescript
interface Usuario {
  id: number;
  nombre: string;
  email: string;
  edad: number;
  activo: boolean;
}

// Partial - hace todas las propiedades opcionales
type UsuarioParcial = Partial<Usuario>;
const actualizarUsuario: UsuarioParcial = {
  nombre: "Nuevo nombre"
  // Otras propiedades son opcionales
};

// Pick - selecciona propiedades específicas
type UsuarioPublico = Pick<Usuario, "id" | "nombre">;

// Omit - excluye propiedades específicas
type UsuarioSinId = Omit<Usuario, "id">;

// Required - hace todas las propiedades requeridas
type UsuarioCompleto = Required<Partial<Usuario>>;

// Record - crea un tipo con claves y valores específicos
type UsuariosPorRol = Record<"admin" | "user" | "guest", Usuario[]>;
```

---

## 🔧 Generics

Los generics permiten crear componentes reutilizables que funcionan con múltiples tipos.

### 1. Funciones Genéricas

```typescript
// Función genérica básica
function identidad<T>(arg: T): T {
  return arg;
}

// Uso
let numero = identidad<number>(42);
let texto = identidad<string>("Hola");
let booleano = identidad(true); // TypeScript infiere el tipo

// Función genérica más compleja
function primerElemento<T>(array: T[]): T | undefined {
  return array[0];
}

const numeros = [1, 2, 3];
const primer = primerElemento(numeros); // tipo: number | undefined

const frutas = ["manzana", "banana"];
const primeraFruta = primerElemento(frutas); // tipo: string | undefined
```

### 2. Interfaces Genéricas

```typescript
// Interface genérica
interface Respuesta<T> {
  data: T;
  status: number;
  message: string;
}

// Uso con diferentes tipos
interface Usuario {
  id: number;
  nombre: string;
}

interface Producto {
  id: number;
  nombre: string;
  precio: number;
}

const respuestaUsuario: Respuesta<Usuario> = {
  data: { id: 1, nombre: "Ana" },
  status: 200,
  message: "OK"
};

const respuestaProductos: Respuesta<Producto[]> = {
  data: [
    { id: 1, nombre: "Laptop", precio: 999 },
    { id: 2, nombre: "Mouse", precio: 25 }
  ],
  status: 200,
  message: "OK"
};
```

### 3. Clases Genéricas

```typescript
// Clase genérica
class Contenedor<T> {
  private items: T[] = [];

  agregar(item: T): void {
    this.items.push(item);
  }

  obtener(index: number): T | undefined {
    return this.items[index];
  }

  obtenerTodos(): T[] {
    return [...this.items];
  }

  get longitud(): number {
    return this.items.length;
  }
}

// Uso
const contenedorNumeros = new Contenedor<number>();
contenedorNumeros.agregar(1);
contenedorNumeros.agregar(2);

const contenedorStrings = new Contenedor<string>();
contenedorStrings.agregar("Hola");
contenedorStrings.agregar("Mundo");
```

### 4. Constraints (Restricciones)

```typescript
// Constraint básico
interface TieneLongitud {
  length: number;
}

function logearLongitud<T extends TieneLongitud>(arg: T): T {
  console.log(arg.length);
  return arg;
}

logearLongitud("Hola"); // ✅ string tiene length
logearLongitud([1, 2, 3]); // ✅ array tiene length
// logearLongitud(123); // Error: number no tiene length

// Constraint con keyof
function obtenerPropiedad<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

const persona = { nombre: "Ana", edad: 25, email: "ana@email.com" };
const nombre = obtenerPropiedad(persona, "nombre"); // tipo: string
const edad = obtenerPropiedad(persona, "edad"); // tipo: number
// const invalido = obtenerPropiedad(persona, "altura"); // Error: 'altura' no existe
```

### 5. Conditional Types

```typescript
// Conditional type básico
type EsArray<T> = T extends any[] ? true : false;

type Test1 = EsArray<string[]>; // true
type Test2 = EsArray<number>; // false

// Conditional type más complejo
type TipoElemento<T> = T extends (infer U)[] ? U : never;

type ElementoString = TipoElemento<string[]>; // string
type ElementoNumero = TipoElemento<number[]>; // number
type NoArray = TipoElemento<string>; // never

// Utility type personalizado
type NonNullable<T> = T extends null | undefined ? never : T;

type SinNull = NonNullable<string | null>; // string
type SinUndefined = NonNullable<number | undefined>; // number
```

### 6. Mapped Types

```typescript
// Mapped type básico
type Readonly<T> = {
  readonly [P in keyof T]: T[P];
};

type Optional<T> = {
  [P in keyof T]?: T[P];
};

interface Usuario {
  id: number;
  nombre: string;
  email: string;
}

type UsuarioReadonly = Readonly<Usuario>;
type UsuarioOpcional = Optional<Usuario>;

// Mapped type con transformación
type Stringify<T> = {
  [P in keyof T]: string;
};

type UsuarioString = Stringify<Usuario>;
// Resultado: { id: string; nombre: string; email: string; }
```

---

## ⚛️ Componentes Tipados

Ahora aplicaremos TypeScript a componentes de React, empezando con lo básico.

### 1. Componentes Funcionales Básicos

```tsx
import React from 'react';

// Componente sin props
const Saludo: React.FC = () => {
  return <h1>¡Hola, mundo!</h1>;
};

// Alternativa más moderna (recomendada)
const SaludoModerno = (): JSX.Element => {
  return <h1>¡Hola, mundo!</h1>;
};

// Componente con JSX implícito
const SaludoSimple = () => <h1>¡Hola, mundo!</h1>;

export default Saludo;
```

### 2. Componentes con Props Tipadas

```tsx
import React from 'react';

// Definir tipos de props
interface PerfilProps {
  nombre: string;
  edad: number;
  email: string;
  activo?: boolean; // Prop opcional
}

// Componente con props tipadas
const Perfil: React.FC<PerfilProps> = ({ nombre, edad, email, activo = true }) => {
  return (
    <div className={`perfil ${activo ? 'activo' : 'inactivo'}`}>
      <h2>{nombre}</h2>
      <p>Edad: {edad} años</p>
      <p>Email: {email}</p>
      <p>Estado: {activo ? 'Activo' : 'Inactivo'}</p>
    </div>
  );
};

// Uso del componente
const App = () => {
  return (
    <div>
      <Perfil 
        nombre="Ana García" 
        edad={28} 
        email="ana@email.com" 
        activo={true}
      />
      <Perfil 
        nombre="Carlos López" 
        edad={32} 
        email="carlos@email.com"
        // activo es opcional, usa valor por defecto
      />
    </div>
  );
};

export default App;
```

### 3. Componentes con Props Complejas

```tsx
import React from 'react';

// Props con objetos anidados
interface Direccion {
  calle: string;
  ciudad: string;
  codigoPostal: string;
  pais: string;
}

interface Usuario {
  id: number;
  nombre: string;
  email: string;
  direccion: Direccion;
  hobbies: string[];
  activo: boolean;
}

interface TarjetaUsuarioProps {
  usuario: Usuario;
  onEdit?: (id: number) => void;
  onDelete?: (id: number) => void;
  showActions?: boolean;
}

const TarjetaUsuario: React.FC<TarjetaUsuarioProps> = ({
  usuario,
  onEdit,
  onDelete,
  showActions = true
}) => {
  return (
    <div className="tarjeta-usuario">
      <div className="usuario-info">
        <h3>{usuario.nombre}</h3>
        <p>{usuario.email}</p>
        <div className="direccion">
          <p>{usuario.direccion.calle}</p>
          <p>{usuario.direccion.ciudad}, {usuario.direccion.codigoPostal}</p>
          <p>{usuario.direccion.pais}</p>
        </div>
        <div className="hobbies">
          <h4>Hobbies:</h4>
          <ul>
            {usuario.hobbies.map((hobby, index) => (
              <li key={index}>{hobby}</li>
            ))}
          </ul>
        </div>
        <span className={`estado ${usuario.activo ? 'activo' : 'inactivo'}`}>
          {usuario.activo ? 'Activo' : 'Inactivo'}
        </span>
      </div>
      
      {showActions && (
        <div className="acciones">
          {onEdit && (
            <button onClick={() => onEdit(usuario.id)}>
              Editar
            </button>
          )}
          {onDelete && (
            <button onClick={() => onDelete(usuario.id)}>
              Eliminar
            </button>
          )}
        </div>
      )}
    </div>
  );
};

// Componente con props de función
interface BotonProps {
  children: React.ReactNode;
  variant?: 'primary' | 'secondary' | 'danger';
  size?: 'small' | 'medium' | 'large';
  disabled?: boolean;
  loading?: boolean;
  onClick?: () => void;
}

const Boton: React.FC<BotonProps> = ({
  children,
  variant = 'primary',
  size = 'medium',
  disabled = false,
  loading = false,
  onClick
}) => {
  const className = `boton boton--${variant} boton--${size}`;
  
  return (
    <button
      className={className}
      disabled={disabled || loading}
      onClick={onClick}
    >
      {loading ? 'Cargando...' : children}
    </button>
  );
};

export { TarjetaUsuario, Boton };
```

### 4. Componentes con Children

```tsx
import React from 'react';

// Props con children tipados
interface ContenedorProps {
  children: React.ReactNode;
  className?: string;
  padding?: boolean;
}

const Contenedor: React.FC<ContenedorProps> = ({
  children,
  className = '',
  padding = true
}) => {
  return (
    <div className={`contenedor ${className} ${padding ? 'con-padding' : ''}`}>
      {children}
    </div>
  );
};

// Children con tipos específicos
interface ModalProps {
  isOpen: boolean;
  onClose: () => void;
  title: string;
  children: React.ReactNode;
  footer?: React.ReactNode;
}

const Modal: React.FC<ModalProps> = ({
  isOpen,
  onClose,
  title,
  children,
  footer
}) => {
  if (!isOpen) return null;

  return (
    <div className="modal-overlay" onClick={onClose}>
      <div className="modal-content" onClick={(e) => e.stopPropagation()}>
        <div className="modal-header">
          <h2>{title}</h2>
          <button onClick={onClose}>×</button>
        </div>
        <div className="modal-body">
          {children}
        </div>
        {footer && (
          <div className="modal-footer">
            {footer}
          </div>
        )}
      </div>
    </div>
  );
};

// Componente con children como función (render props)
interface ToggleProps {
  children: (props: {
    isOn: boolean;
    toggle: () => void;
    turnOn: () => void;
    turnOff: () => void;
  }) => React.ReactNode;
  initialValue?: boolean;
}

const Toggle: React.FC<ToggleProps> = ({ children, initialValue = false }) => {
  const [isOn, setIsOn] = React.useState(initialValue);

  const toggle = () => setIsOn(!isOn);
  const turnOn = () => setIsOn(true);
  const turnOff = () => setIsOn(false);

  return (
    <>
      {children({ isOn, toggle, turnOn, turnOff })}
    </>
  );
};

// Uso de los componentes
const EjemploUso = () => {
  const [modalAbierto, setModalAbierto] = React.useState(false);

  return (
    <Contenedor className="ejemplo" padding={true}>
      <h1>Ejemplo de Componentes</h1>
      
      <Toggle initialValue={false}>
        {({ isOn, toggle }) => (
          <div>
            <p>El interruptor está: {isOn ? 'Encendido' : 'Apagado'}</p>
            <button onClick={toggle}>
              {isOn ? 'Apagar' : 'Encender'}
            </button>
          </div>
        )}
      </Toggle>

      <Boton onClick={() => setModalAbierto(true)}>
        Abrir Modal
      </Boton>

      <Modal
        isOpen={modalAbierto}
        onClose={() => setModalAbierto(false)}
        title="Modal de Ejemplo"
        footer={
          <div>
            <Boton variant="secondary" onClick={() => setModalAbierto(false)}>
              Cancelar
            </Boton>
            <Boton onClick={() => setModalAbierto(false)}>
              Confirmar
            </Boton>
          </div>
        }
      >
        <p>Este es el contenido del modal.</p>
      </Modal>
    </Contenedor>
  );
};

export default EjemploUso;

---

## 📝 Props con TypeScript

Las props son la forma principal de pasar datos entre componentes en React. Con TypeScript, podemos definir exactamente qué props espera cada componente.

### 1. Props Básicas

```tsx
import React from 'react';

// Interface para props simples
interface SaludoProps {
  nombre: string;
  edad?: number; // Opcional
}

const Saludo: React.FC<SaludoProps> = ({ nombre, edad }) => {
  return (
    <div>
      <h1>¡Hola, {nombre}!</h1>
      {edad && <p>Tienes {edad} años</p>}
    </div>
  );
};

// Uso del componente
const App = () => {
  return (
    <div>
      <Saludo nombre="Ana" edad={25} />
      <Saludo nombre="Carlos" /> {/* edad es opcional */}
    </div>
  );
};
```

### 2. Props con Valores por Defecto

```tsx
interface BotonProps {
  children: React.ReactNode;
  variant?: 'primary' | 'secondary' | 'danger';
  size?: 'small' | 'medium' | 'large';
  disabled?: boolean;
  onClick?: () => void;
}

const Boton: React.FC<BotonProps> = ({
  children,
  variant = 'primary',
  size = 'medium',
  disabled = false,
  onClick
}) => {
  const className = `btn btn--${variant} btn--${size}`;
  
  return (
    <button 
      className={className}
      disabled={disabled}
      onClick={onClick}
    >
      {children}
    </button>
  );
};

// Uso con diferentes configuraciones
const BotonesEjemplo = () => {
  return (
    <div>
      <Boton>Botón por defecto</Boton>
      <Boton variant="secondary" size="large">
        Botón secundario grande
      </Boton>
      <Boton variant="danger" disabled>
        Botón deshabilitado
      </Boton>
    </div>
  );
};
```

### 3. Props con Funciones

```tsx
interface Usuario {
  id: number;
  nombre: string;
  email: string;
}

interface ListaUsuariosProps {
  usuarios: Usuario[];
  onUsuarioClick: (usuario: Usuario) => void;
  onUsuarioEliminar: (id: number) => void;
  onUsuarioEditar?: (usuario: Usuario) => void;
}

const ListaUsuarios: React.FC<ListaUsuariosProps> = ({
  usuarios,
  onUsuarioClick,
  onUsuarioEliminar,
  onUsuarioEditar
}) => {
  return (
    <div className="lista-usuarios">
      {usuarios.map(usuario => (
        <div key={usuario.id} className="usuario-item">
          <div onClick={() => onUsuarioClick(usuario)}>
            <h3>{usuario.nombre}</h3>
            <p>{usuario.email}</p>
          </div>
          <div className="acciones">
            {onUsuarioEditar && (
              <button onClick={() => onUsuarioEditar(usuario)}>
                Editar
              </button>
            )}
            <button 
              onClick={() => onUsuarioEliminar(usuario.id)}
              className="btn-danger"
            >
              Eliminar
            </button>
          </div>
        </div>
      ))}
    </div>
  );
};

// Uso del componente
const GestorUsuarios = () => {
  const [usuarios, setUsuarios] = React.useState<Usuario[]>([
    { id: 1, nombre: "Ana", email: "ana@email.com" },
    { id: 2, nombre: "Carlos", email: "carlos@email.com" }
  ]);

  const handleUsuarioClick = (usuario: Usuario) => {
    console.log('Usuario clickeado:', usuario);
  };

  const handleUsuarioEliminar = (id: number) => {
    setUsuarios(prev => prev.filter(u => u.id !== id));
  };

  const handleUsuarioEditar = (usuario: Usuario) => {
    console.log('Editar usuario:', usuario);
  };

  return (
    <ListaUsuarios 
      usuarios={usuarios}
      onUsuarioClick={handleUsuarioClick}
      onUsuarioEliminar={handleUsuarioEliminar}
      onUsuarioEditar={handleUsuarioEditar}
    />
  );
};
```

### 4. Props Genéricas

```tsx
// Componente genérico para listas
interface ListaGenericaProps<T> {
  items: T[];
  renderItem: (item: T, index: number) => React.ReactNode;
  keyExtractor: (item: T) => string | number;
  emptyMessage?: string;
}

function ListaGenerica<T>({
  items,
  renderItem,
  keyExtractor,
  emptyMessage = "No hay elementos"
}: ListaGenericaProps<T>) {
  if (items.length === 0) {
    return <div className="empty-state">{emptyMessage}</div>;
  }

  return (
    <div className="lista-generica">
      {items.map((item, index) => (
        <div key={keyExtractor(item)} className="lista-item">
          {renderItem(item, index)}
        </div>
      ))}
    </div>
  );
}

// Uso con diferentes tipos
interface Producto {
  id: number;
  nombre: string;
  precio: number;
}

const EjemploListaGenerica = () => {
  const productos: Producto[] = [
    { id: 1, nombre: "Laptop", precio: 999 },
    { id: 2, nombre: "Mouse", precio: 25 }
  ];

  const usuarios: Usuario[] = [
    { id: 1, nombre: "Ana", email: "ana@email.com" }
  ];

  return (
    <div>
      <h2>Productos</h2>
      <ListaGenerica
        items={productos}
        keyExtractor={(producto) => producto.id}
        renderItem={(producto) => (
          <div>
            <h3>{producto.nombre}</h3>
            <p>${producto.precio}</p>
          </div>
        )}
        emptyMessage="No hay productos disponibles"
      />

      <h2>Usuarios</h2>
      <ListaGenerica
        items={usuarios}
        keyExtractor={(usuario) => usuario.id}
        renderItem={(usuario) => (
          <div>
            <h3>{usuario.nombre}</h3>
            <p>{usuario.email}</p>
          </div>
        )}
      />
    </div>
  );
};
```

### 5. Extendiendo Props de Elementos HTML

```tsx
// Extender props de button
interface BotonPersonalizadoProps extends React.ButtonHTMLAttributes<HTMLButtonElement> {
  variant?: 'primary' | 'secondary';
  loading?: boolean;
}

const BotonPersonalizado: React.FC<BotonPersonalizadoProps> = ({
  variant = 'primary',
  loading = false,
  children,
  disabled,
  className = '',
  ...rest
}) => {
  return (
    <button
      className={`btn btn--${variant} ${className}`}
      disabled={disabled || loading}
      {...rest}
    >
      {loading ? 'Cargando...' : children}
    </button>
  );
};

// Extender props de input
interface InputPersonalizadoProps extends React.InputHTMLAttributes<HTMLInputElement> {
  label?: string;
  error?: string;
  helperText?: string;
}

const InputPersonalizado: React.FC<InputPersonalizadoProps> = ({
  label,
  error,
  helperText,
  className = '',
  ...rest
}) => {
  return (
    <div className="input-group">
      {label && <label className="input-label">{label}</label>}
      <input 
        className={`input ${error ? 'input--error' : ''} ${className}`}
        {...rest}
      />
      {error && <span className="input-error">{error}</span>}
      {helperText && !error && (
        <span className="input-helper">{helperText}</span>
      )}
    </div>
  );
};

// Uso de componentes extendidos
const FormularioEjemplo = () => {
  const [loading, setLoading] = React.useState(false);
  const [email, setEmail] = React.useState('');
  const [error, setError] = React.useState('');

  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    setLoading(true);
    // Simular envío
    setTimeout(() => setLoading(false), 2000);
  };

  return (
    <form onSubmit={handleSubmit}>
      <InputPersonalizado
        label="Email"
        type="email"
        value={email}
        onChange={(e) => setEmail(e.target.value)}
        error={error}
        helperText="Ingresa tu email para continuar"
        placeholder="ejemplo@email.com"
        required
      />
      
      <BotonPersonalizado
        type="submit"
        variant="primary"
        loading={loading}
        onClick={() => console.log('Botón clickeado')}
      >
        Enviar
      </BotonPersonalizado>
    </form>
  );
};
```

---

## 🎣 State y Hooks Tipados

Los hooks de React con TypeScript proporcionan type safety y mejor experiencia de desarrollo.

### 1. useState con TypeScript

```tsx
import React, { useState } from 'react';

// Estado simple con inferencia de tipos
const ContadorSimple: React.FC = () => {
  const [count, setCount] = useState(0); // TypeScript infiere number
  
  return (
    <div>
      <p>Contador: {count}</p>
      <button onClick={() => setCount(count + 1)}>+</button>
      <button onClick={() => setCount(count - 1)}>-</button>
    </div>
  );
};

// Estado con tipo explícito
interface Usuario {
  id: number;
  nombre: string;
  email: string;
  activo: boolean;
}

const PerfilUsuario: React.FC = () => {
  // Estado que puede ser null inicialmente
  const [usuario, setUsuario] = useState<Usuario | null>(null);
  
  // Estado con valor inicial tipado
  const [usuarios, setUsuarios] = useState<Usuario[]>([]);
  
  // Estado con union types
  const [estado, setEstado] = useState<'idle' | 'loading' | 'success' | 'error'>('idle');
  
  const cargarUsuario = async () => {
    setEstado('loading');
    try {
      // Simular API call
      const nuevoUsuario: Usuario = {
        id: 1,
        nombre: "Ana García",
        email: "ana@email.com",
        activo: true
      };
      setUsuario(nuevoUsuario);
      setEstado('success');
    } catch (error) {
      setEstado('error');
    }
  };
  
  const actualizarUsuario = (campo: keyof Usuario, valor: any) => {
    if (usuario) {
      setUsuario({
        ...usuario,
        [campo]: valor
      });
    }
  };
  
  return (
    <div>
      {estado === 'loading' && <p>Cargando...</p>}
      {estado === 'error' && <p>Error al cargar usuario</p>}
      {usuario && (
        <div>
          <h2>{usuario.nombre}</h2>
          <p>{usuario.email}</p>
          <p>Estado: {usuario.activo ? 'Activo' : 'Inactivo'}</p>
          <button onClick={() => actualizarUsuario('activo', !usuario.activo)}>
            Cambiar estado
          </button>
        </div>
      )}
      <button onClick={cargarUsuario}>Cargar Usuario</button>
    </div>
  );
};
```

### 2. useEffect con TypeScript

```tsx
import React, { useState, useEffect } from 'react';

interface Post {
  id: number;
  title: string;
  body: string;
  userId: number;
}

const ListaPosts: React.FC = () => {
  const [posts, setPosts] = useState<Post[]>([]);
  const [loading, setLoading] = useState<boolean>(true);
  const [error, setError] = useState<string | null>(null);
  
  // Effect para cargar datos
  useEffect(() => {
    const cargarPosts = async (): Promise<void> => {
      try {
        setLoading(true);
        setError(null);
        
        const response = await fetch('https://jsonplaceholder.typicode.com/posts');
        
        if (!response.ok) {
          throw new Error(`Error HTTP: ${response.status}`);
        }
        
        const data: Post[] = await response.json();
        setPosts(data.slice(0, 10)); // Solo primeros 10
      } catch (err) {
        const errorMessage = err instanceof Error ? err.message : 'Error desconocido';
        setError(errorMessage);
      } finally {
        setLoading(false);
      }
    };
    
    cargarPosts();
  }, []); // Array de dependencias vacío
  
  // Effect con cleanup
  useEffect(() => {
    const interval = setInterval(() => {
      console.log('Actualizando cada 5 segundos');
    }, 5000);
    
    // Cleanup function
    return () => {
      clearInterval(interval);
    };
  }, []);
  
  // Effect que depende de posts
  useEffect(() => {
    if (posts.length > 0) {
      document.title = `${posts.length} posts cargados`;
    }
    
    return () => {
      document.title = 'Mi App';
    };
  }, [posts]);
  
  if (loading) return <div>Cargando posts...</div>;
  if (error) return <div>Error: {error}</div>;
  
  return (
    <div>
      <h2>Posts ({posts.length})</h2>
      <ul>
        {posts.map(post => (
          <li key={post.id}>
            <h3>{post.title}</h3>
            <p>{post.body}</p>
          </li>
        ))}
      </ul>
    </div>
  );
};
```

### 3. useReducer con TypeScript

```tsx
import React, { useReducer } from 'react';

// Definir el estado
interface TodoState {
  todos: Todo[];
  filter: 'all' | 'active' | 'completed';
}

interface Todo {
  id: number;
  text: string;
  completed: boolean;
}

// Definir las acciones
type TodoAction = 
  | { type: 'ADD_TODO'; payload: string }
  | { type: 'TOGGLE_TODO'; payload: number }
  | { type: 'DELETE_TODO'; payload: number }
  | { type: 'SET_FILTER'; payload: 'all' | 'active' | 'completed' }
  | { type: 'CLEAR_COMPLETED' };

// Reducer tipado
const todoReducer = (state: TodoState, action: TodoAction): TodoState => {
  switch (action.type) {
    case 'ADD_TODO':
      const newTodo: Todo = {
        id: Date.now(),
        text: action.payload,
        completed: false
      };
      return {
        ...state,
        todos: [...state.todos, newTodo]
      };
      
    case 'TOGGLE_TODO':
      return {
        ...state,
        todos: state.todos.map(todo =>
          todo.id === action.payload
            ? { ...todo, completed: !todo.completed }
            : todo
        )
      };
      
    case 'DELETE_TODO':
      return {
        ...state,
        todos: state.todos.filter(todo => todo.id !== action.payload)
      };
      
    case 'SET_FILTER':
      return {
        ...state,
        filter: action.payload
      };
      
    case 'CLEAR_COMPLETED':
      return {
        ...state,
        todos: state.todos.filter(todo => !todo.completed)
      };
      
    default:
      return state;
  }
};

// Estado inicial
const initialState: TodoState = {
  todos: [],
  filter: 'all'
};

const TodoApp: React.FC = () => {
  const [state, dispatch] = useReducer(todoReducer, initialState);
  const [inputValue, setInputValue] = useState<string>('');
  
  // Filtrar todos según el filtro actual
  const filteredTodos = state.todos.filter(todo => {
    switch (state.filter) {
      case 'active':
        return !todo.completed;
      case 'completed':
        return todo.completed;
      default:
        return true;
    }
  });
  
  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    if (inputValue.trim()) {
      dispatch({ type: 'ADD_TODO', payload: inputValue.trim() });
      setInputValue('');
    }
  };
  
  return (
    <div className="todo-app">
      <h1>Todo App</h1>
      
      <form onSubmit={handleSubmit}>
        <input 
          type="text"
          value={inputValue}
          onChange={(e) => setInputValue(e.target.value)}
          placeholder="Agregar nueva tarea..."
        />
        <button type="submit">Agregar</button>
      </form>
      
      <div className="filters">
        <button 
          onClick={() => dispatch({ type: 'SET_FILTER', payload: 'all' })}
          className={state.filter === 'all' ? 'active' : ''}
        >
          Todas
        </button>
        <button 
          onClick={() => dispatch({ type: 'SET_FILTER', payload: 'active' })}
          className={state.filter === 'active' ? 'active' : ''}
        >
          Activas
        </button>
        <button 
          onClick={() => dispatch({ type: 'SET_FILTER', payload: 'completed' })}
          className={state.filter === 'completed' ? 'active' : ''}
        >
          Completadas
        </button>
      </div>
      
      <ul className="todo-list">
        {filteredTodos.map(todo => (
          <li key={todo.id} className={todo.completed ? 'completed' : ''}>
            <input 
              type="checkbox"
              checked={todo.completed}
              onChange={() => dispatch({ type: 'TOGGLE_TODO', payload: todo.id })}
            />
            <span>{todo.text}</span>
            <button 
              onClick={() => dispatch({ type: 'DELETE_TODO', payload: todo.id })}
              className="delete-btn"
            >
              ×
            </button>
          </li>
        ))}
      </ul>
      
      {state.todos.some(todo => todo.completed) && (
        <button 
          onClick={() => dispatch({ type: 'CLEAR_COMPLETED' })}
          className="clear-completed"
        >
          Limpiar completadas
        </button>
      )}
      
      <div className="stats">
        <p>Total: {state.todos.length}</p>
        <p>Activas: {state.todos.filter(t => !t.completed).length}</p>
        <p>Completadas: {state.todos.filter(t => t.completed).length}</p>
      </div>
    </div>
  );
};
```

### 4. Custom Hooks con TypeScript

```tsx
import { useState, useEffect, useCallback } from 'react';

// Hook para fetch de datos
interface UseFetchResult<T> {
  data: T | null;
  loading: boolean;
  error: string | null;
  refetch: () => Promise<void>;
}

function useFetch<T>(url: string): UseFetchResult<T> {
  const [data, setData] = useState<T | null>(null);
  const [loading, setLoading] = useState<boolean>(true);
  const [error, setError] = useState<string | null>(null);
  
  const fetchData = useCallback(async (): Promise<void> => {
    try {
      setLoading(true);
      setError(null);
      
      const response = await fetch(url);
      if (!response.ok) {
        throw new Error(`Error: ${response.status}`);
      }
      
      const result: T = await response.json();
      setData(result);
    } catch (err) {
      const errorMessage = err instanceof Error ? err.message : 'Error desconocido';
      setError(errorMessage);
    } finally {
      setLoading(false);
    }
  }, [url]);
  
  useEffect(() => {
    fetchData();
  }, [fetchData]);
  
  return { data, loading, error, refetch: fetchData };
}

// Hook para localStorage
function useLocalStorage<T>(
  key: string, 
  initialValue: T
): [T, (value: T | ((prev: T) => T)) => void] {
  const [storedValue, setStoredValue] = useState<T>(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      console.error(`Error reading localStorage key "${key}":`, error);
      return initialValue;
    }
  });
  
  const setValue = (value: T | ((prev: T) => T)) => {
    try {
      const valueToStore = value instanceof Function ? value(storedValue) : value;
      setStoredValue(valueToStore);
      window.localStorage.setItem(key, JSON.stringify(valueToStore));
    } catch (error) {
      console.error(`Error setting localStorage key "${key}":`, error);
    }
  };
  
  return [storedValue, setValue];
}

// Hook para debounce
function useDebounce<T>(value: T, delay: number): T {
  const [debouncedValue, setDebouncedValue] = useState<T>(value);
  
  useEffect(() => {
    const handler = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);
    
    return () => {
      clearTimeout(handler);
    };
  }, [value, delay]);
  
  return debouncedValue;
}

// Hook para toggle
function useToggle(initialValue: boolean = false): [boolean, () => void, (value: boolean) => void] {
  const [value, setValue] = useState<boolean>(initialValue);
  
  const toggle = useCallback(() => {
    setValue(prev => !prev);
  }, []);
  
  const setToggle = useCallback((newValue: boolean) => {
    setValue(newValue);
  }, []);
  
  return [value, toggle, setToggle];
}

// Ejemplo de uso de los custom hooks
const EjemploCustomHooks: React.FC = () => {
  // Hook de fetch
  const { data: posts, loading, error, refetch } = useFetch<Post[]>(
    'https://jsonplaceholder.typicode.com/posts'
  );
  
  // Hook de localStorage
  const [tema, setTema] = useLocalStorage<'light' | 'dark'>('tema', 'light');
  
  // Hook de toggle
  const [mostrarDetalles, toggleDetalles] = useToggle(false);
  
  // Hook de debounce
  const [busqueda, setBusqueda] = useState<string>('');
  const busquedaDebounced = useDebounce(busqueda, 500);
  
  // Effect que se ejecuta cuando cambia la búsqueda debounced
  useEffect(() => {
    if (busquedaDebounced) {
      console.log('Buscando:', busquedaDebounced);
      // Aquí harías la búsqueda real
    }
  }, [busquedaDebounced]);
  
  const postsFiltrados = posts?.filter(post => 
    post.title.toLowerCase().includes(busquedaDebounced.toLowerCase())
  ) || [];
  
  return (
    <div className={`app tema-${tema}`}>
      <header>
        <h1>Ejemplo Custom Hooks</h1>
        <button onClick={() => setTema(tema === 'light' ? 'dark' : 'light')}>>
          Cambiar tema ({tema})
        </button>
      </header>
      
      <div className="busqueda">
        <input 
          type="text"
          value={busqueda}
          onChange={(e) => setBusqueda(e.target.value)}
          placeholder="Buscar posts..."
        />
        <p>Buscando: {busquedaDebounced}</p>
      </div>
      
      <div className="controles">
        <button onClick={toggleDetalles}>
          {mostrarDetalles ? 'Ocultar' : 'Mostrar'} detalles
        </button>
        <button onClick={refetch} disabled={loading}>
          Recargar posts
        </button>
      </div>
      
      {loading && <p>Cargando posts...</p>}
      {error && (
        <div className="error">
          <p>Error: {error}</p>
          <button onClick={refetch}>Reintentar</button>
        </div>
      )}
      
      {posts && (
        <div className="posts">
          <h2>Posts ({postsFiltrados.length})</h2>
          {postsFiltrados.map(post => (
            <div key={post.id} className="post">
              <h3>{post.title}</h3>
              {mostrarDetalles && (
                <div>
                  <p>{post.body}</p>
                  <small>Usuario ID: {post.userId}</small>
                </div>
              )}
            </div>
          ))}
        </div>
      )}
    </div>
  );
};

export default EjemploCustomHooks;
```

---

## 🎯 Eventos y Formularios Tipados

### 1. Manejo de Eventos con TypeScript

```tsx
import React, { useState } from 'react';

const ManejoEventos: React.FC = () => {
  const [mensaje, setMensaje] = useState<string>('');
  const [posicion, setPosicion] = useState<{ x: number; y: number }>({ x: 0, y: 0 });
  
  // Evento de click en botón
  const handleClick = (event: React.MouseEvent<HTMLButtonElement>) => {
    console.log('Botón clickeado:', event.currentTarget.textContent);
    console.log('Posición del click:', event.clientX, event.clientY);
  };
  
  // Evento de input
  const handleInputChange = (event: React.ChangeEvent<HTMLInputElement>) => {
    setMensaje(event.target.value);
  };
  
  // Evento de textarea
  const handleTextareaChange = (event: React.ChangeEvent<HTMLTextAreaElement>) => {
    console.log('Textarea cambiado:', event.target.value);
  };
  
  // Evento de select
  const handleSelectChange = (event: React.ChangeEvent<HTMLSelectElement>) => {
    console.log('Opción seleccionada:', event.target.value);
  };
  
  // Evento de submit
  const handleSubmit = (event: React.FormEvent<HTMLFormElement>) => {
    event.preventDefault();
    console.log('Formulario enviado con:', mensaje);
  };
  
  // Evento de teclado
  const handleKeyDown = (event: React.KeyboardEvent<HTMLInputElement>) => {
    if (event.key === 'Enter') {
      console.log('Enter presionado');
    }
    if (event.ctrlKey && event.key === 's') {
      event.preventDefault();
      console.log('Ctrl+S presionado');
    }
  };
  
  // Evento de mouse
  const handleMouseMove = (event: React.MouseEvent<HTMLDivElement>) => {
    setPosicion({ x: event.clientX, y: event.clientY });
  };
  
  // Evento de focus
  const handleFocus = (event: React.FocusEvent<HTMLInputElement>) => {
    console.log('Input enfocado:', event.target.name);
  };
  
  // Evento de blur
  const handleBlur = (event: React.FocusEvent<HTMLInputElement>) => {
    console.log('Input desenfocado:', event.target.name);
  };
  
  return (
    <div className="manejo-eventos">
      <h2>Manejo de Eventos con TypeScript</h2>
      
      <form onSubmit={handleSubmit}>
        <div>
          <label htmlFor="mensaje">Mensaje:</label>
          <input 
            id="mensaje"
            name="mensaje"
            type="text"
            value={mensaje}
            onChange={handleInputChange}
            onKeyDown={handleKeyDown}
            onFocus={handleFocus}
            onBlur={handleBlur}
            placeholder="Escribe un mensaje"
          />
        </div>
        
        <div>
          <label htmlFor="descripcion">Descripción:</label>
          <textarea 
            id="descripcion"
            name="descripcion"
            onChange={handleTextareaChange}
            placeholder="Descripción detallada"
          />
        </div>
        
        <div>
          <label htmlFor="categoria">Categoría:</label>
          <select id="categoria" name="categoria" onChange={handleSelectChange}>
            <option value="">Seleccionar categoría</option>
            <option value="trabajo">Trabajo</option>
            <option value="personal">Personal</option>
            <option value="estudio">Estudio</option>
          </select>
        </div>
        
        <button type="submit" onClick={handleClick}>
          Enviar
        </button>
      </form>
      
      <div 
        className="mouse-area"
        onMouseMove={handleMouseMove}
        style={{ 
          height: '200px', 
          border: '1px solid #ccc', 
          marginTop: '20px',
          padding: '10px'
        }}
      >
        <p>Mueve el mouse aquí</p>
        <p>Posición: X: {posicion.x}, Y: {posicion.y}</p>
      </div>
    </div>
  );
};
```

### 2. Formularios Complejos con Validación

```tsx
import React, { useState } from 'react';

// Tipos para el formulario
interface FormularioRegistro {
  nombre: string;
  email: string;
  password: string;
  confirmarPassword: string;
  edad: number;
  genero: 'masculino' | 'femenino' | 'otro' | '';
  intereses: string[];
  terminos: boolean;
  newsletter: boolean;
}

interface ErroresFormulario {
  nombre?: string;
  email?: string;
  password?: string;
  confirmarPassword?: string;
  edad?: string;
  genero?: string;
  terminos?: string;
}

const FormularioRegistro: React.FC = () => {
  const [formulario, setFormulario] = useState<FormularioRegistro>({
    nombre: '',
    email: '',
    password: '',
    confirmarPassword: '',
    edad: 0,
    genero: '',
    intereses: [],
    terminos: false,
    newsletter: false
  });
  
  const [errores, setErrores] = useState<ErroresFormulario>({});
  const [enviando, setEnviando] = useState<boolean>(false);
  const [enviado, setEnviado] = useState<boolean>(false);
  
  // Validaciones
  const validarFormulario = (): boolean => {
    const nuevosErrores: ErroresFormulario = {};
    
    // Validar nombre
    if (!formulario.nombre.trim()) {
      nuevosErrores.nombre = 'El nombre es requerido';
    } else if (formulario.nombre.length < 2) {
      nuevosErrores.nombre = 'El nombre debe tener al menos 2 caracteres';
    }
    
    // Validar email
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!formulario.email) {
      nuevosErrores.email = 'El email es requerido';
    } else if (!emailRegex.test(formulario.email)) {
      nuevosErrores.email = 'Email inválido';
    }
    
    // Validar password
    if (!formulario.password) {
      nuevosErrores.password = 'La contraseña es requerida';
    } else if (formulario.password.length < 6) {
      nuevosErrores.password = 'La contraseña debe tener al menos 6 caracteres';
    }
    
    // Validar confirmación de password
    if (formulario.password !== formulario.confirmarPassword) {
      nuevosErrores.confirmarPassword = 'Las contraseñas no coinciden';
    }
    
    // Validar edad
    if (formulario.edad < 18) {
      nuevosErrores.edad = 'Debe ser mayor de 18 años';
    } else if (formulario.edad > 120) {
      nuevosErrores.edad = 'Edad inválida';
    }
    
    // Validar género
    if (!formulario.genero) {
      nuevosErrores.genero = 'Seleccione un género';
    }
    
    // Validar términos
    if (!formulario.terminos) {
      nuevosErrores.terminos = 'Debe aceptar los términos y condiciones';
    }
    
    setErrores(nuevosErrores);
    return Object.keys(nuevosErrores).length === 0;
  };
  
  // Actualizar campo del formulario
  const actualizarCampo = <K extends keyof FormularioRegistro>(
    campo: K,
    valor: FormularioRegistro[K]
  ) => {
    setFormulario(prev => ({
      ...prev,
      [campo]: valor
    }));
    
    // Limpiar error del campo
    if (errores[campo as keyof ErroresFormulario]) {
      setErrores(prev => ({
        ...prev,
        [campo]: undefined
      }));
    }
  };
  
  // Manejar cambio de intereses (checkbox múltiple)
  const manejarIntereses = (interes: string, marcado: boolean) => {
    const nuevosIntereses = marcado
      ? [...formulario.intereses, interes]
      : formulario.intereses.filter(i => i !== interes);
    
    actualizarCampo('intereses', nuevosIntereses);
  };
  
  // Enviar formulario
  const handleSubmit = async (event: React.FormEvent<HTMLFormElement>) => {
    event.preventDefault();
    
    if (!validarFormulario()) {
      return;
    }
    
    setEnviando(true);
    
    try {
      // Simular envío a API
      await new Promise(resolve => setTimeout(resolve, 2000));
      
      console.log('Datos del formulario:', formulario);
      setEnviado(true);
      
      // Resetear formulario
      setFormulario({
        nombre: '',
        email: '',
        password: '',
        confirmarPassword: '',
        edad: 0,
        genero: '',
        intereses: [],
        terminos: false,
        newsletter: false
      });
      
    } catch (error) {
      console.error('Error al enviar formulario:', error);
    } finally {
      setEnviando(false);
    }
  };
  
  if (enviado) {
    return (
      <div className="mensaje-exito">
        <h2>¡Registro exitoso!</h2>
        <p>Tu cuenta ha sido creada correctamente.</p>
        <button onClick={() => setEnviado(false)}>
          Registrar otro usuario
        </button>
      </div>
    );
  }
  
  return (
    <form onSubmit={handleSubmit} className="formulario-registro">
      <h2>Registro de Usuario</h2>
      
      {/* Nombre */}
      <div className="campo">
        <label htmlFor="nombre">Nombre completo *</label>
        <input 
          id="nombre"
          type="text"
          value={formulario.nombre}
          onChange={(e) => actualizarCampo('nombre', e.target.value)}
          className={errores.nombre ? 'error' : ''}
          placeholder="Ingresa tu nombre completo"
        />
        {errores.nombre && <span className="error-mensaje">{errores.nombre}</span>}
      </div>
      
      {/* Email */}
      <div className="campo">
        <label htmlFor="email">Email *</label>
        <input 
          id="email"
          type="email"
          value={formulario.email}
          onChange={(e) => actualizarCampo('email', e.target.value)}
          className={errores.email ? 'error' : ''}
          placeholder="ejemplo@email.com"
        />
        {errores.email && <span className="error-mensaje">{errores.email}</span>}
      </div>
      
      {/* Password */}
      <div className="campo">
        <label htmlFor="password">Contraseña *</label>
        <input 
          id="password"
          type="password"
          value={formulario.password}
          onChange={(e) => actualizarCampo('password', e.target.value)}
          className={errores.password ? 'error' : ''}
          placeholder="Mínimo 6 caracteres"
        />
        {errores.password && <span className="error-mensaje">{errores.password}</span>}
      </div>
      
      {/* Confirmar Password */}
      <div className="campo">
        <label htmlFor="confirmarPassword">Confirmar contraseña *</label>
        <input 
          id="confirmarPassword"
          type="password"
          value={formulario.confirmarPassword}
          onChange={(e) => actualizarCampo('confirmarPassword', e.target.value)}
          className={errores.confirmarPassword ? 'error' : ''}
          placeholder="Repite tu contraseña"
        />
        {errores.confirmarPassword && (
          <span className="error-mensaje">{errores.confirmarPassword}</span>
        )}
      </div>
      
      {/* Edad */}
      <div className="campo">
        <label htmlFor="edad">Edad *</label>
        <input 
          id="edad"
          type="number"
          min="18"
          max="120"
          value={formulario.edad || ''}
          onChange={(e) => actualizarCampo('edad', parseInt(e.target.value) || 0)}
          className={errores.edad ? 'error' : ''}
        />
        {errores.edad && <span className="error-mensaje">{errores.edad}</span>}
      </div>
      
      {/* Género */}
      <div className="campo">
        <label htmlFor="genero">Género *</label>
        <select 
          id="genero"
          value={formulario.genero}
          onChange={(e) => actualizarCampo('genero', e.target.value as FormularioRegistro['genero'])}
          className={errores.genero ? 'error' : ''}
        >
          <option value="">Seleccionar género</option>
          <option value="masculino">Masculino</option>
          <option value="femenino">Femenino</option>
          <option value="otro">Otro</option>
        </select>
        {errores.genero && <span className="error-mensaje">{errores.genero}</span>}
      </div>
      
      {/* Intereses */}
      <div className="campo">
        <label>Intereses (opcional)</label>
        <div className="checkbox-group">
          {['Tecnología', 'Deportes', 'Música', 'Viajes', 'Lectura'].map(interes => (
            <label key={interes} className="checkbox-label">
              <input 
                type="checkbox"
                checked={formulario.intereses.includes(interes)}
                onChange={(e) => manejarIntereses(interes, e.target.checked)}
              />
              {interes}
            </label>
          ))}
        </div>
      </div>
      
      {/* Términos */}
      <div className="campo">
        <label className="checkbox-label">
          <input 
            type="checkbox"
            checked={formulario.terminos}
            onChange={(e) => actualizarCampo('terminos', e.target.checked)}
          />
          Acepto los términos y condiciones *
        </label>
        {errores.terminos && <span className="error-mensaje">{errores.terminos}</span>}
      </div>
      
      {/* Newsletter */}
      <div className="campo">
        <label className="checkbox-label">
          <input 
            type="checkbox"
            checked={formulario.newsletter}
            onChange={(e) => actualizarCampo('newsletter', e.target.checked)}
          />
          Suscribirse al newsletter
        </label>
      </div>
      
      {/* Botón de envío */}
      <button 
        type="submit" 
        disabled={enviando}
        className="boton-enviar"
      >
        {enviando ? 'Registrando...' : 'Registrarse'}
      </button>
      
      <p className="nota">* Campos requeridos</p>
    </form>
  );
};

export default FormularioRegistro;
```

### 3. Formularios con React Hook Form y TypeScript

```tsx
import React from 'react';
import { useForm, SubmitHandler, Controller } from 'react-hook-form';

// Instalar: npm install react-hook-form

interface FormularioContacto {
  nombre: string;
  email: string;
  telefono: string;
  asunto: string;
  mensaje: string;
  prioridad: 'baja' | 'media' | 'alta';
  adjunto?: FileList;
}

const FormularioConHookForm: React.FC = () => {
  const {
    register,
    handleSubmit,
    control,
    formState: { errors, isSubmitting },
    reset,
    watch
  } = useForm<FormularioContacto>({
    defaultValues: {
      nombre: '',
      email: '',
      telefono: '',
      asunto: '',
      mensaje: '',
      prioridad: 'media'
    }
  });
  
  // Observar cambios en tiempo real
  const watchedPrioridad = watch('prioridad');
  
  const onSubmit: SubmitHandler<FormularioContacto> = async (data) => {
    try {
      console.log('Datos del formulario:', data);
      
      // Simular envío
      await new Promise(resolve => setTimeout(resolve, 2000));
      
      alert('Mensaje enviado correctamente!');
      reset(); // Resetear formulario
    } catch (error) {
      console.error('Error al enviar:', error);
    }
  };
  
  return (
    <form onSubmit={handleSubmit(onSubmit)} className="formulario-contacto">
      <h2>Formulario de Contacto</h2>
      
      {/* Nombre */}
      <div className="campo">
        <label htmlFor="nombre">Nombre *</label>
        <input 
          id="nombre"
          {...register('nombre', {
            required: 'El nombre es requerido',
            minLength: {
              value: 2,
              message: 'El nombre debe tener al menos 2 caracteres'
            }
          })}
          className={errors.nombre ? 'error' : ''}
        />
        {errors.nombre && (
          <span className="error-mensaje">{errors.nombre.message}</span>
        )}
      </div>
      
      {/* Email */}
      <div className="campo">
        <label htmlFor="email">Email *</label>
        <input 
          id="email"
          type="email"
          {...register('email', {
            required: 'El email es requerido',
            pattern: {
              value: /^[^\s@]+@[^\s@]+\.[^\s@]+$/,
              message: 'Email inválido'
            }
          })}
          className={errors.email ? 'error' : ''}
        />
        {errors.email && (
          <span className="error-mensaje">{errors.email.message}</span>
        )}
      </div>
      
      {/* Teléfono */}
      <div className="campo">
        <label htmlFor="telefono">Teléfono</label>
        <input 
          id="telefono"
          type="tel"
          {...register('telefono', {
            pattern: {
              value: /^[0-9+\-\s()]+$/,
              message: 'Formato de teléfono inválido'
            }
          })}
          className={errors.telefono ? 'error' : ''}
          placeholder="+1 (555) 123-4567"
        />
        {errors.telefono && (
          <span className="error-mensaje">{errors.telefono.message}</span>
        )}
      </div>
      
      {/* Asunto */}
      <div className="campo">
        <label htmlFor="asunto">Asunto *</label>
        <input 
          id="asunto"
          {...register('asunto', {
            required: 'El asunto es requerido',
            maxLength: {
              value: 100,
              message: 'El asunto no puede exceder 100 caracteres'
            }
          })}
          className={errors.asunto ? 'error' : ''}
        />
        {errors.asunto && (
          <span className="error-mensaje">{errors.asunto.message}</span>
        )}
      </div>
      
      {/* Prioridad con Controller */}
      <div className="campo">
        <label htmlFor="prioridad">Prioridad *</label>
        <Controller
          name="prioridad"
          control={control}
          rules={{ required: 'Seleccione una prioridad' }}
          render={({ field }) => (
            <select 
              {...field}
              id="prioridad"
              className={errors.prioridad ? 'error' : ''}
            >
              <option value="baja">Baja</option>
              <option value="media">Media</option>
              <option value="alta">Alta</option>
            </select>
          )}
        />
        {errors.prioridad && (
          <span className="error-mensaje">{errors.prioridad.message}</span>
        )}
        <p className="info">Prioridad seleccionada: {watchedPrioridad}</p>
      </div>
      
      {/* Mensaje */}
      <div className="campo">
        <label htmlFor="mensaje">Mensaje *</label>
        <textarea 
          id="mensaje"
          rows={5}
          {...register('mensaje', {
            required: 'El mensaje es requerido',
            minLength: {
              value: 10,
              message: 'El mensaje debe tener al menos 10 caracteres'
            },
            maxLength: {
              value: 500,
              message: 'El mensaje no puede exceder 500 caracteres'
            }
          })}
          className={errors.mensaje ? 'error' : ''}
          placeholder="Describe tu consulta..."
        />
        {errors.mensaje && (
          <span className="error-mensaje">{errors.mensaje.message}</span>
        )}
      </div>
      
      {/* Archivo adjunto */}
      <div className="campo">
        <label htmlFor="adjunto">Archivo adjunto (opcional)</label>
        <input 
          id="adjunto"
          type="file"
          accept=".pdf,.doc,.docx,.txt"
          {...register('adjunto')}
        />
        <small>Formatos permitidos: PDF, DOC, DOCX, TXT</small>
      </div>
      
      {/* Botón de envío */}
      <button 
        type="submit" 
        disabled={isSubmitting}
        className="boton-enviar"
      >
        {isSubmitting ? 'Enviando...' : 'Enviar mensaje'}
      </button>
    </form>
  );
};

export default FormularioConHookForm;
```

---

## 🌐 Context API con TypeScript

### 1. Context Básico con TypeScript

```tsx
import React, { createContext, useContext, useState, ReactNode } from 'react';

// Definir el tipo del contexto
interface Usuario {
  id: number;
  nombre: string;
  email: string;
  rol: 'admin' | 'usuario';
}

interface AuthContextType {
  usuario: Usuario | null;
  login: (email: string, password: string) => Promise<void>;
  logout: () => void;
  isLoading: boolean;
  error: string | null;
}

// Crear el contexto
const AuthContext = createContext<AuthContextType | undefined>(undefined);

// Hook personalizado para usar el contexto
export const useAuth = (): AuthContextType => {
  const context = useContext(AuthContext);
  if (context === undefined) {
    throw new Error('useAuth debe ser usado dentro de un AuthProvider');
  }
  return context;
};

// Props del provider
interface AuthProviderProps {
  children: ReactNode;
}

// Provider del contexto
export const AuthProvider: React.FC<AuthProviderProps> = ({ children }) => {
  const [usuario, setUsuario] = useState<Usuario | null>(null);
  const [isLoading, setIsLoading] = useState<boolean>(false);
  const [error, setError] = useState<string | null>(null);
  
  const login = async (email: string, password: string): Promise<void> => {
    try {
      setIsLoading(true);
      setError(null);
      
      // Simular llamada a API
      await new Promise(resolve => setTimeout(resolve, 1000));
      
      if (email === 'admin@test.com' && password === 'admin123') {
        const usuarioLogueado: Usuario = {
          id: 1,
          nombre: 'Administrador',
          email: 'admin@test.com',
          rol: 'admin'
        };
        setUsuario(usuarioLogueado);
      } else {
        throw new Error('Credenciales inválidas');
      }
    } catch (err) {
      setError(err instanceof Error ? err.message : 'Error de login');
    } finally {
      setIsLoading(false);
    }
  };
  
  const logout = (): void => {
    setUsuario(null);
    setError(null);
  };
  
  const value: AuthContextType = {
    usuario,
    login,
    logout,
    isLoading,
    error
  };
  
  return (
    <AuthContext.Provider value={value}>
      {children}
    </AuthContext.Provider>
  );
};

// Componente de login
const LoginForm: React.FC = () => {
  const { login, isLoading, error } = useAuth();
  const [email, setEmail] = useState<string>('');
  const [password, setPassword] = useState<string>('');
  
  const handleSubmit = async (e: React.FormEvent) => {
    e.preventDefault();
    await login(email, password);
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <h2>Iniciar Sesión</h2>
      {error && <div className="error">{error}</div>}
      
      <div>
        <label htmlFor="email">Email:</label>
        <input 
          id="email"
          type="email"
          value={email}
          onChange={(e) => setEmail(e.target.value)}
          required
        />
      </div>
      
      <div>
        <label htmlFor="password">Contraseña:</label>
        <input 
          id="password"
          type="password"
          value={password}
          onChange={(e) => setPassword(e.target.value)}
          required
        />
      </div>
      
      <button type="submit" disabled={isLoading}>
        {isLoading ? 'Iniciando sesión...' : 'Iniciar sesión'}
      </button>
      
      <p>Prueba con: admin@test.com / admin123</p>
    </form>
  );
};

// Componente principal
const App: React.FC = () => {
  const { usuario, logout } = useAuth();
  
  if (!usuario) {
    return <LoginForm />;
  }
  
  return (
    <div>
      <header>
        <h1>Bienvenido, {usuario.nombre}</h1>
        <p>Rol: {usuario.rol}</p>
        <button onClick={logout}>Cerrar sesión</button>
      </header>
      
      <main>
        <h2>Dashboard</h2>
        <p>Contenido protegido para usuarios autenticados</p>
      </main>
    </div>
  );
};

// App principal con provider
const AppWithAuth: React.FC = () => {
  return (
    <AuthProvider>
      <App />
    </AuthProvider>
  );
};

export default AppWithAuth;
```

### 2. Context Complejo con useReducer

```tsx
import React, { createContext, useContext, useReducer, ReactNode } from 'react';

// Tipos para el carrito de compras
interface Producto {
  id: number;
  nombre: string;
  precio: number;
  imagen: string;
}

interface ItemCarrito extends Producto {
  cantidad: number;
}

interface CarritoState {
  items: ItemCarrito[];
  total: number;
  descuento: number;
  isOpen: boolean;
}

type CarritoAction =
  | { type: 'AGREGAR_ITEM'; payload: Producto }
  | { type: 'REMOVER_ITEM'; payload: number }
  | { type: 'ACTUALIZAR_CANTIDAD'; payload: { id: number; cantidad: number } }
  | { type: 'LIMPIAR_CARRITO' }
  | { type: 'APLICAR_DESCUENTO'; payload: number }
  | { type: 'TOGGLE_CARRITO' };

// Reducer del carrito
const carritoReducer = (state: CarritoState, action: CarritoAction): CarritoState => {
  switch (action.type) {
    case 'AGREGAR_ITEM': {
      const itemExistente = state.items.find(item => item.id === action.payload.id);
      
      if (itemExistente) {
        const itemsActualizados = state.items.map(item =>
          item.id === action.payload.id
            ? { ...item, cantidad: item.cantidad + 1 }
            : item
        );
        return {
          ...state,
          items: itemsActualizados,
          total: calcularTotal(itemsActualizados, state.descuento)
        };
      } else {
        const nuevosItems = [...state.items, { ...action.payload, cantidad: 1 }];
        return {
          ...state,
          items: nuevosItems,
          total: calcularTotal(nuevosItems, state.descuento)
        };
      }
    }
    
    case 'REMOVER_ITEM': {
      const itemsFiltrados = state.items.filter(item => item.id !== action.payload);
      return {
        ...state,
        items: itemsFiltrados,
        total: calcularTotal(itemsFiltrados, state.descuento)
      };
    }
    
    case 'ACTUALIZAR_CANTIDAD': {
      const itemsActualizados = state.items.map(item =>
        item.id === action.payload.id
          ? { ...item, cantidad: action.payload.cantidad }
          : item
      ).filter(item => item.cantidad > 0);
      
      return {
        ...state,
        items: itemsActualizados,
        total: calcularTotal(itemsActualizados, state.descuento)
      };
    }
    
    case 'LIMPIAR_CARRITO':
      return {
        ...state,
        items: [],
        total: 0,
        descuento: 0
      };
    
    case 'APLICAR_DESCUENTO':
      return {
        ...state,
        descuento: action.payload,
        total: calcularTotal(state.items, action.payload)
      };
    
    case 'TOGGLE_CARRITO':
      return {
        ...state,
        isOpen: !state.isOpen
      };
    
    default:
      return state;
  }
};

// Función auxiliar para calcular total
const calcularTotal = (items: ItemCarrito[], descuento: number): number => {
  const subtotal = items.reduce((acc, item) => acc + (item.precio * item.cantidad), 0);
  return subtotal - (subtotal * descuento / 100);
};

// Tipo del contexto
interface CarritoContextType {
  state: CarritoState;
  agregarItem: (producto: Producto) => void;
  removerItem: (id: number) => void;
  actualizarCantidad: (id: number, cantidad: number) => void;
  limpiarCarrito: () => void;
  aplicarDescuento: (descuento: number) => void;
  toggleCarrito: () => void;
}

// Crear contexto
const CarritoContext = createContext<CarritoContextType | undefined>(undefined);

// Hook personalizado
export const useCarrito = (): CarritoContextType => {
  const context = useContext(CarritoContext);
  if (context === undefined) {
    throw new Error('useCarrito debe ser usado dentro de un CarritoProvider');
  }
  return context;
};

// Estado inicial
const estadoInicial: CarritoState = {
  items: [],
  total: 0,
  descuento: 0,
  isOpen: false
};

// Provider
interface CarritoProviderProps {
  children: ReactNode;
}

export const CarritoProvider: React.FC<CarritoProviderProps> = ({ children }) => {
  const [state, dispatch] = useReducer(carritoReducer, estadoInicial);
  
  const agregarItem = (producto: Producto) => {
    dispatch({ type: 'AGREGAR_ITEM', payload: producto });
  };
  
  const removerItem = (id: number) => {
    dispatch({ type: 'REMOVER_ITEM', payload: id });
  };
  
  const actualizarCantidad = (id: number, cantidad: number) => {
    dispatch({ type: 'ACTUALIZAR_CANTIDAD', payload: { id, cantidad } });
  };
  
  const limpiarCarrito = () => {
    dispatch({ type: 'LIMPIAR_CARRITO' });
  };
  
  const aplicarDescuento = (descuento: number) => {
    dispatch({ type: 'APLICAR_DESCUENTO', payload: descuento });
  };
  
  const toggleCarrito = () => {
    dispatch({ type: 'TOGGLE_CARRITO' });
  };
  
  const value: CarritoContextType = {
    state,
    agregarItem,
    removerItem,
    actualizarCantidad,
    limpiarCarrito,
    aplicarDescuento,
    toggleCarrito
  };
  
  return (
    <CarritoContext.Provider value={value}>
      {children}
    </CarritoContext.Provider>
  );
};
```

---

## 🔄 Redux con TypeScript

### 1. Configuración de Redux Toolkit

```bash
# Instalar dependencias
npm install @reduxjs/toolkit react-redux
npm install --save-dev @types/react-redux
```

```tsx
// store/index.ts
import { configureStore } from '@reduxjs/toolkit';
import authSlice from './slices/authSlice';
import todosSlice from './slices/todosSlice';

export const store = configureStore({
  reducer: {
    auth: authSlice,
    todos: todosSlice,
  },
});

export type RootState = ReturnType<typeof store.getState>;
export type AppDispatch = typeof store.dispatch;
```

```tsx
// hooks/redux.ts
import { TypedUseSelectorHook, useDispatch, useSelector } from 'react-redux';
import type { RootState, AppDispatch } from '../store';

export const useAppDispatch = () => useDispatch<AppDispatch>();
export const useAppSelector: TypedUseSelectorHook<RootState> = useSelector;
```

### 2. Slice de Autenticación

```tsx
// store/slices/authSlice.ts
import { createSlice, createAsyncThunk, PayloadAction } from '@reduxjs/toolkit';

interface Usuario {
  id: number;
  nombre: string;
  email: string;
  rol: 'admin' | 'usuario';
}

interface AuthState {
  usuario: Usuario | null;
  token: string | null;
  isLoading: boolean;
  error: string | null;
}

const initialState: AuthState = {
  usuario: null,
  token: null,
  isLoading: false,
  error: null,
};

// Async thunk para login
export const loginAsync = createAsyncThunk(
  'auth/login',
  async (credentials: { email: string; password: string }, { rejectWithValue }) => {
    try {
      // Simular API call
      await new Promise(resolve => setTimeout(resolve, 1000));
      
      if (credentials.email === 'admin@test.com' && credentials.password === 'admin123') {
        return {
          usuario: {
            id: 1,
            nombre: 'Administrador',
            email: 'admin@test.com',
            rol: 'admin' as const
          },
          token: 'fake-jwt-token'
        };
      } else {
        throw new Error('Credenciales inválidas');
      }
    } catch (error) {
      return rejectWithValue(error instanceof Error ? error.message : 'Error de login');
    }
  }
);

// Async thunk para logout
export const logoutAsync = createAsyncThunk(
  'auth/logout',
  async () => {
    // Simular limpieza de sesión
    localStorage.removeItem('token');
    return null;
  }
);

const authSlice = createSlice({
  name: 'auth',
  initialState,
  reducers: {
    clearError: (state) => {
      state.error = null;
    },
    setCredentials: (state, action: PayloadAction<{ usuario: Usuario; token: string }>) => {
      state.usuario = action.payload.usuario;
      state.token = action.payload.token;
    },
  },
  extraReducers: (builder) => {
    builder
      // Login
      .addCase(loginAsync.pending, (state) => {
        state.isLoading = true;
        state.error = null;
      })
      .addCase(loginAsync.fulfilled, (state, action) => {
        state.isLoading = false;
        state.usuario = action.payload.usuario;
        state.token = action.payload.token;
        state.error = null;
      })
      .addCase(loginAsync.rejected, (state, action) => {
        state.isLoading = false;
        state.error = action.payload as string;
      })
      // Logout
      .addCase(logoutAsync.fulfilled, (state) => {
        state.usuario = null;
        state.token = null;
        state.error = null;
      });
  },
});

export const { clearError, setCredentials } = authSlice.actions;
export default authSlice.reducer;
```

### 3. Slice de Todos

```tsx
// store/slices/todosSlice.ts
import { createSlice, createAsyncThunk, PayloadAction } from '@reduxjs/toolkit';

interface Todo {
  id: number;
  text: string;
  completed: boolean;
  createdAt: string;
}

interface TodosState {
  items: Todo[];
  filter: 'all' | 'active' | 'completed';
  isLoading: boolean;
  error: string | null;
}

const initialState: TodosState = {
  items: [],
  filter: 'all',
  isLoading: false,
  error: null,
};

// Async thunk para cargar todos
export const fetchTodos = createAsyncThunk(
  'todos/fetchTodos',
  async (_, { rejectWithValue }) => {
    try {
      // Simular API call
      await new Promise(resolve => setTimeout(resolve, 1000));
      
      const todos: Todo[] = [
        {
          id: 1,
          text: 'Aprender TypeScript',
          completed: true,
          createdAt: new Date().toISOString()
        },
        {
          id: 2,
          text: 'Configurar Redux',
          completed: false,
          createdAt: new Date().toISOString()
        }
      ];
      
      return todos;
    } catch (error) {
      return rejectWithValue('Error al cargar todos');
    }
  }
);

// Async thunk para agregar todo
export const addTodoAsync = createAsyncThunk(
  'todos/addTodo',
  async (text: string, { rejectWithValue }) => {
    try {
      // Simular API call
      await new Promise(resolve => setTimeout(resolve, 500));
      
      const newTodo: Todo = {
        id: Date.now(),
        text,
        completed: false,
        createdAt: new Date().toISOString()
      };
      
      return newTodo;
    } catch (error) {
      return rejectWithValue('Error al agregar todo');
    }
  }
);

const todosSlice = createSlice({
  name: 'todos',
  initialState,
  reducers: {
    toggleTodo: (state, action: PayloadAction<number>) => {
      const todo = state.items.find(todo => todo.id === action.payload);
      if (todo) {
        todo.completed = !todo.completed;
      }
    },
    deleteTodo: (state, action: PayloadAction<number>) => {
      state.items = state.items.filter(todo => todo.id !== action.payload);
    },
    setFilter: (state, action: PayloadAction<'all' | 'active' | 'completed'>) => {
      state.filter = action.payload;
    },
    clearCompleted: (state) => {
      state.items = state.items.filter(todo => !todo.completed);
    },
  },
  extraReducers: (builder) => {
    builder
      // Fetch todos
      .addCase(fetchTodos.pending, (state) => {
        state.isLoading = true;
        state.error = null;
      })
      .addCase(fetchTodos.fulfilled, (state, action) => {
        state.isLoading = false;
        state.items = action.payload;
      })
      .addCase(fetchTodos.rejected, (state, action) => {
        state.isLoading = false;
        state.error = action.payload as string;
      })
      // Add todo
      .addCase(addTodoAsync.pending, (state) => {
        state.isLoading = true;
      })
      .addCase(addTodoAsync.fulfilled, (state, action) => {
        state.isLoading = false;
        state.items.push(action.payload);
      })
      .addCase(addTodoAsync.rejected, (state, action) => {
        state.isLoading = false;
        state.error = action.payload as string;
      });
  },
});

export const { toggleTodo, deleteTodo, setFilter, clearCompleted } = todosSlice.actions;
export default todosSlice.reducer;
```

### 4. Componentes con Redux

```tsx
// components/TodoApp.tsx
import React, { useEffect, useState } from 'react';
import { useAppDispatch, useAppSelector } from '../hooks/redux';
import {
  fetchTodos,
  addTodoAsync,
  toggleTodo,
  deleteTodo,
  setFilter,
  clearCompleted
} from '../store/slices/todosSlice';

const TodoApp: React.FC = () => {
  const dispatch = useAppDispatch();
  const { items, filter, isLoading, error } = useAppSelector(state => state.todos);
  const [inputValue, setInputValue] = useState<string>('');
  
  useEffect(() => {
    dispatch(fetchTodos());
  }, [dispatch]);
  
  const filteredTodos = items.filter(todo => {
    switch (filter) {
      case 'active':
        return !todo.completed;
      case 'completed':
        return todo.completed;
      default:
        return true;
    }
  });
  
  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    if (inputValue.trim()) {
      dispatch(addTodoAsync(inputValue.trim()));
      setInputValue('');
    }
  };
  
  const handleToggle = (id: number) => {
    dispatch(toggleTodo(id));
  };
  
  const handleDelete = (id: number) => {
    dispatch(deleteTodo(id));
  };
  
  const handleFilterChange = (newFilter: 'all' | 'active' | 'completed') => {
    dispatch(setFilter(newFilter));
  };
  
  const handleClearCompleted = () => {
    dispatch(clearCompleted());
  };
  
  if (error) {
    return <div className="error">Error: {error}</div>;
  }
  
  return (
    <div className="todo-app">
      <h1>Todo App con Redux</h1>
      
      <form onSubmit={handleSubmit}>
        <input 
          type="text"
          value={inputValue}
          onChange={(e) => setInputValue(e.target.value)}
          placeholder="Agregar nueva tarea..."
          disabled={isLoading}
        />
        <button type="submit" disabled={isLoading || !inputValue.trim()}>
          {isLoading ? 'Agregando...' : 'Agregar'}
        </button>
      </form>
      
      <div className="filters">
        <button 
          onClick={() => handleFilterChange('all')}
          className={filter === 'all' ? 'active' : ''}
        >
          Todas ({items.length})
        </button>
        <button 
          onClick={() => handleFilterChange('active')}
          className={filter === 'active' ? 'active' : ''}
        >
          Activas ({items.filter(t => !t.completed).length})
        </button>
        <button 
          onClick={() => handleFilterChange('completed')}
          className={filter === 'completed' ? 'active' : ''}
        >
          Completadas ({items.filter(t => t.completed).length})
        </button>
      </div>
      
      <ul className="todo-list">
        {filteredTodos.map(todo => (
          <li key={todo.id} className={todo.completed ? 'completed' : ''}>
            <input 
              type="checkbox"
              checked={todo.completed}
              onChange={() => handleToggle(todo.id)}
            />
            <span>{todo.text}</span>
            <button 
              onClick={() => handleDelete(todo.id)}
              className="delete-btn"
            >
              ×
            </button>
          </li>
        ))}
      </ul>
      
      {items.some(todo => todo.completed) && (
        <button onClick={handleClearCompleted} className="clear-completed">
          Limpiar completadas
        </button>
      )}
    </div>
  );
};

export default TodoApp;
```

---

## 🧪 Testing con TypeScript

### 1. Configuración de Testing

```bash
# Instalar dependencias de testing
npm install --save-dev @testing-library/react @testing-library/jest-dom @testing-library/user-event
npm install --save-dev @types/jest
```

```tsx
// setupTests.ts
import '@testing-library/jest-dom';
```

### 2. Testing de Componentes

```tsx
// __tests__/Button.test.tsx
import React from 'react';
import { render, screen, fireEvent } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import Button from '../components/Button';

// Componente a testear
interface ButtonProps {
  children: React.ReactNode;
  onClick?: () => void;
  variant?: 'primary' | 'secondary';
  disabled?: boolean;
}

const Button: React.FC<ButtonProps> = ({
  children,
  onClick,
  variant = 'primary',
  disabled = false
}) => {
  return (
    <button
      className={`btn btn--${variant}`}
      onClick={onClick}
      disabled={disabled}
    >
      {children}
    </button>
  );
};

// Tests
describe('Button Component', () => {
  test('renderiza correctamente con texto', () => {
    render(<Button>Click me</Button>);
    
    const button = screen.getByRole('button', { name: /click me/i });
    expect(button).toBeInTheDocument();
  });
  
  test('aplica la clase CSS correcta según variant', () => {
    const { rerender } = render(<Button variant="primary">Primary</Button>);
    
    let button = screen.getByRole('button');
    expect(button).toHaveClass('btn--primary');
    
    rerender(<Button variant="secondary">Secondary</Button>);
    button = screen.getByRole('button');
    expect(button).toHaveClass('btn--secondary');
  });
  
  test('llama onClick cuando se hace click', async () => {
    const user = userEvent.setup();
    const handleClick = jest.fn();
    
    render(<Button onClick={handleClick}>Click me</Button>);
    
    const button = screen.getByRole('button');
    await user.click(button);
    
    expect(handleClick).toHaveBeenCalledTimes(1);
  });
  
  test('está deshabilitado cuando disabled es true', () => {
    render(<Button disabled>Disabled</Button>);
    
    const button = screen.getByRole('button');
    expect(button).toBeDisabled();
  });
  
  test('no llama onClick cuando está deshabilitado', async () => {
    const user = userEvent.setup();
    const handleClick = jest.fn();
    
    render(<Button onClick={handleClick} disabled>Disabled</Button>);
    
    const button = screen.getByRole('button');
    await user.click(button);
    
    expect(handleClick).not.toHaveBeenCalled();
  });
});
```

### 3. Testing de Hooks Personalizados

```tsx
// __tests__/useCounter.test.tsx
import { renderHook, act } from '@testing-library/react';

// Hook a testear
import { useState, useCallback } from 'react';

interface UseCounterReturn {
  count: number;
  increment: () => void;
  decrement: () => void;
  reset: () => void;
  setCount: (value: number) => void;
}

const useCounter = (initialValue: number = 0): UseCounterReturn => {
  const [count, setCount] = useState<number>(initialValue);
  
  const increment = useCallback(() => {
    setCount(prev => prev + 1);
  }, []);
  
  const decrement = useCallback(() => {
    setCount(prev => prev - 1);
  }, []);
  
  const reset = useCallback(() => {
    setCount(initialValue);
  }, [initialValue]);
  
  return {
    count,
    increment,
    decrement,
    reset,
    setCount
  };
};

// Tests
describe('useCounter Hook', () => {
  test('inicializa con valor por defecto', () => {
    const { result } = renderHook(() => useCounter());
    
    expect(result.current.count).toBe(0);
  });
  
  test('inicializa con valor personalizado', () => {
    const { result } = renderHook(() => useCounter(10));
    
    expect(result.current.count).toBe(10);
  });
  
  test('incrementa el contador', () => {
    const { result } = renderHook(() => useCounter(0));
    
    act(() => {
      result.current.increment();
    });
    
    expect(result.current.count).toBe(1);
  });
  
  test('decrementa el contador', () => {
    const { result } = renderHook(() => useCounter(5));
    
    act(() => {
      result.current.decrement();
    });
    
    expect(result.current.count).toBe(4);
  });
  
  test('resetea al valor inicial', () => {
    const { result } = renderHook(() => useCounter(10));
    
    act(() => {
      result.current.increment();
      result.current.increment();
    });
    
    expect(result.current.count).toBe(12);
    
    act(() => {
      result.current.reset();
    });
    
    expect(result.current.count).toBe(10);
  });
  
  test('establece valor específico', () => {
    const { result } = renderHook(() => useCounter());
    
    act(() => {
      result.current.setCount(25);
    });
    
    expect(result.current.count).toBe(25);
  });
});
```

### 4. Testing de Context

```tsx
// __tests__/AuthContext.test.tsx
import React from 'react';
import { render, screen, waitFor } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import { AuthProvider, useAuth } from '../contexts/AuthContext';

// Componente de prueba
const TestComponent: React.FC = () => {
  const { usuario, login, logout, isLoading, error } = useAuth();
  
  return (
    <div>
      {usuario ? (
        <div>
          <p>Bienvenido, {usuario.nombre}</p>
          <button onClick={logout}>Logout</button>
        </div>
      ) : (
        <div>
          <p>No autenticado</p>
          <button onClick={() => login('admin@test.com', 'admin123')}>
            Login
          </button>
          <button onClick={() => login('wrong@email.com', 'wrong')}>
            Login Wrong
          </button>
        </div>
      )}
      {isLoading && <p>Cargando...</p>}
      {error && <p>Error: {error}</p>}
    </div>
  );
};

const renderWithProvider = () => {
  return render(
    <AuthProvider>
      <TestComponent />
    </AuthProvider>
  );
};

describe('AuthContext', () => {
  test('estado inicial sin usuario', () => {
    renderWithProvider();
    
    expect(screen.getByText('No autenticado')).toBeInTheDocument();
    expect(screen.getByRole('button', { name: /login/i })).toBeInTheDocument();
  });
  
  test('login exitoso', async () => {
    const user = userEvent.setup();
    renderWithProvider();
    
    const loginButton = screen.getByRole('button', { name: 'Login' });
    await user.click(loginButton);
    
    expect(screen.getByText('Cargando...')).toBeInTheDocument();
    
    await waitFor(() => {
      expect(screen.getByText('Bienvenido, Administrador')).toBeInTheDocument();
    });
    
    expect(screen.getByRole('button', { name: /logout/i })).toBeInTheDocument();
  });
  
  test('login fallido', async () => {
    const user = userEvent.setup();
    renderWithProvider();
    
    const loginWrongButton = screen.getByRole('button', { name: 'Login Wrong' });
    await user.click(loginWrongButton);
    
    await waitFor(() => {
      expect(screen.getByText('Error: Credenciales inválidas')).toBeInTheDocument();
    });
    
    expect(screen.getByText('No autenticado')).toBeInTheDocument();
  });
  
  test('logout', async () => {
    const user = userEvent.setup();
    renderWithProvider();
    
    // Primero hacer login
    const loginButton = screen.getByRole('button', { name: 'Login' });
    await user.click(loginButton);
    
    await waitFor(() => {
      expect(screen.getByText('Bienvenido, Administrador')).toBeInTheDocument();
    });
    
    // Luego hacer logout
    const logoutButton = screen.getByRole('button', { name: /logout/i });
    await user.click(logoutButton);
    
    expect(screen.getByText('No autenticado')).toBeInTheDocument();
  });
});
```

---

## 🎯 Ejercicios Prácticos

### Ejercicio 1: Sistema de Gestión de Tareas

Crea una aplicación completa de gestión de tareas con las siguientes características:

**Requisitos:**
- Crear, editar, eliminar y marcar tareas como completadas
- Filtrar tareas por estado (todas, activas, completadas)
- Categorías de tareas con colores
- Fechas de vencimiento
- Búsqueda de tareas
- Persistencia en localStorage
- Validación de formularios
- Testing completo

**Tipos TypeScript requeridos:**
```tsx
interface Tarea {
  id: string;
  titulo: string;
  descripcion: string;
  categoria: Categoria;
  fechaVencimiento: Date;
  completada: boolean;
  prioridad: 'baja' | 'media' | 'alta';
  createdAt: Date;
  updatedAt: Date;
}

interface Categoria {
  id: string;
  nombre: string;
  color: string;
}

interface FiltrosTareas {
  estado: 'todas' | 'activas' | 'completadas';
  categoria?: string;
  prioridad?: 'baja' | 'media' | 'alta';
  busqueda: string;
}
```

### Ejercicio 2: E-commerce con Carrito

Desarrolla una tienda online con:

**Funcionalidades:**
- Catálogo de productos con filtros
- Carrito de compras
- Gestión de usuarios
- Proceso de checkout
- Historial de pedidos
- Sistema de reviews

**Tipos requeridos:**
```tsx
interface Producto {
  id: string;
  nombre: string;
  descripcion: string;
  precio: number;
  categoria: string;
  imagenes: string[];
  stock: number;
  rating: number;
  reviews: Review[];
}

interface ItemCarrito {
  producto: Producto;
  cantidad: number;
}

interface Pedido {
  id: string;
  usuario: Usuario;
  items: ItemCarrito[];
  total: number;
  estado: 'pendiente' | 'procesando' | 'enviado' | 'entregado';
  fechaPedido: Date;
  direccionEnvio: Direccion;
}
```

### Ejercicio 3: Dashboard Analítico

Construye un dashboard con:

**Características:**
- Gráficos interactivos
- Filtros de fecha
- Métricas en tiempo real
- Exportación de datos
- Responsive design

---

## 📚 Recursos Adicionales

### Documentación Oficial
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [React TypeScript Cheatsheet](https://react-typescript-cheatsheet.netlify.app/)
- [Redux Toolkit con TypeScript](https://redux-toolkit.js.org/usage/usage-with-typescript)

### Herramientas Útiles
- **ESLint + Prettier**: Linting y formateo
- **Husky**: Git hooks
- **Storybook**: Documentación de componentes
- **React DevTools**: Debugging
- **Redux DevTools**: Debugging de estado

### Mejores Prácticas
1. **Tipado estricto**: Usa `strict: true` en tsconfig.json
2. **Interfaces vs Types**: Prefiere interfaces para objetos
3. **Naming conventions**: PascalCase para componentes, camelCase para variables
4. **Organización**: Estructura de carpetas clara
5. **Testing**: Cobertura mínima del 80%
6. **Performance**: Usa React.memo, useMemo, useCallback cuando sea necesario

---

## 🎓 Conclusión

Esta guía te ha proporcionado una base sólida para trabajar con TypeScript y React. Desde los conceptos básicos hasta patrones avanzados, ahora tienes las herramientas necesarias para construir aplicaciones robustas y escalables.

**Próximos pasos recomendados:**
1. Practica con los ejercicios propuestos
2. Contribuye a proyectos open source
3. Mantente actualizado con las nuevas versiones
4. Explora librerías complementarias como React Query, Zustand, etc.

¡Feliz coding! 🚀
```
