## Funciones para Cadenas

### `implode()`
- **¿Qué hace?**: Toma un array (una lista de valores) y convierte esos valores en una sola cadena de texto. Lo interesante es que puedes elegir un separador (puede ser un espacio, una coma, un guion, lo que quieras) que se colocará entre los elementos del array.
- **¿Por qué es útil?**: A veces tienes información en forma de lista (por ejemplo, una lista de nombres) y necesitas convertirla en un solo bloque de texto. Ahí es donde entra `implode()`.
  
  **Ejemplo**:
  ```php
  $array = ['Hola', 'Mundo', 'PHP'];
  $resultado = implode(' ', $array);
  echo $resultado; // Output: "Hola Mundo PHP"
  ```

### `explode()`
- **¿Qué hace?**: Lo contrario de `implode()`. Toma una cadena de texto y la divide en varios pedazos, convirtiéndolos en elementos de un array, usando un delimitador que especifiques.
- **¿Por qué es útil?**: Imagina que recibes una frase larga y quieres dividirla en palabras individuales. Ahí es donde `explode()` te ayuda.
  
  **Ejemplo**:
  ```php
  $cadena = "Hola Mundo PHP";
  $resultado = explode(' ', $cadena);
  print_r($resultado);
  ```
  - En este caso, la cadena se divide en un array usando el espacio (`' '`) como delimitador. El resultado es un array con tres elementos: `['Hola', 'Mundo', 'PHP']`.

---

### `trim()`
- **¿Qué hace?**: Elimina espacios en blanco (u otros caracteres específicos) al principio y al final de una cadena de texto.
- **¿Por qué es útil?**: Cuando recibes texto de un formulario, los usuarios suelen dejar espacios en blanco sin querer. `trim()` te ayuda a limpiar esos espacios, evitando errores en la comparación de textos.

  **Ejemplo**:
  ```php
  $cadena = "  Hola Mundo  ";
  $resultado = trim($cadena);
  echo $resultado; // Output: "Hola Mundo"
  ```

---

## Redirección con `header()`

### `header('Location: url')`
- **¿Qué hace?**: Redirige al usuario a otra página web automáticamente.
- **¿Por qué es útil?**: Si necesitas mover a un usuario a otra página (después de que envíen un formulario o inicien sesión, por ejemplo), `header()` te permite hacerlo sin que tengan que hacer clic en un enlace.
  
  **Importante**: Debes usar `header()` **antes** de imprimir cualquier contenido HTML, de lo contrario dará un error.

  **Ejemplo**:
  ```php
  header('Location: index.php');
  exit;
  ```
  - Esto redirige al usuario a "index.php". El `exit` se utiliza para detener el script, evitando que se ejecute cualquier código después de la redirección.

---

## Manejo de Archivos de Texto

Trabajar con archivos de texto en PHP es muy común, ya sea para guardar datos o para leer información que ya tienes.

### Operaciones Básicas

1. **Abrir un archivo**:
    - **Función**: `fopen()`
    - **¿Qué hace?**: Abre un archivo para que puedas leerlo, escribir en él, o ambas cosas. Debes especificar cómo lo vas a usar: solo lectura, solo escritura, etc.
    - **Ejemplo**:
      ```php
      $archivo = fopen('datos.txt', 'r'); // Abre el archivo para solo lectura
      ```

---
# Modos de apertura en `fopen()` en PHP

Cuando trabajas con archivos en PHP, las letras que se usan al abrir un archivo con `fopen()` indican el **modo** en el que quieres interactuar con ese archivo.

## Modos de apertura más comunes:

### 1. **`r` - Solo lectura (read)**
- **Descripción**: Abre el archivo para solo **lectura**. El puntero comienza al principio del archivo.
- **Condición**: El archivo **debe existir**; si no existe, dará error.
- **Ejemplo**:
  ```php
  $archivo = fopen('archivo.txt', 'r'); // Solo lectura
  ```

### 2. **`r+` - Lectura y escritura**
- **Descripción**: Abre el archivo para **lectura y escritura**. El puntero comienza al principio del archivo.
- **Condición**: El archivo debe existir.
- **Ejemplo**:
  ```php
  $archivo = fopen('archivo.txt', 'r+'); // Lectura y escritura
  ```

### 3. **`w` - Solo escritura (write)**
- **Descripción**: Abre el archivo para **escritura**. Si el archivo ya contiene algo, el contenido se **sobrescribe**. Si el archivo no existe, PHP intenta crearlo.
- **Condición**: Si el archivo existe, su contenido se perderá porque se sobrescribe.
- **Ejemplo**:
  ```php
  $archivo = fopen('archivo.txt', 'w'); // Solo escritura
  ```

### 4. **`w+` - Escritura y lectura**
- **Descripción**: Abre el archivo para **lectura y escritura**, pero el contenido se sobrescribe como en `w`. Si el archivo no existe, se creará.
- **Condición**: Como en `w`, el archivo se sobrescribe.
- **Ejemplo**:
  ```php
  $archivo = fopen('archivo.txt', 'w+'); // Escritura y lectura
  ```

