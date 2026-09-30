# Truthy, falsy y nullish

En cualquier lenguade de programación existen los tipos de datos booleano: `true` y `false`. Son imprescindibles.

Pero JavaScript tiene otros conceptos relacionados con las condiciones: valores truthy, falsy y nullish, así como el encadenamiento opcional `?.` y el operador de coalescencia nula `??`. Con estos conceptos codificarás de una forma más concisa y potente.

Date de alta en la plataforma exercism y realiza el siguiente [apartado](https://exercism.org/es-ES/tracks/javascript/exercises/amusement-park). 
Entrega los códigos en un repositorio privado compartido conmigo `lmagarin`.

Introducción
A diferencia de muchos otros lenguajes, en JavaScript hay dos entidades distintas que representan la ausencia de un valor (significativo). Existen null y undefined.

Null
El valor primitivo null se usa como un «valor vacío» intencionado para variables de cualquier tipo.

let name = null;
// name is intentionally set to "empty" because it is not
// available
Puedes comprobar si una variable es null con el operador de igualdad estricta ===.

let name = null;

name === null;
// => true
Undefined
Una variable a la que no se le ha asignado un valor es de tipo undefined.1

Esto significa que, mientras que null representa un valor vacío (pero sigue siendo un valor), undefined representa la ausencia total de un valor. 🤯

undefined aparece en distintos contextos.

Si una variable se declara sin un valor (inicialización), es undefined.
Si intentas acceder al valor de una clave inexistente en un objeto, obtienes undefined.
Si una función no devuelve un valor, el resultado es undefined.
Si no se pasa un argumento a una función, este es undefined, a menos que ese argumento tenga un valor predeterminado.
let name;
console.log(name);
// => undefined
Puedes comprobar si una variable es undefined con el operador de igualdad estricta ===.

let name;

name === undefined;
// => true
Encadenamiento opcional
Si intentas obtener un valor anidado en un objeto pero la clave padre no existe, JavaScript lanzará un error. Para evitar esto fácilmente, el encadenamiento opcional se añadió a la especificación del lenguaje en 2020. Con el operador de encadenamiento opcional ?. puedes asegurarte de que JavaScript solo intente acceder a la clave anidada si el padre no era null ni undefined. En caso contrario, se devuelve undefined.

const obj = {
  address: {
    street: 'Trincomalee Highway',
    city: 'Batticaloa',
  },
};

obj.address.zipCode;
// => undefined

obj.residence.street;
// => TypeError: Cannot read property 'street' of undefined

obj.residence?.street;
// => undefined
Coalescencia nula
Hay situaciones en las que quieres aplicar un valor predeterminado por si una variable es null o undefined (pero solo en ese caso). Para resolver esto, el operador de coalescencia nula ?? se introdujo en 2020. Devuelve el operando de la derecha solo cuando el operando de la izquierda es null o undefined. En caso contrario, se devuelve el operando de la izquierda.

let amount = null;
amount = amount ?? 1;
// => 1

amount = 0;
amount = amount ?? 1;
// => 0
[1] Undefined, MDN. (2021). https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined (consultado el 4 de junio de 2021).

Instrucciones
Tu trabajo consiste en proporcionar y mantener partes del sistema informático de un parque de atracciones. En concreto, eres responsable del programa que gestiona a los visitantes y las entradas.

Primero, crearás un nuevo visitante en el sistema. Después, proporcionarás una función para revocar una entrada. En las tareas 3 y 4, trabajarás en el sistema de seguimiento de entradas que ayuda a evitar la falsificación. Por último, ayudarás a adaptar el sistema a los nuevos requisitos legales.
