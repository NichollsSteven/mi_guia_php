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
