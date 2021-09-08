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

## Breve Resumen: Clases de almacenamiento de Cloud Storage

Al crear un Bucket debemos definir la ubicación y clase.

### Ubicación

Define donde residirán nuestros datos.

### Tipos de ubicación

- Regional: Los datos se replican en las zonas de una sola región. Para datos a los que se accede con frecuencia dentro una región.
- Dual-regional: Los datos se replican en regiones cercanas. Para disponibilidad de datos accedidos frecuentemente en un área específica.
- Multi-regional: Los datos se replican en diferentes regiones (continentes). Para la más alta disponibilidad de datos frecuentemente accedidos.

### Clases

Se refieren a la frecuencia con la que accedemos y disponibilidad que deseamos sobre los objetos dentro del bucket. Además del precio.

- Standars: Objetos a los que accedemos frecuentemente (más caro).
- Nearline: Acceso a los objetos una vez al mes.
- Coldline: Acceso a los objetos una vez al trimestre.
- Archive: Acceso a los objetos una vez al año.

### Clases vs. ubicación

Podemos combinar las clases con diferentes ubicaciones, de acuerdo a nuestras necesidades.

## Clases de almacenamiento en acción

Creamos un Bucket Standar Multi-region en US. Se previo el acceso al público y se eligió el acceso uniforme. Finalmente seleccionamos una retención de 10 años. Esto en gsutil se vería así:

```
gsutil mb -c standard -l us --pap enforced -b on --retention 10y gs://gemb-platzi-storage-bucket-01
```

__Donde__:
```-c``` es la clase
```-l``` es el tipo de locación que deseamos
```--pap``` especifica el acceso público
```-b ```es activar el acceso uniforme
__Avanzado__:
```--retention ```es el periodo de retención del recurso.

### Crear tu primer bucket:

* Seleccionar del menú tipo hamburguesa la opción Cloud Storage.
* Darle clic a “Create Bucket”.
* Darle un nombre único al “bucket” (puedes usar como prefijo el nombre del proyecto) y Continuar.
* Seleccionar donde se almacenará (Multi-Región, Región Dual o Región) y Continuar.
* Seleccionar la clase de almacenamiento (Standard, Nearline, Coldline, Archive) y Continuar.
* Seleccionar control de acceso (Uniform, Fine-grained) y Continuar.
* Escoger la Configuración Avanzada que necesites (Encriptación, política de retención,etc.).
* Darle clic al botón CREATE.