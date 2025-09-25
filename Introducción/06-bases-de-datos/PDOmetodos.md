# Métodos PDO más importantes para consultas SQL.
## 📘 Métodos PDO: Consulta, Ejecución y Recuperación de Datos
### 1. ⚙️ Métodos de Consulta
    *PDO::query($sql)
    ** Función : Ejecuta directamente una consulta SQL y devuelve un objeto .PDOStatement
    ** Uso típico : Para consultas simples que devuelven resultados (SELECT).
    ** Ejemplo: $stmt = $pdo->query("SELECT * FROM usuarios");