### 5. **`a` - Solo agregar (append)**
- **Descripción**: Abre el archivo para **escritura**, pero **sin sobrescribir** el contenido existente. El puntero se posiciona al final del archivo para agregar nuevo contenido. Si el archivo no existe, PHP lo creará.
- **Ejemplo**:
  ```php
  $archivo = fopen('archivo.txt', 'a'); // Solo agregar
  ```

### 6. **`a+` - Agregar y lectura**
- **Descripción**: Abre el archivo para **lectura y escritura**. Como en `a`, el puntero se posiciona al final del archivo para escribir nuevo contenido. Si el archivo no existe, se creará.
- **Ejemplo**:
  ```php
  $archivo = fopen('archivo.txt', 'a+'); // Agregar y lectura
  ```

---

## Resumen de las letras:
- **`r`**: Solo lectura (no cambia el contenido del archivo).
- **`r+`**: Lectura y escritura (no cambia el contenido, pero puede escribir).
- **`w`**: Solo escritura (sobrescribe todo el archivo).
- **`w+`**: Escritura y lectura (sobrescribe todo, pero puedes leer).
- **`a`**: Solo agregar (escribe al final sin borrar lo anterior).
- **`a+`**: Agregar y lectura (escribe al final sin borrar y puedes leer).

## Ejemplo práctico:
Si quieres **solo leer** un archivo y asegurarte de no cambiar nada:
```php
$archivo = fopen('archivo.txt', 'r');
```

Si quieres **escribir** en un archivo, pero **sin borrar lo que ya tiene**:
```php
$archivo = fopen('archivo.txt', 'a'); // Agrega al final
```

Si quieres **escribir** y también **leer** sin perder datos:
```php
$archivo = fopen('archivo.txt', 'a+'); // Lee y agrega al final
```

---

2. **Escribir en un archivo**:
    - **Función**: `fwrite()`
    - **¿Qué hace?**: Escribe datos en un archivo.
    - **Ejemplo**:
      ```php
      fwrite($archivo, "Texto a escribir");
      ```

3. **Leer un archivo**:
    - **Función**: `fgets()`
    - **¿Qué hace?**: Lee una línea del archivo a la vez.
    - **Ejemplo**:
      ```php
      $linea = fgets($archivo); // Lee una línea del archivo
      ```

4. **Cerrar un archivo**:
    - **Función**: `fclose()`
    - **¿Qué hace?**: Cierra el archivo después de que termines de trabajar con él (muy importante).
    - **Ejemplo**:
      ```php
      fclose($archivo);
      ```

### Ejemplo Completo
- Aquí tienes un ejemplo de cómo escribir en un archivo y luego leerlo línea por línea:
  ```php
  // Abrir archivo para escribir
  $archivo = fopen('miarchivo.txt', 'a'); // Modo 'a' agrega al final del archivo
  fwrite($archivo, "Nueva línea de texto
");
  fclose($archivo);

  // Abrir archivo para leer
  $archivo = fopen('miarchivo.txt', 'r'); // Modo 'r' para lectura
  while (!feof($archivo)) {
      echo fgets($archivo); // Lee línea por línea
  }
  fclose($archivo);
  ```

---

## Subir Archivos

PHP permite recibir archivos desde un formulario HTML y guardarlos en el servidor.

### ¿Cómo funciona?
1. En el formulario HTML, el input que permite seleccionar archivos debe tener el atributo `enctype="multipart/form-data"`.
2. Al enviar el formulario, los archivos se almacenan en el superglobal `$_FILES`.
3. Luego, con la función `move_uploaded_file()`, puedes mover el archivo desde la ubicación temporal al destino final en tu servidor.

### Ejemplo de Subida de Archivos

1. **Formulario (HTML)**:
    ```html
    <form action="guardar.php" method="POST" enctype="multipart/form-data">
        <input type="file" name="archivo">
        <button type="submit">Subir</button>
    </form>
    ```

2. **PHP para guardar el archivo**:
    ```php
    $origen = $_FILES['archivo']['tmp_name'];
    $destino = 'subidas/' . $_FILES['archivo']['name'];
    move_uploaded_file($origen, $destino);
    echo "Archivo subido correctamente.";
    ```

---

## Manipulación Avanzada

### Crear carpetas
- **¿Qué hace?**: Si necesitas crear una carpeta en tu servidor para guardar archivos, puedes hacerlo con `mkdir()`.
- **Ejemplo**:
  ```php
  if (!file_exists('carpeta')) {
      mkdir('carpeta');
  }
  ```

### Eliminar archivos
- **¿Qué hace?**: Puedes eliminar archivos con la función `unlink()`.
- **Ejemplo**:
  ```php
  unlink('ruta/archivo.txt');
  ```

---

## Resumen
- **`implode()` y `explode()`**: Te ayudan a trabajar con arrays y cadenas de texto, ya sea para unir o dividir información.
- **`trim()`**: Ideal para limpiar espacios o caracteres extraños al principio y al final de una cadena.
- **`header()`**: Se usa para redireccionar a otras páginas, pero debe colocarse antes de cualquier salida HTML.
- **Manejo de archivos**: Puedes abrir, leer, escribir y cerrar archivos de texto.
- **Subir archivos**: PHP permite manejar formularios con archivos y guardarlos en el servidor usando `$_FILES`.
