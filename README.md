# cheatsheet

Resumen de estructuras mas usadas.

## Javascript

### Crear div

```js
function creaDiv() {
  let div = document.createElement("div");
  // añadir div al body
  document.body.appendChild(div);

  // insertar texto
  div.innerText = "texto insertado";
  // insertar bloque html
  div.innerHTML = "<h1>bloque html</h1>";
  // =====================================================================
  // estilos css al div creado
  // div.style.{propiedad} = "{valor de propiedad en str}";
  div.style.height = "20px";
  // equivalente
  let ds = div.style;
  ds.height = "20px";
  // =====================================================================
  // añadir event listener al div
  // div.addEventListener("{tipo de evento}", {'funcion a ejecutar sin "()"'})
  div.addEventListener("click", click1);
}
```

### Crear div con texto en parametro

```js
function creaDiv(texto) {
  let div = document.createElement("div");
  // añadir div al body
  document.body.appendChild(div);

  // insertar texto
  div.innerText = texto;
  // insertar bloque html
  div.innerHTML = texto;
  // =====================================================================
  // estilos css al div creado
  // div.style.{propiedad} = "{valor de propiedad en str}";
  div.style.height = "20px";
  // equivalente
  let ds = div.style;
  ds.height = "20px";
  // =====================================================================
  // añadir event listener al div
  // div.addEventListener("{tipo de evento}", {'funcion a ejecutar sin "()"'})
  div.addEventListener("click", click1);
}
```

### Crear div con texto y id

```js
function creaDiv(texto, id) {
  let div = document.createElement("div");
  // añadir div al body
  document.body.appendChild(div);
  // añadir id
  div.id = id;
  // añadir texto
  div.innerText = texto;
}
```

### Crear N elementos con id dinámico

Continuacion del ejemplo anterior
Ejemplo para N = 4

```js
function inicio() {
  for (let i = 0; i < 4; i++) {
    // 4 divs con id = 0 a id = 3
    creaDiv("texto de cada div", i); // creaDiv(texto, id)
  }
}
```

### Crear cualquier elemento HTML

Si se desea crear cualquier elemento del html como un p o h1 y meterlo dentro de un div ya creado

```js
let h1 = document.createElement("h1");
let p = document.createElement("p");
// texto h1
h1.innerText = "texto h1";
// texto p
p.innerText = "texto p";
// se añade el h1 al div
div.appendChild(h1);
// se añade el p al div
div.appendChild(p);
```

### Añadir id a elemento creado

```js
let p = document.createElement("p");
p.id = "id elemento"; // puede ser una variable, si se quiere poner una variable no hace falta ""
let idElemento = 2;
p.id = idElemento;
```

### Comportamiento de 2º click distinto del 1º click

```js
function inicio() {
  let div = document.createElement("div");
  document.body.appendChild(div);
  div.addEventListener("click", click1);
}

function click1(e) {
  e.stopImmediatePropagation();
  this.removeEventListener("click", click1);
  this.addEventListener("click", click2);
  // comportamiento 1º CLICK
}

function click2() {
  // comportamiento 2º CLICK
}
```

### Numero aleatorio

```js
// numero aleatorio entre a y b incluido b
function numeroAleatorio(a, b) {
  let numero = Math.floor(a + (b - a) * Math.random() + 1);
  return numero;
}

let num = numeroAleatorio(2, 5); // "num" es un numero entre 2 y 5, incluido el 5
```

### Color aleatorio hexagesimal

```js
function creaColor() {
  let cod = "0123456789ABCDEF";
  let resultado = "#";
  for (let i = 0; i < 6; i++) {
    resultado += cod[Math.floor(Math.random() * cod.length)];
  }
  return resultado;
```

### [Date](<https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/UTC#:~:text=00%3A00%20UTC.-,Syntax,-Date.UTC(year)>)

