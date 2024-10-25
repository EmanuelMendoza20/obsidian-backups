## Mutabilidad

La **mutabilidad** es un concepto que indica si un dato puede cambiar después de haber sido creado.

- **Datos mutables**: Pueden ser modificados directamente, sin necesidad de crear un nuevo objeto. Los objetos y arrays en JavaScript son mutables.
- **Datos inmutables**: No pueden ser modificados directamente. Si intentas cambiarlos, en realidad creas una nueva versión del dato. Los tipos primitivos, como `number`, `string` y `boolean`, son inmutables.

### Ejemplo de mutabilidad con un array:

```javascript
let arr = [1, 2, 3];
arr.push(4);  // Modificas el array original
console.log(arr);  // Resultado: [1, 2, 3, 4]
```

---

## `const` en JavaScript

La palabra clave **`const`** se usa para declarar variables **cuyo valor no puede ser reasignado**. Esto no significa que el contenido de la variable sea inmutable, simplemente que la referencia no se puede cambiar.

### Uso de `const` con tipos primitivos:

Si usas `const` con un tipo de dato primitivo, como un número o una cadena de texto, **no podrás cambiar el valor** de esa variable.

```javascript
const edad = 25;
edad = 30;  // Error: No puedes reasignar el valor de una variable const
```

### Uso de `const` con arrays u objetos:

Si usas `const` con un array u objeto, puedes modificar su contenido (agregar o eliminar elementos, cambiar propiedades) pero **no puedes reasignar** la variable a un nuevo array u objeto.

```javascript
const numeros = [1, 2, 3];
numeros.push(4);  // Esto es permitido
console.log(numeros);  // Resultado: [1, 2, 3, 4]

numeros = [5, 6, 7];  // Error: No puedes reasignar un nuevo array a 'numeros'
```

---

## Resumen

- **Mutabilidad** se refiere a la capacidad de cambiar un valor una vez que ha sido creado.
- **`const`** declara variables que no pueden ser reasignadas, pero los datos mutables dentro de ellas, como los arrays y objetos, pueden ser modificados.

