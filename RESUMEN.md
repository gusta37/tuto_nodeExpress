<!-- Estilos Css -->
<style>
/* fuentes: */
@import url('https://fonts.googleapis.com/css2?family=Roboto+Condensed:wght@100&display=swap');
/* font-family: 'Roboto Condensed', sans-serif; */
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
/* Titulos: */

  .title{
    background: white;
    color: lightgreen;
    border-radius: 5px;
    text-align: center;
    font-family: 'Roboto Condensed', sans-serif;
    padding-top: 10px;
  }
  .subtitle{
    font-family: 'Roboto Condensed', sans-serif;
  }
  .title_container{
    text-align: center;
  }
  .title_img {
    width: 100%;
    height: auto;    
    margin-top: 10px;
    margin-bottom: 10px;
    border-radius: 5px;
  }



/* Subtítulos: */
  .subtitle_img {
    width: 75%;
    height: auto;    
    margin-top: 20px;
    margin-bottom: 20px;
    border-radius: 5px;
  }

</style>

<h1 class="title">📃 Resumen de Node y Express</h1>

---
<div class="title_container"><img src="https://imgs.search.brave.com/BarfiL1oQqVuBHXeaXEsQISMHdyYKhtqvFOHWz2O9LI/rs:fit:500:0:0/g:ce/aHR0cHM6Ly9jZG4u/aGFzaG5vZGUuY29t/L3Jlcy9oYXNobm9k/ZS9pbWFnZS91cGxv/YWQvdjE2NjUxNjQz/MjQ1MjcvUkEzSmlP/UXE0LnBuZz93PTE2/MDAmaD04NDAmZml0/PWNyb3AmY3JvcD1l/bnRyb3B5JmF1dG89/Y29tcHJlc3MsZm9y/bWF0JmZvcm1hdD13/ZWJw" alt="módulos de node" class="title_img" style="border: 2px solid grey;"></div>

---
<h2 class="subtitle">📚 1. <u>Módulos en node</u>:</h2>

Un modulo en javascript es un archivo js que se puede importar a otra parte del proyecto.

### 📤 <u class="subtitle">Exportar</u>:

* Para poder usar el modulo que queremos importar, primero tengo que exportarlo.
* Para exportar el modulo usamos: `module.exports`. Podemos agregar propiedades y métodos al modulo exportado, usando un punto seguido de la propiedad a agregar, ej: `module.exports.saludar = saludar`. El "saludar" después del punto hace referencia al nombre de la propiedad y el "saludar" después del igual, a la función en si. siempre deberían ser iguales para evitar equivocaciones, aunque son independientes.

### 📥 <u class="subtitle">Importar</u>:

* Para importarlo en otra parte del proyecto lo citamos en una constante con el mismo nombre que el modulo (del modulo, no de la función!) y utilizamos `require`. En `require` siempre debemos colocar la ruta del archivo. Ej: 
```javascript
  const saludo = require('./saludo.js');
  ```

### <u class="subtitle">Podemos exportar varios elementos</u>: 
Para exportar varios elementos realizamos un module.exports para cada uno de ellos:
Ej:
```javascript
module.exports.saludar = saludar;
module.exports.saludarHolaMundo = saludarHolaMundo;
```

Otra forma mas fácil y clara de exportar varios elementos, es agregando las propiedades y los elementos dentro del module.exports en forma de objeto:
```javascript
module.exports = {
  saludar: saludar,
  saludarHolaMundo: saludarHolaMundo
}; 
```

### <u class="subtitle">Como llamamos ahora a nuestros elementos?</u>
Ahora debemos llamar a los elementos de nuestras funciones haciendo referencia al elemento en si, de la siguiente forma:
```javascript
console.log(saludos.saludar('freeCodeCamp'));
console.log(saludos.saludarHolaMundo());
```
.saludar('freeCodeCamp') es el elemento(función) que queremos llamar dentro del modulo "saludos". (freeCodeCamp es el parámetro para esa función).

### <u class="subtitle">Como podemos agilizar el proceso</u>? 🏃‍♀️
Usando la desestructuracion. 

Podemos importar solo lo que vamos a usar de un método. o sea, solo las funciones que vamos a usar. 

Para esto usamos la sintaxis de desestructuración que nos permite importar solo lo que queramos de los objetos. 

Después de la constante y dentro de llaves colocamos la propiedad que vamos a usar. 
Ej:
```javascript
const {saludar, saludarHolaMundo} = require('./saludo.js');
```

Usando la desestructuracion ya no necesito nombrar al modulo en el console.log, solo la propiedad.
Ej:
```javascript
console.log(saludar('freeCodeCamp'));
console.log(saludarHolaMundo());
```

## 💬 <u class="subtitle">Módulos nativos de node</u>:

* <u class="subtitle">***Console***</u> : simula la consola del inspector del navegador web. Pueden ser:
  * `log`: muestra un mensaje.
  * `warn`: muestra un advertencia.
  * `error`: muestra un error. Si usamos `new Error` muestra un error detallado.

