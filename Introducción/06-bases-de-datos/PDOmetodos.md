# Métodos PDO más importantes para consultas SQL.
## 📘 Métodos PDO: Consulta, Ejecución y Recuperación de Datos

### 1. ⚙️ Métodos de Consulta
    PDO::query($sql
    Función : Ejecuta directamente una consulta SQL y devuelve un objeto PDOStatement
    Uso típico : Para consultas simples que devuelven resultados (SELECT).
    Ejemplo: 
        $stmt = $pdo->query("SELECT * FROM usuarios");


    PDO::prepare($sql)
    Función : Preparar una consulta SQL para ser ejecutada posteriormente.
    Devuelve Un objeto PDOStatement: Listo para vincular parámetros y ejecutar.
    Ventaja : Seguridad contra inyección SQL cuando se usan parámetros.
    Ejemplo: 
        $stmt = $pdo->prepare("SELECT * FROM usuarios WHERE id = ?");

### 2. ▶️ Métodos de Ejecución
    PDO::exec($sql).
    Función : Ejecuta una consulta SQL que no devuelve resultados .
    Devuelve : El número de filas afectadas (por ejemplo, en INSERT, UPDATE, DELETE).
    No devuelve un objeto PDOStatement, por lo tanto, no se pueden recuperar datos con fetch().
    Ejemplo: 
        $filasAfectadas = $pdo->exec("DELETE FROM usuarios WHERE activo = 0"); 
        echo "Filas eliminadas: " . $filasAfectadas;
        

    PDOStatement::execute([$params]).
    Función : Ejecuta una consulta preparada por medio el metodo prepare()
    Puede recibir una matriz con los valores de los parámetros.
    Es el método principal para ejecutar consultas preparadas.
    Ejemplo:
        $stmt = $pdo->prepare("INSERT INTO usuarios (nombre, email) VALUES (?, ?)");
        $stmt->execute(['Ana', 'ana@example.com']);

    ✅ Nota importante: Cuando se reciba datos del usuario por medio de (formularios, URL, etc.)
    Siempre usar prepare() + execute() para evitar inyecciones SQL.

###  3. 🔍 Métodos para la Recuperación de Resultados
    PDOStatement::fetch($fetch_style)
    
    Función : Recuperar una sola fila del resultado de una consulta.
    Ejemplo: 
        $stmt = $pdo->query("SELECT nombre, email FROM usuarios LIMIT 1");
        $fila = $stmt->fetch(PDO::FETCH_ASSOC);
        echo $fila['nombre'];
        
    PDOStatement::fetchAll($fetch_style).
    
    Función : Recupera todas las filas del resultado como un array.
    Ideal para mostrar listados completos.
    Ejemplo :
        $stmt = $pdo->query("SELECT * FROM usuarios");
        $usuarios = $stmt->fetchAll(PDO::FETCH_ASSOC);
        foreach ($usuarios as $usuario) {
            echo $usuario['nombre'] . "<br>";
        }
        
    EL parametro $fetch_style indica el formato en que recibiremos los resultados :
    PDO::FETCH_ASSOC → array asociativo (por nombre de columna),
    PDO::FETCH_NUM → matriz numérica,
    PDO::FETCH_OBJ → objeto con propiedades.
    
    Otros métodos de recuperación:
    $stmt->fetchColumn($index);  // Devuelve un solo valor de la primera fila, columna $index
    $stmt->fetchObject($class);  // Devuelve un objeto de clase especificada
    
### 📌 ¿Qué es PDOStatement ?
    Es el objeto que representa una consulta SQL en PDO que ya ha sido ejecutada por Metodo 
    query() o preparada por el Metodo prepare():

    Si se ha usado el metodo prepare(): Permite Ejecutarlo, vicular parametros, Conocer su
    estado y Obtener resultados; si se usa query no puede Ejecutar y Vincular Parametros
    pero si el resto.
    
    Ejecutarla por medio del metodo principal execute()
    
    Vincular valores a los parámetros de la consulta:
        a) Directamente en execute()
            $stmt = $pdo->prepare("SELECT * FROM usuarios WHERE email = ?");
            $stmt->execute(['juan@example.com']);
            
        b) Con bindValue()
            $stmt = $pdo->prepare("SELECT * FROM usuarios WHERE email = ?");
            $stmt->bindValue(1, 'juan@example.com');
            $stmt->execute();
            
        c) Con bindParam()
            $email = 'juan@example.com';
            $stmt = $pdo->prepare("SELECT * FROM usuarios WHERE email = ?");
            $stmt->bindParam(1, $email);
            $stmt->execute();

        d) Con Placeholder
            $stmt = $pdo->prepare("SELECT * FROM usuarios WHERE email = :email");
            $param=[':email' => "juan@example.com"]
            $stmt->execute($param) o tambien stmt->execute([':email' => "juan@example.com"]);
  
    Obtener resultados por medio de los metodos:
        a) fecth($style): // Recupera una fila de los resultados Obtenidos de la consulta SQL
        
        b) fetchAll($style): // Recupera todas las filas de los resultados Obtenidos de la consulta SQL
        
        c) fetchColumn(): // Devuelve un solo valor de la primera fila, columna $index
        
        d) fetchObject(): // // Devuelve un objeto de clase especificada
        
    Conocer su estado: Por medio de los metodos:
         a) rowCount(): Número de filas afectadas (útil en ACTUALIZAR/BORRAR/INSERTAR).
        
        b) columnCount(): Número de columnas en el conjunto de resultados.
        
        c) errorCode(): Código de error SQL (si ocurrió uno).
        
        d) errorInfo(): Información detallada del error (array con código, driver, mensaje)

    ✅ Consejo final : Usar siempre prepare() + execute() para consultas dinámicas
        y para consultas estáticas sin parámetros query(). Nunca se debe concatenar
        variables directamente en SQL.




