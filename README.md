# Truthy, falsy y nullish

En cualquier lenguade de programación existen los tipos de datos booleano: `true` y `false`. Son imprescindibles.

Pero JavaScript tiene otros conceptos relacionados con las condiciones: valores truthy, falsy y nullish, así como el encadenamiento opcional `?.` y el operador de coalescencia nula `??`. Con estos conceptos codificarás de una forma más concisa y potente.

Date de alta en la plataforma exercism y realiza el siguiente [apartado](https://exercism.org/es-ES/tracks/javascript/exercises/amusement-park). 
Entrega los códigos en un repositorio privado compartido conmigo `lmagarin`.

# Introducción
A diferencia de muchos otros lenguajes, en JavaScript hay dos entidades distintas que representan la ausencia de un valor (significativo). Existen null y undefined.

# Null
El valor primitivo null se usa como un «valor vacío» intencionado para variables de cualquier tipo.

let name = null;
// name is intentionally set to "empty" because it is not
// available
Puedes comprobar si una variable es null con el operador de igualdad estricta ===.

let name = null;

name === null;
// => true

# Undefined
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

# Encadenamiento opcional
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

# Coalescencia nula
Hay situaciones en las que quieres aplicar un valor predeterminado por si una variable es null o undefined (pero solo en ese caso). Para resolver esto, el operador de coalescencia nula ?? se introdujo en 2020. Devuelve el operando de la derecha solo cuando el operando de la izquierda es null o undefined. En caso contrario, se devuelve el operando de la izquierda.

let amount = null;
amount = amount ?? 1;
// => 1

amount = 0;
amount = amount ?? 1;
// => 0
[1] Undefined, MDN. (2021). https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined (consultado el 4 de junio de 2021).

# Instrucciones
Tu trabajo consiste en proporcionar y mantener partes del sistema informático de un parque de atracciones. En concreto, eres responsable del programa que gestiona a los visitantes y las entradas.

Primero, crearás un nuevo visitante en el sistema. Después, proporcionarás una función para revocar una entrada. En las tareas 3 y 4, trabajarás en el sistema de seguimiento de entradas que ayuda a evitar la falsificación. Por último, ayudarás a adaptar el sistema a los nuevos requisitos legales.

# 1. Crea un nuevo visitante
Cuando los visitantes llegan al parque de atracciones por primera vez, tienen que registrarse introduciendo su nombre y su edad en un terminal y aceptando los términos y condiciones. Por supuesto, también tienen que comprar una entrada. Cada entrada tiene un identificador como H32AZ123.

Escribe una función createVisitor que acepte tres argumentos.

El nombre del visitante.
La edad del visitante.
El identificador de la entrada que ha comprado el visitante.
La función debe devolver un objeto que contenga esta información. Las claves del objeto deben llamarse name, age y ticketId.

<img width="455" height="154" alt="image" src="https://github.com/user-attachments/assets/a3bfc163-ee6a-4424-ae4e-94b8fc7f196a" />



# 2. Revoca la entrada
Cuando las personas salen del parque de atracciones, su entrada se revoca. Si vuelven, tienen que comprar una nueva. Para ahorrar tiempo a los visitantes habituales, solo tienen que registrarse una vez y la información del visitante se conserva para las visitas posteriores.

Eso significa que, cuando un visitante sale del parque, solo hay que invalidar su entrada, pero el resto del objeto del visitante debe permanecer igual. Implementa la función revokeTicket que acepte un objeto de visitante, establezca el identificador de la entrada a null y devuelva el objeto después.

<img width="338" height="126" alt="image" src="https://github.com/user-attachments/assets/732d4f49-a1e9-4a70-acfc-eb2b7f03e772" />



# 3. Determina el estado de la entrada
Para evitar la falsificación, los identificadores de las entradas son únicos. Una vez que se imprime una entrada, su identificador se añade como clave en un objeto del sistema para poder hacerle un seguimiento.

Antes de vender la entrada a un visitante, se almacena con el valor null en el objeto de seguimiento de entradas. Cuando se vende a un visitante, se asigna el nombre del visitante como valor. Cuando los empleados dudan de la validez de una entrada, tienen que consultar el estado de la entrada en el sistema.

Implementa una función ticketStatus que acepte el objeto de seguimiento y un identificador de entrada como argumentos. Debe devolver uno de los siguientes resultados.

'unknown ticket id' si el identificador no se encontró en el objeto de seguimiento
'not sold' en caso de que la entrada se imprimiera pero no se vendiera
'sold to {name}' donde {name} es el nombre del visitante si la entrada se vendió

<img width="403" height="211" alt="image" src="https://github.com/user-attachments/assets/ac975470-5ae8-4ddb-b67b-57294057f869" />


# 4. Mejora la respuesta del estado de la entrada
Al cabo de un tiempo, los empleados te comentan que quieren que el estado de la entrada sea más fácil de entender a primera vista. Solo quieren ver el nombre del visitante o que la entrada no es válida.

Escribe una función simpleTicketStatus que acepte los mismos argumentos que ticketStatus en la tarea 3. Esta función solo devuelve uno de dos resultados diferentes.

el nombre del visitante si la entrada se vendió
'invalid ticket !!!' si la entrada aún no se ha vendido o el identificador no se encontró en el objeto de seguimiento

<img width="535" height="116" alt="image" src="https://github.com/user-attachments/assets/d33587c5-6e76-4dca-b1a7-5f1ebd3058bd" />

# 5. Determina la versión de los términos y condiciones
Debido a nuevos requisitos legales, los objetos de visitante recién creados ahora también contienen información detallada sobre los «Términos y condiciones generales» (GTC) que el usuario ha aceptado. A continuación puedes ver un ejemplo del nuevo objeto de visitante.

Los cajeros del parque de atracciones ahora tienen que comprobar si un visitante necesita firmar una nueva versión de los GTC. Para ello, implementa una función gtcVersion que acepte un objeto de visitante como argumento y devuelva la versión de los GTC si está disponible. Si la información de la versión no está disponible, no debe devolverse nada.

<img width="502" height="136" alt="image" src="https://github.com/user-attachments/assets/3c63c959-db05-49c8-b87e-da3e0a8860af" />