* <u class="subtitle">***Process***</u> : se usa dentro del console.log y nos muestra elementos según su indice.

* <u class="subtitle">***OS(Sistema Operativo)***</u> : nos permite trabajar con el sistema operativo:
  * `os.type`: nos muestra el tipo de dato que es.
  * `os.homedir`: nos muestra el directorio principal.
  * `os.uptime`: nos muestra el tiempo que lleva activo el sistema operativo. (Lo muestra en segundos).
  * `os.userInfo`: nos muestra informacion sobre el sistema operativo.

* <u class="subtitle">***Timer***</u> : nos ayuda a determinar en que momento queremos que se ejecute una función. Estos módulos se pueden usar para ejecutar código de forma asíncrona. Son nativos asi que no necesitas instalarlos ni importarlos.
  
  Las opciones son:
  * 1. `setTimeout()`: se ejecuta en un tiempo determinado medido en milisegundos (1 segundo = 1000 milisegundos).
  * 2. `setImmediate()`: se ejecuta el código asíncrono en la proxima interacción del ciclo de eventos (lo mas pronto posible). Se ejecuta inmediatamente después de todo el código sincrono.
  * 3. `setInterval()`: se ejecuta un numero infinito de veces con un intervalo de tiempo determinado en milisegundos.

* <u class="subtitle">***Fs(File System)***</u> : Sistema de Archivos. Es muy util para trabajar con archivos.
  * Todos los métodos de este modulo son asíncronos por defecto!!! pero podemos elegir las versiones asíncronas o sincronas, según necesitemos.
  * Para convertirlos en sincronos solo agregamos el (sync) al final de los métodos.
  * Las operaciones que podemos realizar con el fs, entre otras, son:

    * Leer un archivo. => `fs.readFile`
    * Modificar un archivo. => `fs.appendFile` o `fs.writeFile`
    * Eliminar un archivo. => `fs.unlink`
    * Renombrar un archivo. => `fs.unlinkSync`

> Mas detalles de como se aplican en el siguiente archivo [Modulo fs](<2 - Modulos de Node/9 - El Modulo fs/app.js> 'Haz Click Aquí')
---
<h2 class="subtitle">📦 2. <u>Paquetes, npm y Json</u>:</h2>

---
<div class="title_container"><img src="https://imgs.search.brave.com/DYQOklAxQGbmMydOnyO8-t4EGln5cGVCBl_VcwtPdXI/rs:fit:860:0:0/g:ce/aHR0cHM6Ly93d3cu/YWRpa3RzLmlvL3dw/LWNvbnRlbnQvdXBs/b2Fkcy8yMDIzLzAz/L1BhY2thZ2VzLUpz/b24ucG5n" alt="módulos de node" class="title_img" style="border: 2px solid grey;"></div>

---
### <u class="subtitle">npm</u>:
<div class="title_container"><img src="https://imgs.search.brave.com/YC2Trw5quq3j1VDRwBez2fR_0QsaHWT17SPREJa0PKI/rs:fit:860:0:0/g:ce/aHR0cHM6Ly9raW5z/dGEuY29tL2VzL3dw/LWNvbnRlbnQvdXBs/b2Fkcy9zaXRlcy84/LzIwMjIvMDcvcXVl/LWVzLW5wbS0xMDI0/eDUxMi5wbmc" alt="módulos de node" class="subtitle_img" style="border: 2px solid grey;"></div>

* Es un compendio de paquetes enorme que puedes usar en node. Para ello debes instalarlo. 
* También es una linea de comandos. 
* Los paquetes de npm están en formato Json y se reconocen por el archivo package.json. 
* Cuando trabajamos con npm se crea automáticamente la carpeta node_modules que contiene todos los paquetes que hemos instalado y que podemos importar en nuestro proyecto.
* Dependencia: es un paquete necesario para que otro paquete funcione correctamente. (Paquete: es un archivo que contiene código que se puede usar en otros proyectos.).

#### <u class="subtitle">Como crear mi archivo Json con npm?</u>

* Primero creamos la carpeta contenedora dentro del proyecto.
* Ubicado dentro de la carpeta, vamos a ejecutar el comando `npm init`.
  
  * Debemos elegir el nombre de nuestro paquete. Por defecto, si no lo cambiamos, se llamara igual que el nombre de la carpeta contenedora.
  * Nos pide elegir la version del paquete.
  * Luego una descripción del paquete.
  * Ahora nos pregunta sobre "entry point" que es el punto de entrada de nuestro paquete.
  * Luego no pregunta mas cosas que no son obligatorias, como: "test command", "git repository", author, etc.
  * Por ultimo damos enter y nos pregunta si es correcta la información.
  * Si damos enter, nos creara el archivo package.json.

* Si queremos crear un archivo con todos los valores por defecto, solo debemos ejecutar el código `npm init --yes`.