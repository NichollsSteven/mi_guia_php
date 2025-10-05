# 📘 Comandos DML (Data Manipulation Language)
## Resumen de los parametros Principales 
* SELECT
* INSERT
* UPDATE
* DELETE
* CASE
* WHERE
* ORDER BY
* LIMIT
* ALIAS
* JOIN.

## 🔍 ¿Qué son los comandos DML?
    Son un conjunto de instrucciones SQL utilizadas para manipular y gestionar
    los datos dentro de la base de datos.No modifican la estructura de las tablas,
    sino su contenido: insertar, actualizar, eliminar o recuperar registros.

## 🛠️ Principales comandos DML

### 1. SELECT
    > Se utiliza para recuperar datos de una o más tablas. Permite especificar
    qué columnas y filas se desean obtener.

#### ✅ Sintaxis básica:
    SELECT [columnas] FROM Nombre_Tabla [WHERE condición] [ORDER BY columna (ASC|DESC)] [LIMIT número];

#### ➤ SELECT: Especifica las columnas que se desean recuperar.  
    Puedes usar para seleccionar todas las columnas.
    SELECT  FROM empleados;

#### ➤ FROM: Indica la tabla de la cual se extraerán los datos.
     FROM empleados;


#### ➤ WHERE (opcional): Filtra los registros que cumplen con una condición específica.
    WHERE salario > 50000;

#### ➤ ORDER BY (opcional): Ordena los resultados en base a una o más columnas,en orden ascendente (ASC) o descendente (DESC).
    ORDER BY nombre ASC;


#### ➤ LIMIT (opcional): Limita el número de registros devueltos por la consulta.
    LIMIT 10;

### 2. INSERT > Permite agregar nuevos registros o filas a una tabla existente.

#### ✅ Sintaxis básica:
    (sql) INSERT INTO Nombre_Tabla (columna1, columna2, columna3) VALUES ('valor1', 'valor2', 'valor3');

#### ➤ Insertar múltiples registros:
    (sql) INSERT INTO Nombre_Tabla (columna1, columna2, columna3) 
    VALUES ('valor1', 'valor2', 'valor3'),
    ('valor4', 'valor5', 'valor6'),
    ('valor7', 'valor8', 'valor9');

### 3. UPDATE > Se utiliza para modificar datos existentes en una tabla. Permite actualizar uno o más registros.

#### ✅ Sintaxis básica:
    (sql) UPDATE Nombre_Tabla  SET columna1 = valor1, columna2 = valor2 WHERE condición;


#### ➤ Actualizar múltiples columnas de un solo registro:
    (sql) UPDATE empleados  SET puesto = 'Senior Developer', salario = 60000 WHERE nombre = 'Juan Perez';


#### ➤ Actualizar múltiples columnas de varios registros con CASE:
    (sql) UPDATE empleados SET salario = CASE 
            WHEN nombre = 'Ana Gomez' THEN 55000 
            WHEN nombre = 'Luis Martinez' THEN 70000 
            ELSE salario 
        END,
        puesto = CASE 
            WHEN nombre = 'Ana Gomez' THEN 'Lead Diseñadora' 
            WHEN nombre = 'Luis Martinez' THEN 'Director' 
            ELSE puesto 
        END 
    WHERE nombre IN ('Ana Gomez', 'Luis Martinez');


#### ➤ Sintaxis general de la cláusula CASE:
    (sql) CASE WHEN condicion1 
    THEN nuevo_valor1 WHEN condicion2
    THEN nuevo_valor2 ELSE valor_por_defecto
    END


#### ➤ Ejemplo práctico con CASE:
    (sql) UPDATE cuentas SET saldo = CASE WHEN saldo <= 1000 THEN saldo  1.05 ELSE saldo END;
    > Esto aplica un aumento del 5% solo a saldos menores o iguales a 1000.



### 4. DELETE > Se utiliza para borrar filas o registros específicos en una tabla.

#### ✅ Sintaxis básica:
    (sql) DELETE FROM Nombre_Tabla WHERE condición;


#### ➤ DELETE FROM: Indica que se van a eliminar registros de la tabla especificada.  
    nombre_tabla: es el nombre de la tabla de la cual se desea eliminar registros.

#### ➤ WHERE condición: Especifica qué registros deben ser eliminados.  
    Si no se incluye WHERE, se eliminarán todos los registros de la tabla.

