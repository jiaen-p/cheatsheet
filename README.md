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
