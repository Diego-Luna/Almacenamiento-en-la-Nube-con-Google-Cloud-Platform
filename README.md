# Almacenamiento-en-la-Nube-con-Google-Cloud-Platform

## gsutil

Se sugiere ponerle al Bucket que este asociado con el proyecto, para que sea fácil de ubicar. El nombre del Bucket debe ser único.

Crear un Bucket (make Bucket)

```
gsutil mb gs://mi-proyecto-bucket-01
```

Ver mis Buckets

```
gsutil ls
```

Ver los objetos en un Bucket

```
gsutil ls gs://mi-proyecto-bucket-01
```

Copiar objetos a un Bucket

```
gsutil cp ./archivo.txt gs://mi-proyecto-bucket-01
```

Copiar objetos de un Bucket a otro lado

```
gsutil cp gs://mi-proyecto-bucket-01/archivo.txt .
```

Activar el versionamiento en los objetos de un Bucket

```
gsutil versioning set on gs://mi-proyecto-bucket-01
```

Desactivar el versionamiento en los objetos de un Bucket

```
gsutil versioning set off gs://mi-proyecto-bucket-01
```
