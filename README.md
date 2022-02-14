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
// ===================================================================================
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
