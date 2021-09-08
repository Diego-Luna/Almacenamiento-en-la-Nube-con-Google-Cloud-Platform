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

**Donde**:
`-c` es la clase
`-l` es el tipo de locación que deseamos
`--pap` especifica el acceso público
`-b `es activar el acceso uniforme
**Avanzado**:
`--retention `es el periodo de retención del recurso.

### Crear tu primer bucket:

- Seleccionar del menú tipo hamburguesa la opción Cloud Storage.
- Darle clic a “Create Bucket”.
- Darle un nombre único al “bucket” (puedes usar como prefijo el nombre del proyecto) y Continuar.
- Seleccionar donde se almacenará (Multi-Región, Región Dual o Región) y Continuar.
- Seleccionar la clase de almacenamiento (Standard, Nearline, Coldline, Archive) y Continuar.
- Seleccionar control de acceso (Uniform, Fine-grained) y Continuar.
- Escoger la Configuración Avanzada que necesites (Encriptación, política de retención,etc.).
- Darle clic al botón CREATE.

## Google Cloud Bigtable

Cloud Bigtable es el servicio de base de datos de Big Data NoSQL de Google, completamente administrado a escala de patabytes para casos de uso en los que el acceso de datos aleatorios de baja latencia, la escalabilidad y la confiabilidad son fundamentales

**Características**

- Alto procesamiento
- Procesamiento de baja latencia
- Cantidades muy grandes de datos
- Cambios de tamaño sin tiempo de inactividad
- Replicación flexible y automatizada
- Google Search, Maps y otros productos de Google

**¿Cómo interactuamos con Cloud Big Table?**

- Api de aplicación: Podemos leer y escribir datos atraves de una capa de servicio llamada rede Hbase, que es un gestor de codigo abierto que nos ayuda exponer el point que nos proveen estas operaciones de escribir leer actualizar y borrar y esto se usa normalmente para enviar datos a las aplicaciones o paneles de control
- Streaming / Transmisión: Datflow Streaming, Saprk Streaming y Apache Storm
- Batch Processing / Procesamiento por lotes: Los datos se pueden leer y escribir en Big Table en forma de batch (cantidades grandes) esto se puede hacer a través de hadoop, Datflow, Apache Spark.

## Cloud SQL

Este es el servicio administrado de Bases de Datos Relacionales. Puede ser MySQL, PosgreSQL y SLQ Server.

En caso de necesitar mayor rendimiento se puede escalar de forma vertical (un máquina más potente).
Si se requiere más disponibilidad se puede optar por una arquitectura en dos zonas.

**Características claves**

- Totalmente administrada
- Una solución integrada: Se puede acceder a ellas desde cualquier lado.
- Confiable: ES fácil configurar las replicas, copias de seguridad y activar el proceso de Failover (reemplazar una instancia cuando esta falla).
- Migraciones sencillas a CloudSQL: Database Migration Service ayuda a migrar las DB on premise a la Nube facilmente.

En este tipo de Bases de datos realizamos transacciones y deben cumplir los principios ACID.

- Atomicity: Asegura que todas las operaciones que una transaccion se realicen, y en caso contrario que sea posible regresar al estado anterior (rollback).

- Consistency: Asegura que todas las transacciones se realicen con exito, los datos deben tener sentido.

- Isolation: Dicta que las operaciones sean aisladas y transparentes, es decir, multiples operaciones ocurren de forma independiente y sin afectarse.

- Durabilty: Nos asegura que el resultado de una operación permanezca incluso cuando hubo un error.

## Cloud Spanner

Base de datos de nivel empresarial, distribuido fuertemente consistente y de forma global, estructura relacional a escala horizontal no relacional.

Cloud Spanner Características Clave.
* Base de datos relacional diseñada para cualquier escala
* Disponibilidad cinco 9 (99,999%)
* Fragmentación automática.
