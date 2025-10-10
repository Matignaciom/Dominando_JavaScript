# 📚 Guía Completa de Aprendizaje React

## 🎯 Introducción

React es una biblioteca de JavaScript popular para construir interfaces de usuario reutilizables y basadas en componentes para páginas web o aplicaciones. React combina HTML con funcionalidad de JavaScript en su propio lenguaje de marcado llamado JSX. También facilita la gestión del flujo de datos en toda la aplicación.

### ¿Qué aprenderás?
- ✅ Crear diferentes componentes de React
- ✅ Manejar datos en forma de state y props
- ✅ Usar diferentes métodos del ciclo de vida como componentDidMount
- ✅ Renderizado condicional y manejo de listas
- ✅ Redux para gestión de estado global
- ✅ Integración de React con Redux
- ✅ Mejores prácticas y patrones modernos

---

## 🚀 Configuración Inicial

### Prerrequisitos
- Node.js (versión 14 o superior)
- npm o yarn
- Editor de código (VS Code recomendado)

### Crear un Nuevo Proyecto React

```bash
# Opción 1: Create React App (recomendado para principiantes)
npx create-react-app mi-app-react
cd mi-app-react
npm start

# Opción 2: Vite (más rápido)
npm create vite@latest mi-app-react -- --template react
cd mi-app-react
npm install
npm run dev
```

### Estructura de Proyecto Recomendada

```
mi-app-react/
├── public/
│   ├── index.html
│   └── favicon.ico
├── src/
│   ├── components/
│   │   ├── Header.js
│   │   └── Footer.js
│   ├── pages/
│   │   ├── Home.js
│   │   └── About.js
│   ├── hooks/
│   │   └── useCustomHook.js
│   ├── utils/
│   │   └── helpers.js
│   ├── App.js
│   ├── App.css
│   └── index.js
├── package.json
└── README.md
```

### Extensiones de VS Code Recomendadas
- ES7+ React/Redux/React-Native snippets
- Bracket Pair Colorizer
- Auto Rename Tag
- Prettier - Code formatter

---

## 📋 Tabla de Contenidos

