✅  ##    1. Funciones básicas de cadena (rápidas y simples)
#  php  strlen()– longitud de la cadena
#  php  strpos(), – posición de subcadena strrpos()
#  php  substr()– extraer parte de la cadena
#  php  str_replace()/ – reemplazo simple str_ireplace()
#  php  trim(), , – eliminar espacios ltrim() rtrim()
#  php  strtolower(), , , – cambiar mayúsculas/minúsculas strtoupper()ucfirst()ucwords()
#  php  explode()/ – dividir y unir cadenas implode()
#  php  str_repeat()– repetir una cadena
#  php  str_contains(), , (PHP 8+)  str_starts_with()  str_ends_with()


🔤    ## 1. Longitud y posición
#  php strlen($str): Devuelve la longitud de una cadena.
    echo strlen("Hola"); // 4

#  php strpos($haystack, $needle): Encuentra la posición de la primera aparición de una subcadena.
    echo strpos("Hola mundo", "mundo"); // 5

#  php strrpos($haystack, $needle): Encuentra la posición de la última aparición de una subcadena.
    echo strrpos("hola hola", "hola"); // 5

✂️  ## 2. Extracción, División y Unión
#  php substr($str, $start, $length = null): Extrae una parte de la cadena.
    echo substr("Hola mundo", 0, 4); // "Hola"

#  php explode($delimiter, $str): Divide una cadena en un array usando un delimitador.
    $arr = explode(",", "manzana,pera,uva"); // ["manzana", "pera", "uva"]
#  php implode($glue, $pieces)o : Une elementos de un array en una cadena.join()
    echo implode("-", ["a", "b", "c"]); // "a-b-c"
#  php str_split($str, $length = 1): Convierte una cadena en una matriz de caracteres (o bloques).
    print_r(str_split("hola")); // ['h','o','l','a']

🔁  ## 3. Reemplazo y modificación
#  php str_replace($search, $replace, $subject): Reemplaza todas las apariciones de una subcadena.
    echo str_replace("mundo", "PHP", "Hola mundo"); // "Hola PHP"
    
#  php str_ireplace($search, $replace, $subject): Igual que , pero insensible a mayúsculas/minúsculas .str_replace

#  php trim($str), , : Eliminan espacios (u otros caracteres) al inicio, final o ambos lados.ltrim($str)rtrim($str)
    echo trim("  Hola  "); // "Hola"

📏  ## 4. Comparación y búsqueda
#  php strcasecmp($str1, $str2): Compara dos cadenas insensibles a mayúsculas .
#  php strcmp($str1, $str2): Compara dos cadenas (sensible a mayúsculas).
#  php strncmp($str1, $str2, $len): Compara los primeros n caracteres.

🧼  ## 5. Transformación de caso
#  php strtolower($str):Convierte a minúsculas.
#  php strtoupper($str):Convierte a mayúsculas.
#  php ucfirst($str): Convierte la primera letra en mayúscula.
#  php ucwords($str): Convierte la primera letra de cada palabra en mayúscula.

🔍  ## 6.  Funciones con expresiones regulares (potentes, pero más lentas)
Estos utilizan el motor PCRE ( Perl Compatible Regular Expressions ) y son ideales para patrones complejos.
#  php  📌preg_match($pattern, $subject, &$matches = null)  Busca la primera coincidencia de un patrón en una cadena.
    if (preg_match("/\d{3}-\d{2}-\d{4}/", "Mi SSN es 123-45-6789", $coincidencias))
    {  echo $coincidencias[0]; // "123-45-6789"  }
    
#  php  📌preg_match_all($pattern, $subject, &$matches) Encuentra todas las coincidencias del patrón.
    $texto = "Emails: ana@example.com, bob@test.org";
    preg_match_all('/[\w.-]+@[\w.-]+\.\w+/', $texto, $emails);
    print_r($emails[0]); 
    // ['ana@example.com', 'bob@test.org']

#  php  📌preg_replace($pattern, $replacement, $subject) Reemplace todas las coincidencias con un valor (puede usar retroreferencias).
    $texto = "Fecha: 2024-05-10";
    $nuevo = preg_replace('/(\d{4})-(\d{2})-(\d{2})/', '$3/$2/$1', $texto);
    echo $nuevo; // "Fecha: 10/05/2024"

#  php  📌preg_split($pattern, $subject)
    Divide una cadena usando un patrón regex (más flexible que ).explode
    $palabras = preg_split('/\s+/', "Hola    mundo  PHP"); 
    // ['Hola', 'mundo', 'PHP']

#  php  📌preg_grep($pattern, $array)  Filtra un array usando una expresión regular.
    $archivos = ['foto.jpg', 'doc.pdf', 'imagen.png'];
    $imagenes = preg_grep('/\.(jpg|png|gif)$/i', $archivos);
    // ['foto.jpg', 'imagen.png']




1
echo ucfirst("hola mundo"); // "Hola mundo"
