# Splunk Simple Architecture

Arquitectura simple de Splunk.

## Partes de la arquitectura

+ Splunk Enterprise, modo standalone
+ Splunk Universal Forwarder

Ambas partes ya están conectadas y pre-configuradas para:

+ Indexar datos por parte de la instancia de Splunk Enterprise.
+ Enviar datos al indexador por parte del Splunk Universal Forwarder.
+ Conectarse al master por parte del Splunk Universal Forwarder.

## Levantar la arquitectura

Nos situamos en la raíz del proyecto y ejecutamos el siguiente comando:

``` bash
docker-compose up
```

## Acceder a Splunk Enterprise

Nos dirigimos a la url <http://127.0.0.1:8000>. Introducimos las credenciales:

+ Usuario: admin
+ Contraseña: admin1234

## Notas

+ Recurso para generar los comandos de Docker: <https://docker-commands-generator.vercel.app/>