- [formatear fecha 1](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleString#:~:text=Copy%20to%20Clipboard-,Using%20options,-The%20results%20provided)

- [formatear fecha 2](https://stackoverflow.com/questions/3552461/how-to-format-a-javascript-date#:~:text=Options%20key%20examples)

Crear un objeto date con una fecha, los valores sin rellenar se toman como valores predeterminados.

El objeto fecha esta creado en la franja horaria +0h, tiene en cuenta el cambio de horas de verano-invierno

- year = numero de 4 digitos o de 0-99 si es entre 1900-1999
- month = 0-11 siendo 0 enero y 11 diciembre, si es 12 se toma como enero del proximo año
- day = 1-31
- horas, minutos, segundos, milisegundos empiezan a contar desde 0

```js
let fecha = new Date(Date.UTC(year, month, date, hour, min, sec, milisec));
```

FORMATEAR la salida ver formatear fecha 2 para ver que opciones existe no es necesario rellenar todas, solo las que se desea

```js
let options = {
  weekday: "long",
  year: "numeric",
  month: "long",
  day: "numeric",
};
let fechaStr = fecha.toLocaleDateString("es-ES", options);
```

### Rellenar con 0 por la izquierda

```js
let numero = 1;
// se requiere rellenar con 0 hasta 2 digitos
let numeroStr = String(numero).padStart(2, 0); // 01

let numero2 = 11;

let numero2Str = String(numero).padStart(2, 0); // 11
```

## HTML

Programa de inicio

```html
<head>
  <!-- dentro del head -->
  <script>
    // variables globales
    let vg = 0;
    function inicio() {
      // programa
      // variables locales
      let vl = 2;
    }
    // funciones auxiliares
    window.onload = inicio;
  </script>
</head>
```

Borrar contenido del body

```js
document.body.innerHTML = "";
```

## Estilos

### Poner un div a lado del otro usando float

```js
div1.style.float = "left";
div2.style.float = "left";
```

### Crear salto con float

Siguiendo el ejemplo anterior, podemos tener un div3 que este en otra linea

```js
div3.style.float = "left";
div3.style.clear = "left";
```

### Centrar contenido del div horizontalmente

[justify content](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-content#:~:text=See%20also-,justify%2Dcontent,-The%20CSS%20justify)

```js
div.style.display = "flex";
div.style.justifyContent = "center";
```

### Centrar contenido del div verticalmente

[align items](https://developer.mozilla.org/en-US/docs/Web/CSS/align-items#:~:text=See%20also-,align%2Ditems,-The%20CSS%20align)

```js
div.style.display = "flex";
div.style.alignItems = "center";
```

### Centrar contenido del div vertical y horizontal

```js
div.style.display = "flex";
div.style.justifyContent = "center";
div.style.alignItems = "center";
```

### Cambiar color de texto

El texto se encuetra dentro de un div

```js
div.style.color = "white";
```

### Cambiar color de fondo de un div

```js
div.style.backgroundColor = "black";
```

### Tamaños de caja

Si se quiere definir el tamaño de un div con width sin importar el padding y el borde, hay que añadir la propiedad de [box sizing](https://www.w3schools.com/CSSref/css3_pr_box-sizing.asp#:~:text=Demo%20%E2%9D%AF-,border%2Dbox,-The%20width%20and)

```js
div.style.boxSizing = "border-box";
```

### Cambiar fuente del documento entero

Esto iria dentro de inicio

```js
document.body.style.fontFamily = "Monospace";
```

### Cambiar fuente de un elemento

Ejemplo para un elemento p

```js
let p = document.createElement("p");
document.body.appendChild(p);
p.style.fontFamily = "Monospace";
```

### Añadir / eliminar clase a un elemento

```js
let div = document.getElementById("idDiv");
div.classList.add("class"); // añade "class" a las clases existentes de div
div.classList.remove("class"); // elimina "class" de las clases de div
```

### Modificar las clases de un elemento

```js
let div = document.getElementById("idDiv");
div.classList = "clase1 clase2 clase3"; // el elemento tendra solo las clases que estan presentes
// se puede eliminar todas las clases igualando a ""
div.classList = "";
```

### Obtener un elemento del documento a traves de su id

Si su id es "ejemplo"

```js
let objetoEjemplo = document.getElementById("ejemplo");
objetoEjemplo.style.fontSize = "24px";
```

### Obtener todos los elementos de un tipo

Ejemplo, se requiere todos los h2 del documento

```js
let titulos = document.getElementsByTagName("h2"); // es un array de objetos h2
for (titulo of titulos) {
  // hacer cosas a cada titulo de uno en uno
  titulo.style.color = "red";
}
```
