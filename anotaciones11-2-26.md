```markdown
# Apuntes de MongoDB: Comandos de Respaldo y Migración

Comandos vistos en clase para realizar respaldos, restauraciones, importaciones y exportaciones de datos en MongoDB desde la consola de Windows (CMD).

---

## 1. Respaldo y Restauración (Formato Binario/BSON)

Estos comandos se utilizan para generar copias de seguridad completas y exactas de la base de datos.

### Generar Respaldo (Dump)
Crea una copia de la base de datos `bdidgsg1` en la carpeta especificada.
```cmd
mongodump --db bdidgsg1 --out c:/backups

```

### Restaurar Respaldo (Restore)

Restaura la colección `alumnos` desde el archivo `.bson` generado previamente hacia una nueva base de datos llamada `backupidgs`.

```cmd
mongorestore --db backupidgs --collection alumnos c:/backups/bdidgsg1/alumnos.bson

```

---

## 2. Exportación de Datos (Texto Plano)

Estos comandos extraen los datos en formatos legibles (JSON o CSV) para usarlos en otras aplicaciones.

### Exportar a JSON

Exporta todos los documentos de la colección `alumnos` a un archivo JSON.

```cmd
mongoexport --db backupidgs --collection alumnos --type=json --out c:/backups/COLECCIONES/copia1.json

```

### Exportar a CSV (Excel)

Exporta campos específicos (`matricula`, `nombre`, `carrera`) a un archivo CSV.
*Nota: Es obligatorio especificar los `--fields` cuando se usa csv.*

```cmd
mongoexport --db backupidgs --collection alumnos --type=csv --fields matricula,nombre,carrera --out c:/backups/COLECCIONES/copia2.csv

```

---

## 3. Importación de Datos (Texto Plano)

Estos comandos permiten cargar datos desde archivos externos hacia MongoDB.

### Importar desde CSV

Carga los datos del archivo CSV a una base de datos nueva llamada `copiaidgs`.
*Nota: Se usa `--headerline` para indicar que la primera fila del archivo contiene los nombres de los campos.*

```cmd
mongoimport --db copiaidgs --collection alumnos --type=csv --headerline --file c:/backups/COLECCIONES/copia2.csv

```

### Importar desde JSON

Carga los datos del archivo JSON a una base de datos llamada `bdcopia`.

```cmd
mongoimport --db bdcopia --collection alumnos --type=json --file c:/backups/COLECCIONES/copia1.json

```

---

## 4. Exportación con Filtros (Query)

Exporta solo los documentos que cumplen una condición específica.

### Exportar con Query en Windows

Exporta los alumnos donde el campo `carrera` es igual a `"dn"`.
*⚠️ Importante: En Windows CMD, se deben usar comillas dobles `"` para envolver el query y escapar las comillas internas con barra invertida `\`.*

```cmd
mongoexport --db backupidgs --collection alumnos --query "{\"carrera\":\"dn\"}" --out c:/backups/COLECCIONES/copia3.json

```

```

```