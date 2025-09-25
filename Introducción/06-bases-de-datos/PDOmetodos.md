# Métodos PDO más importantes para consultas SQL.
## 📘 Métodos PDO: Consulta, Ejecución y Recuperación de Datos

### 1. ⚙️ Métodos de Consulta
    PDO::query($sql)
    Función : Ejecuta directamente una consulta SQL y devuelve un objeto .PDOStatement
    Uso típico : Para consultas simples que devuelven resultados (SELECT).
    Ejemplo: $stmt = $pdo->query("SELECT * FROM usuarios");

    PDO::prepare($sql)
    Función : Preparar una consulta SQL para ser ejecutada posteriormente.
    Devuelve : Un objeto listo para vincular parámetros y ejecutar.PDOStatement
    Ventaja : Seguridad contra inyección SQL cuando se usan parámetros.
    Ejemplo :$stmt = $pdo->prepare("SELECT * FROM usuarios WHERE id = ?");

### 2. ▶️ Métodos de Ejecución
    PDO::exec($sql)
    Función : Ejecuta una consulta SQL que no devuelve resultados .
    Devuelve : El número de filas afectadas (por ejemplo, en INSERT, UPDATE, DELETE).
    No devuelve un objeto PDOStatement, por lo tanto, no puedes recuperar datos con fetch().
    Ejemplo :$filasAfectadas = $pdo->exec("DELETE FROM usuarios WHERE activo = 0"); 
    echo "Filas eliminadas: " . $filasAfectadas;

    PDOStatement::execute([$params])
    Función : Ejecuta una consulta preparada ( ).prepare()
    Puede recibir una matriz con los valores de los parámetros.
    Es el método principal para ejecutar consultas preparadas.
    Ejemplo :$stmt = $pdo->prepare("INSERT INTO usuarios (nombre, email) VALUES (?, ?)");
    $stmt->execute(['Ana', 'ana@example.com']);

    ✅ Nota importante : Cuando se reciba datos del usuario por medio de (formularios, URL, etc.)  Siempre usa prepare() + execute() para evitar inyecciones SQL.

###  3. 🔍 Métodos para la Recuperación de Resultados
    PDOStatement::fetch($fetch_style)
    
    Función : Recuperar una sola fila del resultado de una consulta.
    Estilos comunes :
    PDO::FETCH_ASSOC → array asociativo (por nombre de columna),
    PDO::FETCH_NUM → matriz numérica,
    PDO::FETCH_OBJ → objeto con propiedades.
    Ejemplo : $stmt = $pdo->query("SELECT nombre, email FROM usuarios LIMIT 1");
    $fila = $stmt->fetch(PDO::FETCH_ASSOC);
    echo $fila['nombre'];