#### ➤ Eliminar un registro específico:
    (sql) DELETE FROM empleados WHERE nombre = 'Juan';

#### ➤ Eliminar múltiples registros:
    (sql) DELETE FROM empleados WHERE salario < 1000;


#### ➤ Eliminar registros basados en múltiples condiciones:
    (sql) DELETE FROM empleados WHERE puesto = 'INTERNO' AND salario < 20000;


#### ➤ Eliminar registros basados en fechas:
    (sql) DELETE FROM empleados WHERE fecha_contratacion < '20200101';


#### ➤ Eliminar empleados dentro de un rango de salario:
    (sql) DELETE FROM empleados WHERE salario BETWEEN 30000 AND 50000;


#### ➤ Eliminar todos los registros de una tabla:
    (sql) DELETE FROM Nombre_Tabla;
    > ⚠️ ¡Cuidado! Sin WHERE, se borran todos los datos de la tabla (pero la estructura permanece).

## 🧩 Cláusulas clave en DML

### ▶ CASE > Se utiliza para especificar diferentes valores según condiciones.
    (sql)CASE WHEN condicion1 THEN valor1 WHEN condicion2 THEN valor2 ELSE valor_default END

### ▶ WHERE > Se utiliza para limitar la actualización o eliminación solo a los registros que cumplen con las condiciones especificadas.


## 📌 Alias en consultas SQL
### ❓ ¿Qué son los alias?
    Un alias es un nombre temporal que se puede dar a una tabla o a una columna en una consulta SQL.  
    Se utiliza para hacer que las consultas sean más legibles y cortas, especialmente cuando se trabaja con nombres largos o      cuando se realizan uniones que involucran varias tablas.



### ➤ Asignar alias a tablas:
    Se pueden asignar alias a una tabla en el FROM o en el JOIN,
    usando la palabra clave AS (aunque en muchos casos se puede omitir).

#### ✅ Sintaxis:
    SELECT columna1, columna2 FROM Nombre_Tabla AS alias_de_la_tabla;
     O simplemente:
    SELECT columna1, columna2 
    FROM Nombre_Tabla alias_de_la_tabla;


#### ✅ Ejemplo:
    (sql) SELECT c.Nombre FROM clientes AS c;
     O sin AS:
    SELECT c.Nombre FROM clientes c;

### ➤ Asignar alias a columnas:
    Se puede asignar un alias a una columna en el SELECT
    para que el resultado tenga un nombre más amigable.

#### ✅ Sintaxis:
    (sql) SELECT columna AS alias_columna FROM Nombre_Tabla;


#### ✅ Ejemplo:
    (sql) SELECT nombre AS nombre_cliente FROM clientes;

### 🎯 Ejemplo completo usando alias:
    Imaginemos que tenemos las tablas empleados y departamentos,
    y queremos obtener una lista de empleados junto con el nombre
    de su departamento. Aquí se usan alias para simplificar la consulta.
    
    SELECT e.Nombre AS empleado, d.Nombre_departamento AS departamento
    FROM empleados AS e JOIN departamentos AS d ON e.id_departamento = d.id_departamento;

## 🔗 Unir Estudiantes y Cursos (JOIN)
    ### Tablas:
     estudiantes: id_estudiantes, nombre
     inscripciones: id_estudiante, id_curso
     cursos: id_curso, nombre_curso

    ### Consulta con JOIN:
    SELECT e.nombre AS estudiantes, c.nombre_curso FROM estudiantes e 
    JOIN inscripciones i ON e.id_estudiantes = i.id_estudiante 
    JOIN cursos c ON i.id_curso = c.id_curso;

    > Esta consulta devuelve el nombre del estudiante y el nombre del curso al que está inscrito.


### ✅ Consejos finales:
     Usa WHERE siempre que quieras filtrar datos, especialmente en UPDATE y DELETE.
     Usa LIMIT en SELECT para evitar sobrecargar la memoria con grandes conjuntos de datos.
     Usa CASE para lógica condicional dentro de consultas.
     Usa alias (AS) para mejorar la legibilidad, especialmente en consultas con múltiples tablas.
     ¡Nunca uses DELETE sin WHERE a menos que realmente quieras borrar toda la tabla!



¿Quieres que te genere un archivo .pdf, .md o incluso un script PHP que ejecute estos comandos usando PDO? ¡Solo dime cómo lo necesitas!
