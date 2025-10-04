# 📘 Comandos DDL (Data Definition Language):

## 🔍 ¿Qué son los comandos DDL?
    Son un conjunto de instrucciones SQL utilizadas
    para definir y modificar la estructura de la base de datos y sus objetos,     como tablas,índices y esquemas.

### 🛠️ Principales comandos DDL

#### CREATE Se utiliza para crear nuevos objetos en
la base de datos: bases de datos, tablas, índices, etc.

    Ejemplo - 1: Crear una base de datos
    
    DROP DATABASE IF EXISTS Producción;
    /*Elimina la base de datos 'Producción' si existe*/
      
    CREATE DATABASE Producción CHARACTER SET utf8mb4;
    /*Crea la base de datos 'Producción' con codificación utf8mb4*/
    
    USE Producción
    /*Prepara la base de datos para ser usada */

      Ejemplo - 2: Crear una tabla
      CREATE TABLE Nombre_Tabla (
      Nombre_campo TipoDato(Longitud) Restricción,
      Nombre_campo TipoDato(Longitud) ...);

#### 2. ALTER Permite modificar la estructura de una base de datos, tablas o índices existentes.

    Ejemplo - 1 Agregar columna:
    ALTER TABLE Nombre_Tabla ADD "Nombre_columna" Tipo_Dato;

    Ejemplo - 2 Eliminar columna:
    ALTER TABLE Nombre_Tabla DROP COLUMN Nombre_columna;

    Ejemplo - 3 Modificar tipo de dato de una columna:
    ALTER TABLE Nombre_Tabla MODIFY COLUMN Nombre_columna Nuevo_Tipo_Dato;
    
    Ejemplo - 4 Renombrar columna:
    ALTER TABLE Nombre_Tabla CHANGE Nombre_columna Nuevo_Nombre Tipo_Dato;

    Ejemplo - 5 Convertir campo en clave foránea: 
    ALTER TABLE Nombre_Tabla ADD CONSTRAINT "Nombre_foranea"
    FOREIGN KEY  (Nombre_campo) REFERENCES Nombre_Tabla                        (Campo_Primary_Key);

    Ejemplo - 6 Convertir campo en clave primaria:
    ALTER TABLE Nombre_Tabla ADD PRIMARY KEY (Nombre_campo);


#### 3. DROP Se emplea para eliminar de forma permanente bases de datos, tablas o índices.

    Ejemplo - 1 Eliminar Tabla:
    DROP TABLE Nombre_Tabla;
    Elimina completamente la tabla y sus datos

#### 4. TRUNCATE Elimina todos los registros de una tabla, sin alterar su estructura.

    TRUNCATE TABLE Nombre_Tabla;
    Elimina todos los registros de una tabla, sin alterar su estructura.
    

### 🧱 Creación de Tablas: Restricciones y Claves
#### 🔒 Restricciones al definir campos

    Ejemplo - 1 NOT NULL: En dicho campo no se aceptan valores nulos.
    Nombre_campo TipoDato NOT NULL

    Ejemplo - 2 UNIQUE: Asegura que todos los valores en la columna
    sean únicos (puede ser nulo, pero solo una vez si no es NOT NULL).
    Nombre_campo TipoDato UNIQUE
    Ejemplo: email VARCHAR(100) UNIQUE

    Ejemplo - 3.1 CHECK con lista de valores: Solo se aceptan los valores      predefinidos. 
    CHECK (Nombre_campo IN ('Valor1', 'Valor2', 'Valor3'))

    Ejemplo - 3.2 CHECK con rango numérico: Solo se aceptan valores
    dentro del rango especificado. 
    CHECK (Nombre_campo BETWEEN 1 AND 3)

    Ejemplo - 3.3 CHECK con comparación: lo se aceptan valores
    menores o  mayores a un número específico. 
    CHECK (Nombre_campo < 50)

    Ejemplo - 4 DEFAULT: Define un valor por defecto si no se
    proporciona uno al insertar.
    Nombre_campo TipoDato DEFAULT 'valor_predeterminado'
    Ejemplo: estado VARCHAR(20) DEFAULT 'activo'

    Ejemplo - 5 PRIMARY KEY: Clave primaria → identificador único
    de cada registro. Puede ser simple o compuesta.
    Nombre_campo TipoDato PRIMARY KEY 
    O bien, al final de la tabla:
    PRIMARY KEY (Nombre_campo)

    Ejemplo - 6 FOREIGN KEY:Clave foránea → referencia a
    una clave primaria en otra tabla.
    Nombre_campo TipoDato,FOREIGN KEY (Nombre_campo)
    REFERENCES Nombre_Tabla (Campo_Primary_Key)
    Con nombre explícito:
    CONSTRAINT fk_nombre FOREIGN KEY (Nombre_campo) 
    REFERENCES Nombre_Tabla (Campo_Primary_Key)

#### 🔑 Formas de definir una clave primaria
    (Ya cubiertas: declaración explícita, por referencia, única + PK,         auto incremento)

#### 🔗 Formas de definir una clave foránea
    (Ya cubiertas: con nombres explícitos y implícitos)
    
    
    
    
    


      
    
    
