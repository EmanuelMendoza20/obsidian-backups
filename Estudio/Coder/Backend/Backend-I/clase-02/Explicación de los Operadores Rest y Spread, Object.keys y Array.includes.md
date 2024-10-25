
### **`1. Object.keys()`**

==`Object.keys()`== es un método que te permite obtener un **array** con los nombres (claves) de las propiedades de un objeto. Es como hacer un inventario de las propiedades de ese objeto.

#### **Ejemplo:**

Imagina que tienes un objeto que representa a un estudiante:

```js
let estudiante = {
  nombre: "Emanuel",
  edad: 20,
  carrera: "Programación"
};

let claves = Object.keys(estudiante);
console.log(claves); 
// Resultado: ["nombre", "edad", "carrera"]
```

En este caso, ==Object.keys(estudiante)== devuelve un array que contiene los nombres de las propiedades del objeto estudiante. Es útil cuando quieres saber qué propiedades tiene un objeto sin tener que recorrerlo manualmente.

### **2. `Array.includes()`**

==`Array.includes()`== es un método que se utiliza para determinar si un **array** contiene un valor específico. Devuelve `true` si el valor se encuentra en el array y `false` si no.

#### **Ejemplo:**

Imagina que tienes un array de frutas:

```js
let frutas = ["manzana", "banana", "naranja"];

let tieneBanana = frutas.includes("banana");
console.log(tieneBanana); 
// Resultado: true

let tieneFresa = frutas.includes("fresa");
console.log(tieneFresa); 
// Resultado: false
```

En este caso, `frutas.includes("banana")` devuelve `true` porque "banana" está presente en el array. Por otro lado, `frutas.includes("fresa")` devuelve `false` porque "fresa" no está en la lista.

### **Resumen**

- **`Object.keys(objeto)`**: Devuelve un array con las claves (nombres de propiedades) de un objeto.
- **`Array.includes(valor)`**: Verifica si un array contiene un valor específico, devolviendo `true` o `false`.

Espero que esta explicación te haya aclarado las cosas. ¡Si tienes más preguntas, aquí estoy!

---

Los operadores **rest** y **spread** parecen iguales porque ambos usan los tres puntitos (`...`), pero tienen funciones diferentes dependiendo de cómo y dónde los uses. Vamos a desmenuzarlo con ejemplos claros y un toque divertido.

## **Operador Spread (`...`)**
El operador **spread** "expande" algo que ya está agrupado (como un array o un objeto) en sus partes individuales. Piensa que tienes una pizza (el array completo) y con el operador spread, es como si estuvieras sacando cada rebanada de la pizza.

### **Ejemplo con Arrays:**
```js
const partes = ['tomate', 'queso', 'pepperoni'];
const nuevaPizza = ['masa', ...partes, 'aceitunas'];
console.log(nuevaPizza);
// Resultado: ['masa', 'tomate', 'queso', 'pepperoni', 'aceitunas']
```
En este caso, el operador **spread** ha sacado los ingredientes individuales de `partes` y los ha colocado en `nuevaPizza`.

### **Ejemplo con Objetos:**
```js
const infoBasica = { nombre: 'Harry', casa: 'Gryffindor' };
const infoCompleta = { ...infoBasica, varita: 'Acebo' };
console.log(infoCompleta);
// Resultado: { nombre: 'Harry', casa: 'Gryffindor', varita: 'Acebo' }
```
Aquí, el operador **spread** ha "expansado" el contenido de `infoBasica` dentro del nuevo objeto `infoCompleta`.

## **Operador Rest (`...`)**
El operador **rest** funciona al revés. En lugar de expandir, lo que hace es *agrupar* varios elementos en una sola entidad, como si juntarás muchas rebanadas de pizza en una sola caja.

### 1. **En funciones con múltiples argumentos**
Cuando no sabes cuántos argumentos va a recibir una función, puedes usar **rest** para capturarlos en un array.

```js
function concatenarCadenas(...cadenas) {
  return cadenas.join(' ');
}

console.log(concatenarCadenas('¡Hola', 'mundo!', 'Estoy', 'aprendiendo', 'Node.js!'));
// Resultado: '¡Hola mundo! Estoy aprendiendo Node.js!'
```

### 2. **Rest en Desestructuración de Arrays**
Capturas una parte del array y el resto lo agrupas en una nueva variable.

```js
const numeros = [1, 2, 3, 4, 5];
const [primero, segundo, ...resto] = numeros;

console.log(primero); // 1
console.log(segundo); // 2
console.log(resto);    // [3, 4, 5]
```

### 3. **Rest en Desestructuración de Objetos**
Igual que en arrays, puedes capturar algunas propiedades y agrupar el resto.

```js
const persona = { nombre: 'Hermione', casa: 'Gryffindor', varita: 'Vid', edad: 20 };
const { nombre, ...otrasPropiedades } = persona;

console.log(nombre);           // 'Hermione'
console.log(otrasPropiedades); // { casa: 'Gryffindor', varita: 'Vid', edad: 20 }
```

### 4. **Rest para Combinar Arrays en Funciones**
Usa **rest** para recibir varios arrays y combinarlos en uno solo.

```js
function combinarArrays(...arrays) {
  return arrays.flat(); // aplana los arrays en un solo nivel
}

const frutas = ['manzana', 'pera'];
const vegetales = ['zanahoria', 'lechuga'];
const carnes = ['pollo', 'res'];

console.log(combinarArrays(frutas, vegetales, carnes));
// Resultado: ['manzana', 'pera', 'zanahoria', 'lechuga', 'pollo', 'res']
```

### 5. **Rest en Parámetros Opcionales**
Cuando una función tiene parámetros fijos y otros opcionales, **rest** los agrupa en un solo array.

```js
function hacerMagia(conjuro, ...ingredientes) {
  console.log(`Usando el conjuro: ${conjuro}`);
  console.log('Ingredientes:', ingredientes);
}

hacerMagia('Wingardium Leviosa', 'pluma', 'varita', 'fuerza mental');
// Resultado:
// Usando el conjuro: Wingardium Leviosa
// Ingredientes: ['pluma', 'varita', 'fuerza mental']
```

## **Resumen**
- **Spread (`...`)**: Toma algo grande (como un array u objeto) y lo *expande* en partes individuales.
- **Rest (`...`)**: Toma varias cosas y las *agrupa* en una sola (como agrupar argumentos o el "resto" de un array u objeto).

---