1. [JSX - JavaScript XML](#jsx---javascript-xml)
2. [Componentes](#componentes)
3. [Props](#props)
4. [State y Ciclo de Vida](#state-y-ciclo-de-vida)
5. [Eventos y Formularios](#eventos-y-formularios)
6. [Renderizado Condicional](#renderizado-condicional)
7. [Listas y Keys](#listas-y-keys)
8. [Estilos en React](#estilos-en-react)
9. [Hooks Modernos](#hooks-modernos)
10. [Redux](#redux)
11. [React + Redux](#react--redux)
12. [Ejercicios Prácticos](#ejercicios-prácticos)
13. [Troubleshooting](#troubleshooting)

---

## 🏗️ JSX - JavaScript XML

JSX es una extensión de sintaxis para JavaScript que permite escribir elementos HTML dentro de JavaScript.

### 1. Crear un Elemento JSX Simple

```jsx
// Elemento JSX básico
const element = <h1>¡Hola, mundo!</h1>;

// Renderizar en el DOM
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(element, document.getElementById('root'));
```

### 2. Crear un Elemento JSX Complejo

```jsx
// JSX con múltiples elementos (debe tener un elemento padre)
const complexElement = (
  <div>
    <h1>Mi Aplicación React</h1>
    <p>Esta es una aplicación construida con React.</p>
    <ul>
      <li>Elemento 1</li>
      <li>Elemento 2</li>
      <li>Elemento 3</li>
    </ul>
  </div>
);

// Alternativa con React.Fragment
const fragmentElement = (
  <React.Fragment>
    <h1>Título</h1>
    <p>Párrafo</p>
  </React.Fragment>
);

// Sintaxis corta de Fragment
const shortFragment = (
  <>
    <h1>Título</h1>
    <p>Párrafo</p>
  </>
);
```

### 3. Comentarios en JSX

```jsx
const elementWithComments = (
  <div>
    {/* Este es un comentario en JSX */}
    <h1>Título Principal</h1>
    {/* 
      Los comentarios en JSX deben estar
      dentro de llaves y usar la sintaxis
      de comentarios de JavaScript
    */}
    <p>Contenido del párrafo</p>
  </div>
);
```

### 4. Clases CSS en JSX

```jsx
// En JSX usamos 'className' en lugar de 'class'
const styledElement = (
  <div className="container">
    <h1 className="title">Título con Estilo</h1>
    <p className="description">Descripción con clase CSS</p>
  </div>
);
```

### 5. Etiquetas Auto-cerradas

```jsx
// Etiquetas que se auto-cierran deben incluir la barra diagonal
const selfClosingTags = (
  <div>
    <img src="imagen.jpg" alt="Descripción" />
    <input type="text" placeholder="Escribe aquí" />
    <br />
    <hr />
  </div>
);
```

### 6. Expresiones JavaScript en JSX

```jsx
const nombre = 'Juan';
const edad = 25;

const elementWithJS = (
  <div>
    <h1>Hola, {nombre}!</h1>
    <p>Tienes {edad} años</p>
    <p>El próximo año tendrás {edad + 1} años</p>
    <p>Fecha actual: {new Date().toLocaleDateString()}</p>
  </div>
);
```

---

## 🧩 Componentes

Los componentes son la base de React. Permiten dividir la UI en piezas independientes y reutilizables.

### 1. Componente Funcional Simple

```jsx
// Componente funcional básico
function Saludo() {
  return <h1>¡Hola desde un componente!</h1>;
}

// Sintaxis con arrow function
const SaludoArrow = () => {
  return <h1>¡Hola desde arrow function!</h1>;
};

// Sintaxis corta (sin return explícito)
const SaludoCorto = () => <h1>¡Hola corto!</h1>;
```

### 2. Componente de Clase

```jsx
import React, { Component } from 'react';

class SaludoClase extends Component {
  render() {
    return <h1>¡Hola desde componente de clase!</h1>;
  }
}
```

### 3. Composición de Componentes

```jsx
// Componente Header
function Header() {
  return (
    <header>
      <h1>Mi Sitio Web</h1>
      <nav>
        <ul>
          <li>Inicio</li>
          <li>Acerca de</li>
          <li>Contacto</li>
        </ul>
      </nav>
    </header>
  );
}

// Componente Main
function Main() {
  return (
    <main>
      <h2>Contenido Principal</h2>
      <p>Este es el contenido principal de la página.</p>
    </main>
  );
}

// Componente Footer
function Footer() {
  return (
    <footer>
      <p>&copy; 2024 Mi Sitio Web. Todos los derechos reservados.</p>
    </footer>
  );
}

// Componente App que compone todos
function App() {
  return (
    <div className="app">
      <Header />
      <Main />
      <Footer />
    </div>
  );
}
```

### 4. Componentes Anidados

```jsx
// Componente Producto
function Producto({ nombre, precio, imagen }) {
  return (
    <div className="producto">
      <img src={imagen} alt={nombre} />
      <h3>{nombre}</h3>
      <p>${precio}</p>
    </div>
  );
}

// Componente ListaProductos
function ListaProductos() {
  const productos = [
    { id: 1, nombre: 'Laptop', precio: 999, imagen: 'laptop.jpg' },
    { id: 2, nombre: 'Mouse', precio: 25, imagen: 'mouse.jpg' },
    { id: 3, nombre: 'Teclado', precio: 75, imagen: 'teclado.jpg' }
  ];

  return (
    <div className="lista-productos">
      <h2>Nuestros Productos</h2>
      {productos.map(producto => (
        <Producto
          key={producto.id}
          nombre={producto.nombre}
          precio={producto.precio}
          imagen={producto.imagen}
        />
      ))}
    </div>
  );
}
```

---

## 📦 Props

Las props (propiedades) son la forma de pasar datos de un componente padre a un componente hijo.

### 1. Props Básicas

```jsx
// Componente que recibe props
function Saludo(props) {
  return <h1>¡Hola, {props.nombre}!</h1>;
}

// Uso del componente
function App() {
  return (
    <div>
      <Saludo nombre="Ana" />
      <Saludo nombre="Carlos" />
      <Saludo nombre="María" />
    </div>
  );
}
```

### 2. Destructuring de Props

```jsx
// Destructuring en los parámetros
function Perfil({ nombre, edad, profesion }) {
  return (
    <div className="perfil">
      <h2>{nombre}</h2>
      <p>Edad: {edad} años</p>
      <p>Profesión: {profesion}</p>
    </div>
  );
}

// Uso
function App() {
  return (
    <Perfil 
      nombre="Laura" 
      edad={28} 
      profesion="Desarrolladora" 
    />
  );
}
```

### 3. Props por Defecto

```jsx
// Con defaultProps (componentes de clase)
class Boton extends React.Component {
  render() {
    return (
      <button className={this.props.tipo}>
        {this.props.texto}
      </button>
    );
  }
}

Boton.defaultProps = {
  tipo: 'primary',
  texto: 'Hacer clic'
};

// Con valores por defecto en parámetros (componentes funcionales)
function BotonFuncional({ tipo = 'primary', texto = 'Hacer clic' }) {
  return (
    <button className={tipo}>
      {texto}
    </button>
  );
}
```

### 4. Validación de Props con PropTypes

```jsx
import PropTypes from 'prop-types';

function Usuario({ nombre, edad, email, activo }) {
  return (
    <div className={`usuario ${activo ? 'activo' : 'inactivo'}`}>
      <h3>{nombre}</h3>
      <p>Edad: {edad}</p>
      <p>Email: {email}</p>
    </div>
  );
}

Usuario.propTypes = {
  nombre: PropTypes.string.isRequired,
  edad: PropTypes.number.isRequired,
  email: PropTypes.string.isRequired,
  activo: PropTypes.bool
};

Usuario.defaultProps = {
  activo: true
};
```

### 5. Pasar Arrays como Props

```jsx
function ListaTareas({ tareas }) {
  return (
    <ul>
      {tareas.map((tarea, index) => (
        <li key={index}>{tarea}</li>
      ))}
    </ul>
  );
}

function App() {
  const misTareas = [
    'Estudiar React',
    'Hacer ejercicio',
    'Leer un libro',
    'Cocinar cena'
  ];

  return <ListaTareas tareas={misTareas} />;
}
```

### 6. Props Children

```jsx
// Componente que usa children
function Tarjeta({ children, titulo }) {
  return (
    <div className="tarjeta">
      <h2>{titulo}</h2>
      <div className="contenido">
        {children}
      </div>
    </div>
  );
}

// Uso de children
function App() {
  return (
    <Tarjeta titulo="Mi Tarjeta">
      <p>Este contenido se pasa como children.</p>
      <button>Botón dentro de la tarjeta</button>
    </Tarjeta>
  );
}
```

---

## 🔄 State y Ciclo de Vida

El state permite que los componentes mantengan y actualicen datos que pueden cambiar con el tiempo.

### 1. State con Componentes de Clase

```jsx
import React, { Component } from 'react';

class Contador extends Component {
  constructor(props) {
    super(props);
    // Inicializar state
    this.state = {
      count: 0,
      mensaje: 'Contador inicial'
    };
  }

  // Método para incrementar
  incrementar = () => {
    this.setState({
      count: this.state.count + 1,
      mensaje: `Contador: ${this.state.count + 1}`
    });
  }

  // Método para decrementar
  decrementar = () => {
    this.setState(prevState => ({
      count: prevState.count - 1,
      mensaje: `Contador: ${prevState.count - 1}`
    }));
  }

  render() {
    return (
      <div>
        <h2>{this.state.mensaje}</h2>
        <p>Valor actual: {this.state.count}</p>
        <button onClick={this.incrementar}>+</button>
        <button onClick={this.decrementar}>-</button>
      </div>
    );
  }
}
```

### 2. State con Hooks (useState)

```jsx
import React, { useState } from 'react';

function ContadorFuncional() {
  // Declarar variable de state
  const [count, setCount] = useState(0);
  const [mensaje, setMensaje] = useState('Contador inicial');

  const incrementar = () => {
    setCount(count + 1);
    setMensaje(`Contador: ${count + 1}`);
  };

  const decrementar = () => {
    setCount(prevCount => {
      const nuevoCount = prevCount - 1;
      setMensaje(`Contador: ${nuevoCount}`);
      return nuevoCount;
    });
  };

  return (
    <div>
      <h2>{mensaje}</h2>
      <p>Valor actual: {count}</p>
      <button onClick={incrementar}>+</button>
      <button onClick={decrementar}>-</button>
    </div>
  );
}
```

### 3. Métodos del Ciclo de Vida

```jsx
import React, { Component } from 'react';

class ComponenteConCicloVida extends Component {
  constructor(props) {
    super(props);
    this.state = {
      datos: null,
      cargando: true
    };
    console.log('1. Constructor ejecutado');
  }

  // Se ejecuta después de que el componente se monta
  componentDidMount() {
    console.log('3. componentDidMount ejecutado');
    // Simular carga de datos
    setTimeout(() => {
      this.setState({
        datos: 'Datos cargados desde la API',
        cargando: false
      });
    }, 2000);
  }

  // Se ejecuta cuando el componente se actualiza
  componentDidUpdate(prevProps, prevState) {
    console.log('4. componentDidUpdate ejecutado');
    if (prevState.cargando !== this.state.cargando) {
      console.log('El estado de carga cambió');
    }
  }

  // Se ejecuta antes de que el componente se desmonte
  componentWillUnmount() {
    console.log('5. componentWillUnmount ejecutado');
    // Limpiar timers, suscripciones, etc.
  }

  render() {
    console.log('2. Render ejecutado');
    return (
      <div>
        <h2>Componente con Ciclo de Vida</h2>
        {this.state.cargando ? (
          <p>Cargando...</p>
        ) : (
          <p>{this.state.datos}</p>
        )}
      </div>
    );
  }
}
```

### 4. useEffect Hook (Equivalente al Ciclo de Vida)

```jsx
import React, { useState, useEffect } from 'react';

function ComponenteConUseEffect() {
  const [datos, setDatos] = useState(null);
  const [cargando, setCargando] = useState(true);

  // Equivalente a componentDidMount
  useEffect(() => {
    console.log('Componente montado');
    
    // Simular carga de datos
    const timer = setTimeout(() => {
      setDatos('Datos cargados desde la API');
      setCargando(false);
    }, 2000);

    // Cleanup (equivalente a componentWillUnmount)
    return () => {
      console.log('Limpiando timer');
      clearTimeout(timer);
    };
  }, []); // Array vacío = solo se ejecuta una vez

  // Equivalente a componentDidUpdate para 'cargando'
  useEffect(() => {
    console.log('Estado de carga cambió:', cargando);
  }, [cargando]); // Se ejecuta cuando 'cargando' cambia

  return (
    <div>
      <h2>Componente con useEffect</h2>
      {cargando ? (
        <p>Cargando...</p>
      ) : (
        <p>{datos}</p>
      )}
    </div>
  );
}
```

---

## 🎯 Eventos y Formularios

React maneja eventos de forma sintética, proporcionando una API consistente entre navegadores.

### 1. Manejo Básico de Eventos

```jsx
function BotonConEventos() {
  const manejarClick = (e) => {
    e.preventDefault(); // Prevenir comportamiento por defecto
    console.log('Botón clickeado!');
    console.log('Evento:', e);
  };

  const manejarMouseOver = () => {
    console.log('Mouse sobre el botón');
  };

  return (
    <button 
      onClick={manejarClick}
      onMouseOver={manejarMouseOver}
    >
      Hacer clic
    </button>
  );
}
```

### 2. Formularios Controlados

```jsx
import React, { useState } from 'react';

function FormularioControlado() {
  const [formData, setFormData] = useState({
    nombre: '',
    email: '',
    mensaje: '',
    pais: 'mexico',
    acepta: false
  });

  const manejarCambio = (e) => {
    const { name, value, type, checked } = e.target;
    setFormData(prevState => ({
      ...prevState,
      [name]: type === 'checkbox' ? checked : value
    }));
  };

  const manejarEnvio = (e) => {
    e.preventDefault();
    console.log('Datos del formulario:', formData);
    
    // Validación básica
    if (!formData.nombre || !formData.email) {
      alert('Por favor completa todos los campos requeridos');
      return;
    }
    
    // Aquí enviarías los datos a un servidor
    alert('Formulario enviado correctamente!');
  };

  return (
    <form onSubmit={manejarEnvio}>
      <div>
        <label htmlFor="nombre">Nombre:</label>
        <input
          type="text"
          id="nombre"
          name="nombre"
          value={formData.nombre}
          onChange={manejarCambio}
          required
        />
      </div>

      <div>
        <label htmlFor="email">Email:</label>
        <input
          type="email"
          id="email"
          name="email"
          value={formData.email}
          onChange={manejarCambio}
          required
        />
      </div>

      <div>
        <label htmlFor="mensaje">Mensaje:</label>
        <textarea
          id="mensaje"
          name="mensaje"
          value={formData.mensaje}
          onChange={manejarCambio}
          rows="4"
        />
      </div>

      <div>
        <label htmlFor="pais">País:</label>
        <select
          id="pais"
          name="pais"
          value={formData.pais}
          onChange={manejarCambio}
        >
          <option value="mexico">México</option>
          <option value="argentina">Argentina</option>
          <option value="colombia">Colombia</option>
          <option value="espana">España</option>
        </select>
      </div>

      <div>
        <label>
          <input
            type="checkbox"
            name="acepta"
            checked={formData.acepta}
            onChange={manejarCambio}
          />
          Acepto los términos y condiciones
        </label>
      </div>

      <button type="submit">Enviar</button>
    </form>
  );
}
```

### 3. Validación de Formularios

```jsx
import React, { useState } from 'react';

function FormularioConValidacion() {
  const [formData, setFormData] = useState({
    email: '',
    password: '',
    confirmPassword: ''
  });
  
  const [errores, setErrores] = useState({});

  const validarEmail = (email) => {
    const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return regex.test(email);
  };

  const validarFormulario = () => {
    const nuevosErrores = {};

    if (!formData.email) {
      nuevosErrores.email = 'El email es requerido';
    } else if (!validarEmail(formData.email)) {
      nuevosErrores.email = 'El email no es válido';
    }

    if (!formData.password) {
      nuevosErrores.password = 'La contraseña es requerida';
    } else if (formData.password.length < 6) {
      nuevosErrores.password = 'La contraseña debe tener al menos 6 caracteres';
    }

    if (formData.password !== formData.confirmPassword) {
      nuevosErrores.confirmPassword = 'Las contraseñas no coinciden';
    }

    return nuevosErrores;
  };

  const manejarCambio = (e) => {
    const { name, value } = e.target;
    setFormData(prev => ({
      ...prev,
      [name]: value
    }));

    // Limpiar error cuando el usuario empiece a escribir
    if (errores[name]) {
      setErrores(prev => ({
        ...prev,
        [name]: ''
      }));
    }
  };

  const manejarEnvio = (e) => {
    e.preventDefault();
    const nuevosErrores = validarFormulario();
    
    if (Object.keys(nuevosErrores).length === 0) {
      console.log('Formulario válido:', formData);
      alert('Registro exitoso!');
    } else {
      setErrores(nuevosErrores);
    }
  };

  return (
    <form onSubmit={manejarEnvio}>
      <div>
        <label>Email:</label>
        <input
          type="email"
          name="email"
          value={formData.email}
          onChange={manejarCambio}
        />
        {errores.email && <span className="error">{errores.email}</span>}
      </div>

      <div>
        <label>Contraseña:</label>
        <input
          type="password"
          name="password"
          value={formData.password}
          onChange={manejarCambio}
        />
        {errores.password && <span className="error">{errores.password}</span>}
      </div>

      <div>
        <label>Confirmar Contraseña:</label>
        <input
          type="password"
          name="confirmPassword"
          value={formData.confirmPassword}
          onChange={manejarCambio}
        />
        {errores.confirmPassword && <span className="error">{errores.confirmPassword}</span>}
      </div>

      <button type="submit">Registrarse</button>
    </form>
  );
}
```

---

## 🔀 Renderizado Condicional

React permite mostrar diferentes elementos basándose en condiciones.

### 1. If-Else con Variables

```jsx
function SaludoCondicional({ usuario }) {
  let contenido;
  
  if (usuario) {
    contenido = <h1>¡Bienvenido de vuelta, {usuario.nombre}!</h1>;
  } else {
    contenido = <h1>Por favor, inicia sesión.</h1>;
  }
  
  return <div>{contenido}</div>;
}
```

### 2. Operador Ternario

```jsx
function EstadoUsuario({ estaLogueado, nombre }) {
  return (
    <div>
      {estaLogueado ? (
        <div>
          <h2>¡Hola, {nombre}!</h2>
          <button>Cerrar Sesión</button>
        </div>
      ) : (
        <div>
          <h2>Bienvenido, invitado</h2>
          <button>Iniciar Sesión</button>
        </div>
      )}
    </div>
  );
}
```

### 3. Operador && (AND Lógico)

```jsx
function Notificaciones({ mensajes }) {
  return (
    <div>
      <h1>Mi Aplicación</h1>
      {mensajes.length > 0 && (
        <div className="notificaciones">
          <h2>Tienes {mensajes.length} mensajes nuevos</h2>
          <ul>
            {mensajes.map((mensaje, index) => (
              <li key={index}>{mensaje}</li>
            ))}
          </ul>
        </div>
      )}
    </div>
  );
}
```

### 4. Renderizado Basado en Props

```jsx
function Alerta({ tipo, mensaje, mostrar }) {
  if (!mostrar) return null;

  const claseCSS = `alerta alerta-${tipo}`;
  
  return (
    <div className={claseCSS}>
      <p>{mensaje}</p>
    </div>
  );
}

// Uso
function App() {
  return (
    <div>
      <Alerta 
        tipo="exito" 
        mensaje="Operación exitosa" 
        mostrar={true} 
      />
      <Alerta 
        tipo="error" 
        mensaje="Hubo un error" 
        mostrar={false} 
      />
    </div>
  );
}
```

### 5. Switch con Múltiples Condiciones

```jsx
function EstadoPedido({ estado }) {
  const renderizarEstado = () => {
    switch (estado) {
      case 'pendiente':
        return (
          <div className="estado-pendiente">
            <span>⏳</span>
            <p>Pedido pendiente</p>
          </div>
        );
      case 'procesando':
        return (
          <div className="estado-procesando">
            <span>🔄</span>
            <p>Procesando pedido</p>
          </div>
        );
      case 'enviado':
        return (
          <div className="estado-enviado">
            <span>🚚</span>
            <p>Pedido enviado</p>
          </div>
        );
      case 'entregado':
        return (
          <div className="estado-entregado">
            <span>✅</span>
            <p>Pedido entregado</p>
          </div>
        );
      default:
        return (
          <div className="estado-desconocido">
            <span>❓</span>
            <p>Estado desconocido</p>
          </div>
        );
    }
  };

  return (
    <div className="pedido">
      <h3>Estado del Pedido</h3>
      {renderizarEstado()}
    </div>
  );
}
```

---

## 📝 Listas y Keys

React puede renderizar arrays de elementos de forma eficiente.

### 1. Renderizar Lista Simple

```jsx
function ListaSimple() {
  const frutas = ['Manzana', 'Banana', 'Naranja', 'Uva'];
  
  return (
    <ul>
      {frutas.map((fruta, index) => (
        <li key={index}>{fruta}</li>
      ))}
    </ul>
  );
}
```

### 2. Lista con Objetos y Keys Únicas

```jsx
function ListaProductos() {
  const productos = [
    { id: 1, nombre: 'Laptop', precio: 999, categoria: 'Electrónicos' },
    { id: 2, nombre: 'Mouse', precio: 25, categoria: 'Accesorios' },
    { id: 3, nombre: 'Teclado', precio: 75, categoria: 'Accesorios' },
    { id: 4, nombre: 'Monitor', precio: 300, categoria: 'Electrónicos' }
  ];

  return (
    <div className="lista-productos">
      <h2>Catálogo de Productos</h2>
      {productos.map(producto => (
        <div key={producto.id} className="producto">
          <h3>{producto.nombre}</h3>
          <p>Precio: ${producto.precio}</p>
          <p>Categoría: {producto.categoria}</p>
        </div>
      ))}
    </div>
  );
}
```

### 3. Filtrado Dinámico de Listas

```jsx
import React, { useState } from 'react';

function ListaFiltrable() {
  const [filtro, setFiltro] = useState('');
  const [categoriaFiltro, setCategoriaFiltro] = useState('todas');
  
  const productos = [
    { id: 1, nombre: 'iPhone', precio: 999, categoria: 'telefono' },
    { id: 2, nombre: 'Samsung Galaxy', precio: 799, categoria: 'telefono' },
    { id: 3, nombre: 'MacBook', precio: 1299, categoria: 'laptop' },
    { id: 4, nombre: 'Dell XPS', precio: 1099, categoria: 'laptop' },
    { id: 5, nombre: 'iPad', precio: 599, categoria: 'tablet' }
  ];

  const productosFiltrados = productos.filter(producto => {
    const coincideNombre = producto.nombre.toLowerCase().includes(filtro.toLowerCase());
    const coincideCategoria = categoriaFiltro === 'todas' || producto.categoria === categoriaFiltro;
    return coincideNombre && coincideCategoria;
  });

  return (
    <div>
      <h2>Productos ({productosFiltrados.length})</h2>
      
      <div className="filtros">
        <input
          type="text"
          placeholder="Buscar productos..."
          value={filtro}
          onChange={(e) => setFiltro(e.target.value)}
        />
        
        <select 
          value={categoriaFiltro} 
          onChange={(e) => setCategoriaFiltro(e.target.value)}
        >
          <option value="todas">Todas las categorías</option>
          <option value="telefono">Teléfonos</option>
          <option value="laptop">Laptops</option>
          <option value="tablet">Tablets</option>
        </select>
      </div>

      <div className="productos">
        {productosFiltrados.length > 0 ? (
          productosFiltrados.map(producto => (
            <div key={producto.id} className="producto">
              <h3>{producto.nombre}</h3>
              <p>${producto.precio}</p>
              <span className="categoria">{producto.categoria}</span>
            </div>
          ))
        ) : (
          <p>No se encontraron productos.</p>
        )}
      </div>
    </div>
  );
}
```

### 4. Lista Interactiva con Acciones

```jsx
import React, { useState } from 'react';

function ListaTareas() {
  const [tareas, setTareas] = useState([
    { id: 1, texto: 'Aprender React', completada: false },
    { id: 2, texto: 'Hacer ejercicio', completada: true },
    { id: 3, texto: 'Leer un libro', completada: false }
  ]);
  
  const [nuevaTarea, setNuevaTarea] = useState('');

  const agregarTarea = (e) => {
    e.preventDefault();
    if (nuevaTarea.trim()) {
      const nueva = {
        id: Date.now(),
        texto: nuevaTarea,
        completada: false
      };
      setTareas([...tareas, nueva]);
      setNuevaTarea('');
    }
  };

  const toggleTarea = (id) => {
    setTareas(tareas.map(tarea =>
      tarea.id === id ? { ...tarea, completada: !tarea.completada } : tarea
    ));
  };

  const eliminarTarea = (id) => {
    setTareas(tareas.filter(tarea => tarea.id !== id));
  };

  return (
    <div className="lista-tareas">
      <h2>Lista de Tareas</h2>
      
      <form onSubmit={agregarTarea}>
        <input
          type="text"
          value={nuevaTarea}
          onChange={(e) => setNuevaTarea(e.target.value)}
          placeholder="Nueva tarea..."
        />
        <button type="submit">Agregar</button>
      </form>

      <ul>
        {tareas.map(tarea => (
          <li key={tarea.id} className={tarea.completada ? 'completada' : ''}>
            <input
              type="checkbox"
              checked={tarea.completada}
              onChange={() => toggleTarea(tarea.id)}
            />
            <span>{tarea.texto}</span>
            <button onClick={() => eliminarTarea(tarea.id)}>
              Eliminar
            </button>
          </li>
        ))}
      </ul>
      
      <p>
        {tareas.filter(t => !t.completada).length} de {tareas.length} tareas pendientes
      </p>
    </div>
  );
}
```

---

## 🎨 Estilos en React

React ofrece varias formas de aplicar estilos a los componentes.

### 1. Estilos Inline

```jsx
function ComponenteConEstilosInline() {
  const estiloTitulo = {
    color: 'blue',
    fontSize: '24px',
    textAlign: 'center',
    marginBottom: '20px'
  };

  const estiloBoton = {
    backgroundColor: '#007bff',
    color: 'white',
    border: 'none',
    padding: '10px 20px',
    borderRadius: '5px',
    cursor: 'pointer'
  };

  return (
    <div style={{ padding: '20px', backgroundColor: '#f8f9fa' }}>
      <h1 style={estiloTitulo}>Título con Estilo</h1>
      <button style={estiloBoton}>Botón Estilizado</button>
    </div>
  );
}
```

### 2. Estilos Condicionales

```jsx
import React, { useState } from 'react';

function BotonConEstilosCondicionales() {
  const [activo, setActivo] = useState(false);
  const [hover, setHover] = useState(false);

  const estiloBoton = {
    padding: '12px 24px',
    border: 'none',
    borderRadius: '6px',
    cursor: 'pointer',
    transition: 'all 0.3s ease',
    backgroundColor: activo ? '#28a745' : '#007bff',
    color: 'white',
    transform: hover ? 'scale(1.05)' : 'scale(1)',
    boxShadow: hover ? '0 4px 8px rgba(0,0,0,0.2)' : '0 2px 4px rgba(0,0,0,0.1)'
  };

  return (
    <button
      style={estiloBoton}
      onClick={() => setActivo(!activo)}
      onMouseEnter={() => setHover(true)}
      onMouseLeave={() => setHover(false)}
    >
      {activo ? 'Activo' : 'Inactivo'}
    </button>
  );
}
```

### 3. CSS Modules

```css
/* Button.module.css */
.button {
  padding: 12px 24px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-size: 16px;
  transition: all 0.3s ease;
}

.primary {
  background-color: #007bff;
  color: white;
}

.secondary {
  background-color: #6c757d;
  color: white;
}

.button:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0,0,0,0.2);
}
```

```jsx
// Button.js
import styles from './Button.module.css';

function Button({ children, variant = 'primary', onClick }) {
  return (
    <button 
      className={`${styles.button} ${styles[variant]}`}
      onClick={onClick}
    >
      {children}
    </button>
  );
}
```

### 4. Styled Components (CSS-in-JS)

```jsx
// Primero instalar: npm install styled-components
import styled from 'styled-components';

const StyledButton = styled.button`
  padding: 12px 24px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-size: 16px;
  transition: all 0.3s ease;
  background-color: ${props => props.primary ? '#007bff' : '#6c757d'};
  color: white;

  &:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
  }

  &:active {
    transform: translateY(0);
  }
`;

const Container = styled.div`
  padding: 20px;
  max-width: 800px;
  margin: 0 auto;
  background-color: #f8f9fa;
  border-radius: 8px;
`;

function ComponenteConStyledComponents() {
  return (
    <Container>
      <h1>Styled Components</h1>
      <StyledButton primary onClick={() => alert('Primario!')}>
        Botón Primario
      </StyledButton>
      <StyledButton onClick={() => alert('Secundario!')}>
        Botón Secundario
      </StyledButton>
    </Container>
  );
}
```

---

## 🪝 Hooks Modernos

Los Hooks permiten usar estado y otras características de React en componentes funcionales.

### 1. useState - Estado Local

```jsx
import React, { useState } from 'react';

function ContadorConUseState() {
  const [count, setCount] = useState(0);
  const [nombre, setNombre] = useState('');
  const [usuario, setUsuario] = useState({
    nombre: '',
    email: '',
    edad: 0
  });

  const incrementar = () => setCount(count + 1);
  const decrementar = () => setCount(prev => prev - 1);

  const actualizarUsuario = (campo, valor) => {
    setUsuario(prev => ({
      ...prev,
      [campo]: valor
    }));
  };

  return (
    <div>
      <h2>Contador: {count}</h2>
      <button onClick={incrementar}>+</button>
      <button onClick={decrementar}>-</button>
      
      <div>
        <input
          type="text"
          placeholder="Tu nombre"
          value={nombre}
          onChange={(e) => setNombre(e.target.value)}
        />
        <p>Hola, {nombre}!</p>
      </div>

      <div>
        <h3>Información del Usuario</h3>
        <input
          type="text"
          placeholder="Nombre"
          value={usuario.nombre}
          onChange={(e) => actualizarUsuario('nombre', e.target.value)}
        />
        <input
          type="email"
          placeholder="Email"
          value={usuario.email}
          onChange={(e) => actualizarUsuario('email', e.target.value)}
        />
        <input
          type="number"
          placeholder="Edad"
          value={usuario.edad}
          onChange={(e) => actualizarUsuario('edad', parseInt(e.target.value))}
        />
        <pre>{JSON.stringify(usuario, null, 2)}</pre>
      </div>
    </div>
  );
}
```

### 2. useEffect - Efectos Secundarios

```jsx
import React, { useState, useEffect } from 'react';

function ComponenteConUseEffect() {
  const [count, setCount] = useState(0);
  const [datos, setDatos] = useState(null);
  const [cargando, setCargando] = useState(true);

  // Efecto que se ejecuta en cada render
  useEffect(() => {
    document.title = `Contador: ${count}`;
  });

  // Efecto que se ejecuta solo una vez (componentDidMount)
  useEffect(() => {
    console.log('Componente montado');
    
    // Simular carga de datos
    const cargarDatos = async () => {
      setCargando(true);
      try {
        // Simular API call
        await new Promise(resolve => setTimeout(resolve, 2000));
        setDatos('Datos cargados exitosamente');
      } catch (error) {
        console.error('Error cargando datos:', error);
      } finally {
        setCargando(false);
      }
    };

    cargarDatos();
  }, []); // Array vacío = solo una vez

  // Efecto que se ejecuta cuando count cambia
  useEffect(() => {
    if (count > 0) {
      console.log(`El contador cambió a: ${count}`);
    }
  }, [count]); // Se ejecuta cuando count cambia

  // Efecto con cleanup
  useEffect(() => {
    const interval = setInterval(() => {
      console.log('Timer ejecutándose...');
    }, 1000);

    // Cleanup function
    return () => {
      console.log('Limpiando interval');
      clearInterval(interval);
    };
  }, []);

  return (
    <div>
      <h2>useEffect Examples</h2>
      <p>Contador: {count}</p>
      <button onClick={() => setCount(count + 1)}>Incrementar</button>
      
      <div>
        <h3>Datos de la API:</h3>
        {cargando ? <p>Cargando...</p> : <p>{datos}</p>}
      </div>
    </div>
  );
}
```

### 3. useContext - Contexto Global

```jsx
import React, { createContext, useContext, useState } from 'react';

// Crear contexto
const TemaContext = createContext();
const UsuarioContext = createContext();

// Provider del tema
function TemaProvider({ children }) {
  const [tema, setTema] = useState('claro');

  const toggleTema = () => {
    setTema(prev => prev === 'claro' ? 'oscuro' : 'claro');
  };

  return (
    <TemaContext.Provider value={{ tema, toggleTema }}>
      {children}
    </TemaContext.Provider>
  );
}

// Provider del usuario
function UsuarioProvider({ children }) {
  const [usuario, setUsuario] = useState(null);

  const login = (datosUsuario) => {
    setUsuario(datosUsuario);
  };

  const logout = () => {
    setUsuario(null);
  };

  return (
    <UsuarioContext.Provider value={{ usuario, login, logout }}>
      {children}
    </UsuarioContext.Provider>
  );
}

// Hook personalizado para usar el tema
function useTema() {
  const context = useContext(TemaContext);
  if (!context) {
    throw new Error('useTema debe usarse dentro de TemaProvider');
  }
  return context;
}

// Hook personalizado para usar el usuario
function useUsuario() {
  const context = useContext(UsuarioContext);
  if (!context) {
    throw new Error('useUsuario debe usarse dentro de UsuarioProvider');
  }
  return context;
}

// Componente que usa los contextos
function Header() {
  const { tema, toggleTema } = useTema();
  const { usuario, logout } = useUsuario();

  const estilos = {
    backgroundColor: tema === 'claro' ? '#fff' : '#333',
    color: tema === 'claro' ? '#333' : '#fff',
    padding: '20px',
    display: 'flex',
    justifyContent: 'space-between',
    alignItems: 'center'
  };

  return (
    <header style={estilos}>
      <h1>Mi Aplicación</h1>
      <div>
        <button onClick={toggleTema}>
          Cambiar a tema {tema === 'claro' ? 'oscuro' : 'claro'}
        </button>
        {usuario ? (
          <div>
            <span>Hola, {usuario.nombre}!</span>
            <button onClick={logout}>Cerrar Sesión</button>
          </div>
        ) : (
          <span>No logueado</span>
        )}
      </div>
    </header>
  );
}

// Componente principal
function AppConContexto() {
  const { usuario, login } = useUsuario();

  const manejarLogin = () => {
    login({ nombre: 'Juan Pérez', email: 'juan@email.com' });
  };

  return (
    <div>
      <Header />
      <main style={{ padding: '20px' }}>
        {!usuario && (
          <button onClick={manejarLogin}>Iniciar Sesión</button>
        )}
        <p>Contenido principal de la aplicación</p>
      </main>
    </div>
  );
}

// App con providers
function App() {
  return (
    <TemaProvider>
      <UsuarioProvider>
        <AppConContexto />
      </UsuarioProvider>
    </TemaProvider>
  );
}
```

### 4. useReducer - Estado Complejo

```jsx
import React, { useReducer } from 'react';

// Definir el estado inicial
const estadoInicial = {
  items: [],
  cargando: false,
  error: null,
  filtro: 'todos'
};

// Definir las acciones
const ACCIONES = {
  AGREGAR_ITEM: 'AGREGAR_ITEM',
  ELIMINAR_ITEM: 'ELIMINAR_ITEM',
  TOGGLE_ITEM: 'TOGGLE_ITEM',
  SET_CARGANDO: 'SET_CARGANDO',
  SET_ERROR: 'SET_ERROR',
  SET_FILTRO: 'SET_FILTRO',
  LIMPIAR_COMPLETADOS: 'LIMPIAR_COMPLETADOS'
};

// Reducer function
function tareasReducer(state, action) {
  switch (action.type) {
    case ACCIONES.AGREGAR_ITEM:
      return {
        ...state,
        items: [...state.items, {
          id: Date.now(),
          texto: action.payload,
          completado: false
        }]
      };
    
    case ACCIONES.ELIMINAR_ITEM:
      return {
        ...state,
        items: state.items.filter(item => item.id !== action.payload)
      };
    
    case ACCIONES.TOGGLE_ITEM:
      return {
        ...state,
        items: state.items.map(item =>
          item.id === action.payload
            ? { ...item, completado: !item.completado }
            : item
        )
      };
    
    case ACCIONES.SET_CARGANDO:
      return {
        ...state,
        cargando: action.payload
      };
    
    case ACCIONES.SET_ERROR:
      return {
        ...state,
        error: action.payload
      };
    
    case ACCIONES.SET_FILTRO:
      return {
        ...state,
        filtro: action.payload
      };
    
    case ACCIONES.LIMPIAR_COMPLETADOS:
      return {
        ...state,
        items: state.items.filter(item => !item.completado)
      };
    
    default:
      return state;
  }
}

function TareasConUseReducer() {
  const [state, dispatch] = useReducer(tareasReducer, estadoInicial);
  const [inputValue, setInputValue] = useState('');

  const agregarTarea = (e) => {
    e.preventDefault();
    if (inputValue.trim()) {
      dispatch({ type: ACCIONES.AGREGAR_ITEM, payload: inputValue });
      setInputValue('');
    }
  };

  const itemsFiltrados = state.items.filter(item => {
    switch (state.filtro) {
      case 'activos':
        return !item.completado;
      case 'completados':
        return item.completado;
      default:
        return true;
    }
  });

  return (
    <div>
      <h2>Lista de Tareas con useReducer</h2>
      
      <form onSubmit={agregarTarea}>
        <input
          type="text"
          value={inputValue}
          onChange={(e) => setInputValue(e.target.value)}
          placeholder="Nueva tarea..."
        />
        <button type="submit">Agregar</button>
      </form>

      <div>
        <button 
          onClick={() => dispatch({ type: ACCIONES.SET_FILTRO, payload: 'todos' })}
          style={{ fontWeight: state.filtro === 'todos' ? 'bold' : 'normal' }}
        >
          Todos
        </button>
        <button 
          onClick={() => dispatch({ type: ACCIONES.SET_FILTRO, payload: 'activos' })}
          style={{ fontWeight: state.filtro === 'activos' ? 'bold' : 'normal' }}
        >
          Activos
        </button>
        <button 
          onClick={() => dispatch({ type: ACCIONES.SET_FILTRO, payload: 'completados' })}
          style={{ fontWeight: state.filtro === 'completados' ? 'bold' : 'normal' }}
        >
          Completados
        </button>
        <button onClick={() => dispatch({ type: ACCIONES.LIMPIAR_COMPLETADOS })}>
          Limpiar Completados
        </button>
      </div>

      <ul>
        {itemsFiltrados.map(item => (
          <li key={item.id}>
            <input
              type="checkbox"
              checked={item.completado}
              onChange={() => dispatch({ type: ACCIONES.TOGGLE_ITEM, payload: item.id })}
            />
            <span style={{ textDecoration: item.completado ? 'line-through' : 'none' }}>
              {item.texto}
            </span>
            <button onClick={() => dispatch({ type: ACCIONES.ELIMINAR_ITEM, payload: item.id })}>
              Eliminar
            </button>
          </li>
        ))}
      </ul>

      <p>
        {state.items.filter(item => !item.completado).length} de {state.items.length} tareas pendientes
      </p>
    </div>
  );
}
```

---

## 🗃️ Redux

Redux es una biblioteca para manejar el estado global de la aplicación de forma predecible.

### 1. Conceptos Básicos de Redux

```jsx
// store.js
import { createStore } from 'redux';

// 1. ACTIONS - Describen qué pasó
const INCREMENTAR = 'INCREMENTAR';
const DECREMENTAR = 'DECREMENTAR';
const RESET = 'RESET';

// Action Creators
const incrementar = () => ({ type: INCREMENTAR });
const decrementar = () => ({ type: DECREMENTAR });
const reset = () => ({ type: RESET });

// 2. REDUCER - Especifica cómo cambia el estado
const estadoInicial = {
  count: 0
};

function contadorReducer(state = estadoInicial, action) {
  switch (action.type) {
    case INCREMENTAR:
      return { ...state, count: state.count + 1 };
    case DECREMENTAR:
      return { ...state, count: state.count - 1 };
    case RESET:
      return { ...state, count: 0 };
    default:
      return state;
  }
}

// 3. STORE - Mantiene el estado de la aplicación
const store = createStore(contadorReducer);

export { store, incrementar, decrementar, reset };
```

### 2. Redux con Múltiples Reducers

```jsx
// reducers/contadorReducer.js
const INCREMENTAR = 'contador/INCREMENTAR';
const DECREMENTAR = 'contador/DECREMENTAR';

const estadoInicialContador = { valor: 0 };

export function contadorReducer(state = estadoInicialContador, action) {
  switch (action.type) {
    case INCREMENTAR:
      return { ...state, valor: state.valor + 1 };
    case DECREMENTAR:
      return { ...state, valor: state.valor - 1 };
    default:
      return state;
  }
}

export const incrementarContador = () => ({ type: INCREMENTAR });
export const decrementarContador = () => ({ type: DECREMENTAR });

// reducers/usuarioReducer.js
const LOGIN = 'usuario/LOGIN';
const LOGOUT = 'usuario/LOGOUT';

const estadoInicialUsuario = { 
  usuario: null, 
  estaLogueado: false 
};

export function usuarioReducer(state = estadoInicialUsuario, action) {
  switch (action.type) {
    case LOGIN:
      return {
        ...state,
        usuario: action.payload,
        estaLogueado: true
      };
    case LOGOUT:
      return {
        ...state,
        usuario: null,
        estaLogueado: false
      };
    default:
      return state;
  }
}

export const login = (datosUsuario) => ({ 
  type: LOGIN, 
  payload: datosUsuario 
});
export const logout = () => ({ type: LOGOUT });

// store.js
import { createStore, combineReducers } from 'redux';
import { contadorReducer } from './reducers/contadorReducer';
import { usuarioReducer } from './reducers/usuarioReducer';

const rootReducer = combineReducers({
  contador: contadorReducer,
  usuario: usuarioReducer
});

const store = createStore(rootReducer);

export default store;
```

### 3. Redux con Acciones Asíncronas (Redux Thunk)

```jsx
// Instalar: npm install redux-thunk
import { createStore, applyMiddleware } from 'redux';
import thunk from 'redux-thunk';

// Actions
const FETCH_USUARIOS_REQUEST = 'FETCH_USUARIOS_REQUEST';
const FETCH_USUARIOS_SUCCESS = 'FETCH_USUARIOS_SUCCESS';
const FETCH_USUARIOS_FAILURE = 'FETCH_USUARIOS_FAILURE';

// Action Creators Síncronos
const fetchUsuariosRequest = () => ({
  type: FETCH_USUARIOS_REQUEST
});

const fetchUsuariosSuccess = (usuarios) => ({
  type: FETCH_USUARIOS_SUCCESS,
  payload: usuarios
});

const fetchUsuariosFailure = (error) => ({
  type: FETCH_USUARIOS_FAILURE,
  payload: error
});

// Action Creator Asíncrono (Thunk)
const fetchUsuarios = () => {
  return async (dispatch) => {
    dispatch(fetchUsuariosRequest());
    
    try {
      const response = await fetch('https://jsonplaceholder.typicode.com/users');
      const usuarios = await response.json();
      dispatch(fetchUsuariosSuccess(usuarios));
    } catch (error) {
      dispatch(fetchUsuariosFailure(error.message));
    }
  };
};

// Reducer
const estadoInicial = {
  usuarios: [],
  cargando: false,
  error: null
};

function usuariosReducer(state = estadoInicial, action) {
  switch (action.type) {
    case FETCH_USUARIOS_REQUEST:
      return {
        ...state,
        cargando: true,
        error: null
      };
    case FETCH_USUARIOS_SUCCESS:
      return {
        ...state,
        cargando: false,
        usuarios: action.payload
      };
    case FETCH_USUARIOS_FAILURE:
      return {
        ...state,
        cargando: false,
        error: action.payload
      };
    default:
      return state;
  }
}

// Store con middleware
const store = createStore(
  usuariosReducer,
  applyMiddleware(thunk)
);

export { store, fetchUsuarios };
```

### 4. Redux Toolkit (Forma Moderna)

```jsx
// Instalar: npm install @reduxjs/toolkit
import { createSlice, configureStore, createAsyncThunk } from '@reduxjs/toolkit';

// Async Thunk para cargar usuarios
export const fetchUsuarios = createAsyncThunk(
  'usuarios/fetchUsuarios',
  async () => {
    const response = await fetch('https://jsonplaceholder.typicode.com/users');
    return response.json();
  }
);

// Slice (combina actions y reducer)
const usuariosSlice = createSlice({
  name: 'usuarios',
  initialState: {
    lista: [],
    cargando: false,
    error: null
  },
  reducers: {
    agregarUsuario: (state, action) => {
      state.lista.push(action.payload);
    },
    eliminarUsuario: (state, action) => {
      state.lista = state.lista.filter(usuario => usuario.id !== action.payload);
    }
  },
  extraReducers: (builder) => {
    builder
      .addCase(fetchUsuarios.pending, (state) => {
        state.cargando = true;
      })
      .addCase(fetchUsuarios.fulfilled, (state, action) => {
        state.cargando = false;
        state.lista = action.payload;
      })
      .addCase(fetchUsuarios.rejected, (state, action) => {
        state.cargando = false;
        state.error = action.error.message;
      });
  }
});

// Exportar actions
export const { agregarUsuario, eliminarUsuario } = usuariosSlice.actions;

// Configurar store
const store = configureStore({
  reducer: {
    usuarios: usuariosSlice.reducer
  }
});

export default store;
```

---

## 🔗 React + Redux

Integración de React con Redux para manejar el estado global de la aplicación.

### 1. Configuración Básica con React-Redux

```jsx
// Instalar: npm install react-redux
// index.js
import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';
import store from './store';
import App from './App';

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
);
```

### 2. Conectar Componentes con useSelector y useDispatch

```jsx
// components/Contador.js
import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { incrementar, decrementar, reset } from '../store';

function Contador() {
  const count = useSelector(state => state.count);
  const dispatch = useDispatch();

  return (
    <div>
      <h2>Contador: {count}</h2>
      <button onClick={() => dispatch(incrementar())}>+</button>
      <button onClick={() => dispatch(decrementar())}>-</button>
      <button onClick={() => dispatch(reset())}>Reset</button>
    </div>
  );
}

export default Contador;
```

### 3. Componente con Estado Complejo

```jsx
// components/ListaUsuarios.js
import React, { useEffect } from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { fetchUsuarios, agregarUsuario, eliminarUsuario } from '../store/usuariosSlice';

function ListaUsuarios() {
  const { lista, cargando, error } = useSelector(state => state.usuarios);
  const dispatch = useDispatch();

  useEffect(() => {
    dispatch(fetchUsuarios());
  }, [dispatch]);

  const handleAgregarUsuario = () => {
    const nuevoUsuario = {
      id: Date.now(),
      name: 'Usuario Nuevo',
      email: 'nuevo@email.com'
    };
    dispatch(agregarUsuario(nuevoUsuario));
  };

  if (cargando) return <div>Cargando usuarios...</div>;
  if (error) return <div>Error: {error}</div>;

  return (
    <div>
      <h2>Lista de Usuarios</h2>
      <button onClick={handleAgregarUsuario}>Agregar Usuario</button>
      
      <ul>
        {lista.map(usuario => (
          <li key={usuario.id}>
            <span>{usuario.name} - {usuario.email}</span>
            <button onClick={() => dispatch(eliminarUsuario(usuario.id))}>
              Eliminar
            </button>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default ListaUsuarios;
```

### 4. Formulario Conectado a Redux

```jsx
// components/FormularioUsuario.js
import React, { useState } from 'react';
import { useDispatch } from 'react-redux';
import { agregarUsuario } from '../store/usuariosSlice';

function FormularioUsuario() {
  const [nombre, setNombre] = useState('');
  const [email, setEmail] = useState('');
  const dispatch = useDispatch();

  const handleSubmit = (e) => {
    e.preventDefault();
    
    if (nombre.trim() && email.trim()) {
      dispatch(agregarUsuario({
        id: Date.now(),
        name: nombre,
        email: email
      }));
      
      setNombre('');
      setEmail('');
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <h3>Agregar Nuevo Usuario</h3>
      
      <div>
        <label>Nombre:</label>
        <input
          type="text"
          value={nombre}
          onChange={(e) => setNombre(e.target.value)}
          required
        />
      </div>
      
      <div>
        <label>Email:</label>
        <input
          type="email"
          value={email}
          onChange={(e) => setEmail(e.target.value)}
          required
        />
      </div>
      
      <button type="submit">Agregar Usuario</button>
    </form>
  );
}

export default FormularioUsuario;
```

### 5. Selectors Personalizados

```jsx
// selectors/usuariosSelectors.js
import { createSelector } from '@reduxjs/toolkit';

// Selector básico
export const selectUsuarios = (state) => state.usuarios.lista;

// Selector con memoización
export const selectUsuariosActivos = createSelector(
  [selectUsuarios],
  (usuarios) => usuarios.filter(usuario => usuario.activo)
);

// Selector con parámetros
export const selectUsuarioPorId = createSelector(
  [selectUsuarios, (state, id) => id],
  (usuarios, id) => usuarios.find(usuario => usuario.id === id)
);

// Uso en componente
function DetalleUsuario({ usuarioId }) {
  const usuario = useSelector(state => selectUsuarioPorId(state, usuarioId));
  
  if (!usuario) return <div>Usuario no encontrado</div>;
  
  return (
    <div>
      <h3>{usuario.name}</h3>
      <p>{usuario.email}</p>
    </div>
  );
}
```

---

## 🏋️ Ejercicios Prácticos

### Ejercicio 1: Calculadora Avanzada con Redux

```jsx
// store/calculadoraSlice.js
import { createSlice } from '@reduxjs/toolkit';

const calculadoraSlice = createSlice({
  name: 'calculadora',
  initialState: {
    valorActual: '0',
    valorAnterior: null,
    operacion: null,
    esperandoOperando: false,
    historial: []
  },
  reducers: {
    ingresarDigito: (state, action) => {
      const digito = action.payload;
      
      if (state.esperandoOperando) {
        state.valorActual = digito;
        state.esperandoOperando = false;
      } else {
        state.valorActual = state.valorActual === '0' ? digito : state.valorActual + digito;
      }
    },
    
    ingresarPunto: (state) => {
      if (state.esperandoOperando) {
        state.valorActual = '0.';
        state.esperandoOperando = false;
      } else if (state.valorActual.indexOf('.') === -1) {
        state.valorActual += '.';
      }
    },
    
    seleccionarOperacion: (state, action) => {
      const operacion = action.payload;
      
      if (state.valorAnterior === null) {
        state.valorAnterior = state.valorActual;
      } else if (state.operacion) {
        const resultado = calcular(state.valorAnterior, state.valorActual, state.operacion);
        state.valorActual = String(resultado);
        state.valorAnterior = String(resultado);
      }
      
      state.esperandoOperando = true;
      state.operacion = operacion;
    },
    
    calcular: (state) => {
      if (state.valorAnterior !== null && state.operacion) {
        const resultado = calcular(state.valorAnterior, state.valorActual, state.operacion);
        
        state.historial.push({
          operacion: `${state.valorAnterior} ${state.operacion} ${state.valorActual} = ${resultado}`,
          timestamp: new Date().toLocaleTimeString()
        });
        
        state.valorActual = String(resultado);
        state.valorAnterior = null;
        state.operacion = null;
        state.esperandoOperando = true;
      }
    },
    
    limpiar: (state) => {
      state.valorActual = '0';
      state.valorAnterior = null;
      state.operacion = null;
      state.esperandoOperando = false;
    },
    
    limpiarHistorial: (state) => {
      state.historial = [];
    }
  }
});

function calcular(primerOperando, segundoOperando, operacion) {
  const anterior = parseFloat(primerOperando);
  const actual = parseFloat(segundoOperando);
  
  switch (operacion) {
    case '+': return anterior + actual;
    case '-': return anterior - actual;
    case '×': return anterior * actual;
    case '÷': return anterior / actual;
    default: return actual;
  }
}

export const {
  ingresarDigito,
  ingresarPunto,
  seleccionarOperacion,
  calcular,
  limpiar,
  limpiarHistorial
} = calculadoraSlice.actions;

export default calculadoraSlice.reducer;

// components/Calculadora.js
import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import {
  ingresarDigito,
  ingresarPunto,
  seleccionarOperacion,
  calcular,
  limpiar,
  limpiarHistorial
} from '../store/calculadoraSlice';

function Calculadora() {
  const { valorActual, historial } = useSelector(state => state.calculadora);
  const dispatch = useDispatch();

  const botones = [
    ['C', '±', '%', '÷'],
    ['7', '8', '9', '×'],
    ['4', '5', '6', '-'],
    ['1', '2', '3', '+'],
    ['0', '.', '=']
  ];

  const manejarClick = (valor) => {
    if (valor >= '0' && valor <= '9') {
      dispatch(ingresarDigito(valor));
    } else if (valor === '.') {
      dispatch(ingresarPunto());
    } else if (['+', '-', '×', '÷'].includes(valor)) {
      dispatch(seleccionarOperacion(valor));
    } else if (valor === '=') {
      dispatch(calcular());
    } else if (valor === 'C') {
      dispatch(limpiar());
    }
  };

  return (
    <div className="calculadora">
      <div className="pantalla">
        <div className="valor-actual">{valorActual}</div>
      </div>
      
      <div className="botones">
        {botones.map((fila, indiceFila) => (
          <div key={indiceFila} className="fila">
            {fila.map(boton => (
              <button
                key={boton}
                onClick={() => manejarClick(boton)}
                className={`boton ${
                  ['+', '-', '×', '÷', '='].includes(boton) ? 'operacion' : ''
                } ${boton === 'C' ? 'limpiar' : ''}`}
              >
                {boton}
              </button>
            ))}
          </div>
        ))}
      </div>
      
      <div className="historial">
        <h3>Historial</h3>
        <button onClick={() => dispatch(limpiarHistorial())}>
          Limpiar Historial
        </button>
        <ul>
          {historial.map((entrada, index) => (
            <li key={index}>
              <span>{entrada.operacion}</span>
              <small>{entrada.timestamp}</small>
            </li>
          ))}
        </ul>
      </div>
    </div>
  );
}

export default Calculadora;
```

### Ejercicio 2: Aplicación de Clima con API

```jsx
// store/climaSlice.js
import { createSlice, createAsyncThunk } from '@reduxjs/toolkit';

export const obtenerClima = createAsyncThunk(
  'clima/obtenerClima',
  async (ciudad) => {
    const API_KEY = 'tu_api_key_aqui';
    const response = await fetch(
      `https://api.openweathermap.org/data/2.5/weather?q=${ciudad}&appid=${API_KEY}&units=metric&lang=es`
    );
    
    if (!response.ok) {
      throw new Error('Ciudad no encontrada');
    }
    
    return response.json();
  }
);

const climaSlice = createSlice({
  name: 'clima',
  initialState: {
    datosActuales: null,
    cargando: false,
    error: null,
    ciudadesFavoritas: [],
    historialBusquedas: []
  },
  reducers: {
    agregarFavorita: (state, action) => {
      const ciudad = action.payload;
      if (!state.ciudadesFavoritas.find(c => c.id === ciudad.id)) {
        state.ciudadesFavoritas.push(ciudad);
      }
    },
    
    eliminarFavorita: (state, action) => {
      state.ciudadesFavoritas = state.ciudadesFavoritas.filter(
        ciudad => ciudad.id !== action.payload
      );
    },
    
    limpiarError: (state) => {
      state.error = null;
    }
  },
  extraReducers: (builder) => {
    builder
      .addCase(obtenerClima.pending, (state) => {
        state.cargando = true;
        state.error = null;
      })
      .addCase(obtenerClima.fulfilled, (state, action) => {
        state.cargando = false;
        state.datosActuales = action.payload;
        
        // Agregar al historial
        const busqueda = {
          ciudad: action.payload.name,
          timestamp: new Date().toISOString(),
          temperatura: action.payload.main.temp
        };
        
        state.historialBusquedas.unshift(busqueda);
        if (state.historialBusquedas.length > 10) {
          state.historialBusquedas.pop();
        }
      })
      .addCase(obtenerClima.rejected, (state, action) => {
        state.cargando = false;
        state.error = action.error.message;
      });
  }
});

export const { agregarFavorita, eliminarFavorita, limpiarError } = climaSlice.actions;
export default climaSlice.reducer;

// components/AppClima.js
import React, { useState } from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { obtenerClima, agregarFavorita, eliminarFavorita, limpiarError } from '../store/climaSlice';

function AppClima() {
  const [ciudadInput, setCiudadInput] = useState('');
  const { datosActuales, cargando, error, ciudadesFavoritas, historialBusquedas } = useSelector(state => state.clima);
  const dispatch = useDispatch();

  const buscarClima = (e) => {
    e.preventDefault();
    if (ciudadInput.trim()) {
      dispatch(obtenerClima(ciudadInput.trim()));
      setCiudadInput('');
    }
  };

  const agregarAFavoritas = () => {
    if (datosActuales) {
      dispatch(agregarFavorita({
        id: datosActuales.id,
        name: datosActuales.name,
        country: datosActuales.sys.country
      }));
    }
  };

  return (
    <div className="app-clima">
      <h1>Aplicación del Clima</h1>
      
      <form onSubmit={buscarClima}>
        <input
          type="text"
          value={ciudadInput}
          onChange={(e) => setCiudadInput(e.target.value)}
          placeholder="Ingresa una ciudad..."
          disabled={cargando}
        />
        <button type="submit" disabled={cargando}>
          {cargando ? 'Buscando...' : 'Buscar'}
        </button>
      </form>

      {error && (
        <div className="error">
          <p>Error: {error}</p>
          <button onClick={() => dispatch(limpiarError())}>Cerrar</button>
        </div>
      )}

      {datosActuales && (
        <div className="clima-actual">
          <h2>{datosActuales.name}, {datosActuales.sys.country}</h2>
          <div className="temperatura">{Math.round(datosActuales.main.temp)}°C</div>
          <div className="descripcion">{datosActuales.weather[0].description}</div>
          <div className="detalles">
            <p>Sensación térmica: {Math.round(datosActuales.main.feels_like)}°C</p>
            <p>Humedad: {datosActuales.main.humidity}%</p>
            <p>Viento: {datosActuales.wind.speed} m/s</p>
          </div>
          <button onClick={agregarAFavoritas}>Agregar a Favoritas</button>
        </div>
      )}

      <div className="favoritas">
        <h3>Ciudades Favoritas</h3>
        {ciudadesFavoritas.map(ciudad => (
          <div key={ciudad.id} className="ciudad-favorita">
            <span>{ciudad.name}, {ciudad.country}</span>
            <button onClick={() => dispatch(obtenerClima(ciudad.name))}>Ver</button>
            <button onClick={() => dispatch(eliminarFavorita(ciudad.id))}>Eliminar</button>
          </div>
        ))}
      </div>

      <div className="historial">
        <h3>Historial de Búsquedas</h3>
        {historialBusquedas.map((busqueda, index) => (
          <div key={index} className="busqueda-historial">
            <span>{busqueda.ciudad} - {Math.round(busqueda.temperatura)}°C</span>
            <small>{new Date(busqueda.timestamp).toLocaleString()}</small>
          </div>
        ))}
      </div>
    </div>
  );
}

export default AppClima;
```

---

## 🚨 Troubleshooting - Problemas Comunes

### 1. Errores de JSX

**Error:** `Adjacent JSX elements must be wrapped in an enclosing tag`
```jsx
// ❌ Incorrecto
function Componente() {
  return (
    <h1>Título</h1>
    <p>Párrafo</p>
  );
}

// ✅ Correcto
function Componente() {
  return (
    <div>
      <h1>Título</h1>
      <p>Párrafo</p>
    </div>
  );
}

// ✅ También correcto (React Fragment)
function Componente() {
  return (
    <>
      <h1>Título</h1>
      <p>Párrafo</p>
    </>
  );
}
```

### 2. Problemas con el Estado

**Error:** El estado no se actualiza inmediatamente
```jsx
// ❌ Problema común
function Contador() {
  const [count, setCount] = useState(0);
  
  const incrementar = () => {
    setCount(count + 1);
    console.log(count); // Muestra el valor anterior
  };
  
  return <button onClick={incrementar}>Count: {count}</button>;
}

// ✅ Solución
function Contador() {
  const [count, setCount] = useState(0);
  
  const incrementar = () => {
    setCount(prevCount => {
      const nuevoCount = prevCount + 1;
      console.log(nuevoCount); // Muestra el valor correcto
      return nuevoCount;
    });
  };
  
  return <button onClick={incrementar}>Count: {count}</button>;
}
```

### 3. Problemas con useEffect

**Error:** Bucle infinito en useEffect
```jsx
// ❌ Causa bucle infinito
function Componente() {
  const [datos, setDatos] = useState([]);
  
  useEffect(() => {
    fetch('/api/datos')
      .then(res => res.json())
      .then(setDatos);
  }); // Sin array de dependencias
  
  return <div>{datos.length}</div>;
}

// ✅ Solución
function Componente() {
  const [datos, setDatos] = useState([]);
  
  useEffect(() => {
    fetch('/api/datos')
      .then(res => res.json())
      .then(setDatos);
  }, []); // Array vacío para ejecutar solo una vez
  
  return <div>{datos.length}</div>;
}
```

### 4. Problemas con Keys en Listas

**Error:** Warning sobre keys faltantes
```jsx
// ❌ Sin keys
function Lista({ items }) {
  return (
    <ul>
      {items.map(item => (
        <li>{item.nombre}</li>
      ))}
    </ul>
  );
}

// ✅ Con keys únicas
function Lista({ items }) {
  return (
    <ul>
      {items.map(item => (
        <li key={item.id}>{item.nombre}</li>
      ))}
    </ul>
  );
}
```

### 5. Problemas con Redux

**Error:** Estado no se actualiza en Redux
```jsx
// ❌ Mutación directa del estado
const reducer = (state = initialState, action) => {
  switch (action.type) {
    case 'AGREGAR_ITEM':
      state.items.push(action.payload); // Mutación directa
      return state;
    default:
      return state;
  }
};

// ✅ Inmutabilidad
const reducer = (state = initialState, action) => {
  switch (action.type) {
    case 'AGREGAR_ITEM':
      return {
        ...state,
        items: [...state.items, action.payload]
      };
    default:
      return state;
  }
};
```

### 6. Problemas de Rendimiento

**Error:** Re-renderizados innecesarios
```jsx
// ❌ Función creada en cada render
function Lista({ items }) {
  return (
    <ul>
      {items.map(item => (
        <li key={item.id}>
          <button onClick={() => console.log(item.id)}>
            {item.nombre}
          </button>
        </li>
      ))}
    </ul>
  );
}

// ✅ Función memoizada
function Lista({ items }) {
  const handleClick = useCallback((id) => {
    console.log(id);
  }, []);
  
  return (
    <ul>
      {items.map(item => (
        <li key={item.id}>
          <button onClick={() => handleClick(item.id)}>
            {item.nombre}
          </button>
        </li>
      ))}
    </ul>
  );
}
```

### 7. Errores de Dependencias

**Error:** Module not found
```bash
# Verificar que el paquete esté instalado
npm list react

# Reinstalar dependencias
npm install

# Limpiar cache
npm cache clean --force
```

### 8. Problemas con el Servidor de Desarrollo

**Error:** Puerto ya en uso
```bash
# Cambiar puerto
npm start -- --port 3001

# O en package.json
"scripts": {
  "start": "react-scripts start --port 3001"
}
```

---

## 📚 Recursos Adicionales

### Documentación Oficial
- [React Documentation](https://reactjs.org/docs)
- [Redux Documentation](https://redux.js.org/)
- [React-Redux Documentation](https://react-redux.js.org/)

### Herramientas de Desarrollo
- [React Developer Tools](https://chrome.google.com/webstore/detail/react-developer-tools)
- [Redux DevTools](https://chrome.google.com/webstore/detail/redux-devtools)

### Cursos y Tutoriales
- [React Tutorial Oficial](https://reactjs.org/tutorial/tutorial.html)
- [Redux Essentials](https://redux.js.org/tutorials/essentials/part-1-overview-concepts)

---

¡Felicidades! Has completado esta guía completa de React y Redux. Continúa practicando y construyendo proyectos para dominar estas tecnologías.
