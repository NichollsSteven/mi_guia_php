# Explicacion a fondo de las Fúnciones

## 🔤 1. Longitud y posición
 ### strlen($str): Devuelve la longitud de una cadena.
    echo strlen("Hola"); // 4

###  strpos($haystack, $needle): Encuentra la posición de la primera aparición de una subcadena.
    echo strpos("Hola mundo", "mundo"); // 5

###  strrpos($haystack, $needle): Encuentra la posición de la última aparición de una subcadena.
    echo strrpos("hola hola", "hola"); // 5

## ✂️ 2. Extracción, División y Unión
### substr($str, $start, $length = null): Extrae una parte de la cadena.
    echo substr("Hola mundo", 0, 4); // "Hola"

### explode($delimiter, $str): Divide una cadena en un array usando un delimitador.
    $arr = explode(",", "manzana,pera,uva"); // ["manzana", "pera", "uva"]
### implode($glue, $pieces)o : Une elementos de un array en una cadena.join()
    echo implode("-", ["a", "b", "c"]); // "a-b-c"
### str_split($str, $length = 1): Convierte una cadena en una matriz de caracteres (o bloques).
    print_r(str_split("hola")); // ['h','o','l','a']

## 🔁 3. Reemplazo y modificación
### str_replace($search, $replace, $subject): Reemplaza todas las apariciones de una subcadena.
    echo str_replace("mundo", "PHP", "Hola mundo"); // "Hola PHP"
    
### str_ireplace($search, $replace, $subject): Igual que , pero insensible a mayúsculas/minúsculas .str_replace

### trim($str), , : Eliminan espacios (u otros caracteres) al inicio, final o ambos lados.ltrim($str)rtrim($str)
    echo trim("  Hola  "); // "Hola"

## 📏 4. Comparación y búsqueda
### strcasecmp($str1, $str2): Compara dos cadenas insensibles a mayúsculas .
### strcmp($str1, $str2): Compara dos cadenas (sensible a mayúsculas).
### strncmp($str1, $str2, $len): Compara los primeros n caracteres.

## 🧼 5. Transformación de caso
### strtolower($str):Convierte a minúsculas.
### strtoupper($str):Convierte a mayúsculas.
### ucfirst($str): Convierte la primera letra en mayúscula.
    echo ucfirst("hola mundo"); // "Hola mundo"
 ###  ucwords($str): Convierte la primera letra de cada palabra en mayúscula.


## 🔍 6.  Funciones con expresiones regulares (potentes, pero más lentas)
Estos utilizan el motor PCRE ( Perl Compatible Regular Expressions ) y son ideales para patrones complejos.
### 📌preg_match($pattern, $subject, &$matches = null)  Busca la primera coincidencia de un patrón en una cadena.
    if (preg_match("/\d{3}-\d{2}-\d{4}/", "Mi SSN es 123-45-6789", $coincidencias))
    {  echo $coincidencias[0]; // "123-45-6789"  }
    
### 📌preg_match_all($pattern, $subject, &$matches) Encuentra todas las coincidencias del patrón.
    $texto = "Emails: ana@example.com, bob@test.org";
    preg_match_all('/[\w.-]+@[\w.-]+\.\w+/', $texto, $emails);
    print_r($emails[0]); 
    // ['ana@example.com', 'bob@test.org']

### 📌preg_replace($pattern, $replacement, $subject) Reemplace todas las coincidencias con un valor (puede usar retroreferencias).
    $texto = "Fecha: 2024-05-10";
    $nuevo = preg_replace('/(\d{4})-(\d{2})-(\d{2})/', '$3/$2/$1', $texto);
    echo $nuevo; // "Fecha: 10/05/2024"

### 📌preg_split($pattern, $subject)
    Divide una cadena usando un patrón regex (más flexible que ).explode
    $palabras = preg_split('/\s+/', "Hola    mundo  PHP"); 
    // ['Hola', 'mundo', 'PHP']

### 📌preg_grep($pattern, $array)  Filtra un array usando una expresión regular.
    $archivos = ['foto.jpg', 'doc.pdf', 'imagen.png'];
    $imagenes = preg_grep('/\.(jpg|png|gif)$/i', $archivos);
    // ['foto.jpg', 'imagen.png']


