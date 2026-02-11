
# repaso de mongo

- creacion de base de datos 
```json 
use (nombre de la base de datos)
```
- creacion de colleciones 
```json 
db.createColletion("")
```

- consulta para insercion en coleccion 

```json 
bdidgsgq> db.alumnos.insertOne(
... {
... matricula:1,
... nombre:'juan',
... promedio:8.5,
... carrera:'ti'})
{
  acknowledged: true,
  insertedId: ObjectId('698bc4d9e6a013b8ca628ca0')
}
``` 
- mongodump se utilisa para copia de seguridad
```json   
mongodump --db bdidgsgq --out c:/backups
```
-copia de collecion 
```jsonn
mongodump --db bdidgsgq --collection alumnos c:/backups/Coleciones
```
y para restaurar
```json 
mongorestore --db bdidgsgq c:/backups/bdidgsgq
```
- comando para restaurar una base de datos con una sola colleccion 
```json 
mongorestore --db backupidgs --collection alumnos c:/backups/bdidgsgq/alumnos.bs
```
- comando para exportar datos de mongo en formato json
```json 
mongoexport --db bdidgsgq --collection alumnos --type=json --out c:/backups/colleciones/copia1.json
```
- exportar datos en datos en formato csv 
```json 
mongoexport --db backupidgs --collection alumnos --type=csv --fields matricula, nombre,carrera --out c:/backups/colleciones/copia2.csv
```

