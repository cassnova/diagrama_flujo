# Desafío: javaScript

## Nombre de Desafío: diagrama_flujo

## Instrucciones

Determiná que será impreso en la consola, sin ejecutar el código.

> Investiga cuál es la diferencia entre declarar una variable con `var` y directamente asignarle un valor.

```javascript
x = 1;
var a = 5;
var b = 10;
var c = function (a, b, c) {
  var x = 10;
  console.log(x); // 10
  console.log(a); // 8
  var f = function (a, b, c) {
    b = a;
    console.log(b); // 8
    b = c;
    var x = 5;
  };
  f(a, b, c);
  console.log(b); // 9
};
c(8, 9, 10);
console.log(b); // 10
console.log(x);
```

```javascript
console.log(bar);
console.log(baz);
foo();
function foo() {
  console.log("Hola!");
}
var bar = 1;
baz = 2;
// Da undefined con los dos primeros log, pero tambien dar un error ya que no se ha definido baz y al final tira el log de Hola
```

```javascript
var instructor = "Jhoswe";
if (true) {
  var instructor = "Jose";
}
console.log(instructor);
// Jose
```

```javascript
var instructor = "Jhoswe";
console.log(instructor);
(function () {
  if (true) {
    var instructor = "Jose";
    console.log(instructor);
  }
})();
console.log(instructor);
// 1, Jhoswe 2. Jose 3. Jhoswe
```

```javascript
var instructor = "Jhoswe";
let pm = "Jose";
if (true) {
  var instructor = "The Flash";
  let pm = "Reverse Flash";
  console.log(instructor);
  console.log(pm);
}
console.log(instructor);
console.log(pm);
// 1. The Flash 2. Reverse Flash 3. The Flash 4. Jose
```

### Coerción de Datos

¿Cuál crees que será el resultado de la ejecución de estas operaciones?:

```javascript
6 / "3" // 2
"2" * "3" // 6
4 + 5 + "px" // Da como resultado 9px
"$" + 4 + 5 // Da como resultado $9
"4" - 2 // 2
"4px" - 2 // Da como resultado NaN
7 / 0 // Infinity
{}[0] // Undefined
parseInt("09") // Lo transforma a 9
5 && 2 // 2
2 && 5 // 5
5 || 0 // 5
0 || 5 // 5
[3]+[3]-[10] // 23 "Preguntar porque"
3>2>1 // False
[] == ![] // True
```

> Si te quedó alguna duda repasá con [este artículo](http://javascript.info/tutorial/object-conversion).

### Hoisting

¿Cuál es el output o salida en consola luego de ejecutar este código? Explicar por qué:

```javascript
function test() {
  console.log(a);  // Da como valor undefined ya que el comportamiento global de la variable var no funciona dentro de funciones 
  console.log(foo()); // Devuelve el numero 2 por que el valor retornado se coloca al principio del scope de la funcion.

  var a = 1;
  function foo() {
    return 2;
  }
}

test();
```

Y el de este código? :

```javascript
var snack = "Meow Mix";

function getFood(food) {
  if (food) {
    var snack = "Friskies";
    return snack;
  }
  return snack;
}

getFood(false); // Esta invocacion de funcion no realizara ningun cambio a la variable snack por que se le esta dando como argumento "false" y la funcion tiene una condicion al dar true.
```

### This

¿Cuál es el output o salida en consola luego de ejecutar esté código? Explicar por qué:

```javascript
var fullname = "Jhoswe Castro";
var obj = {
  fullname: "Jose Zuñiga",
  fullname: "Jorge Alonso",
  getFullname: function () {
    return this.fullname;
  },
};

console.log(obj.getFullname()); // Retorna el valor "Jorge Alonso por que es la ultima coincidencia que encuentra"

var test = obj.getFullname;

console.log(test()); // Devuelve un error por que test no es una funcion y se le esta colocando los ()
```

### Event loop

Considerando el siguiente código, ¿Cuál sería el orden en el que se muestra por consola? ¿Por qué?

```javascript
function printing() {
  console.log(1);  // Primero
  setTimeout(function () {
    console.log(2);  // Cuarto
  }, 1000);
  setTimeout(function () {
    console.log(3);  // Tercero
  }, 0);
  console.log(4);  // Segundo
}

printing(); //
```