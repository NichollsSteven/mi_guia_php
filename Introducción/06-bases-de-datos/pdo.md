# 📝 API basada en objetos PDO para conectarse a una base de datos con PHP
## 1. Conectarse al servidor con PDO

### 🔧Configuración de parámetros de conexión:
    $host = 'localhost';
    $user = 'usuario';
    $charset = 'utf8mb4';
    $db = 'nombre_bd';
    $pass = 'contraseña';

### Construcción de la cadena DSN (Data Source Name o Nombre de la fuente de datos):
    $dsn = "mysql:host=$host;dbname=$db;charset=$charset";
    
### ⚙️ Opciones de configuración DOP:
    $options = [
        PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION, // Lanza excepciones en caso de error
        PDO::ATTR_DEFAULT_FETCH_MODE => PDO::FETCH_ASSOC, // Devuelve resultados como arrays asociativos
        PDO::ATTR_EMULATE_PREPARES  => false,  // Usa preparaciones reales (mejor seguridad)
    ];
### 🛡️ Bloqueo try-catch para manejo de errores:
    try {
        $pdo = new PDO($dsn, $user, $pass, $options);
        }catch (PDOException $e){
          die($e->getCode() . " - " . $e->getMessage());
        }
### Ejemplo completo
 * Archivo: conexion.php
 * Descripción: Establece una conexión segura a una base de datos MySQL usando PDO.
 * Autor: Tu nombre o equipo
 * Fecha: 2025
   
        // Parámetros de conexión a la base de datos
        $host = 'localhost';  // Servidor de la base de datos (generalmente 'localhost')
        $db   = 'nombre_bd';  // Nombre de la base de datos
        $user = 'usuario';    // Usuario de la base de datos
        $pass = 'contraseña'; // Contraseña del usuario
       $charset = 'utf8mb4'; // Juego de caracteres (recomendado para soporte completo de UTF-8)
       $dsn = "mysql:host=$host;dbname=$db;charset=$charset";
       $options =
       [
            PDO::ATTR_ERRMODE  => PDO::ERRMODE_EXCEPTION,
            PDO::ATTR_DEFAULT_FETCH_MODE => PDO::FETCH_ASSOC,
            PDO::ATTR_EMULATE_PREPARES   => false
       ];

        try {
            // Crear una nueva instancia de PDO
            $pdo = new PDO($dsn, $user, $pass, $options);
            
        } catch (PDOException $e) {
            die("Error de conexión (" . $e->getCode() . "): " . htmlspecialchars($e->getMessage()));
        }

