# MT940 Unitec y UVM para BBVA
## _Resumen_

Este programa es para el parseo y generacion del documento simplificado de las MT940 que se generan por parte de BBVA para UNITEC y UVM.

## Features

El repositorio de procesamiento de MT940 es MT940Engine y consiste en los siguientes procesos:

- MT940TimerStarter- Timer que inicializa el proceso de lectura de archivos MT940
- ProcessingMT940 - Proceso que parcea cada uno de los archivos y en base a las reglas establecidas genera el archivo simplificado
- SaveInfoInDBBatch - Este proceso se encarga de insertar la informacion del archivo simplificado en la BD tabla temporal para los reportes.
 

## Installation


```sh
TBD
```

For production environments...

```sh
TBD
```

## Configuracion
 
Variables Globales para configurar:

| Variable | Value | Descripcion|
| ------ | ------ | ------ |
|/CorrespBan|||
|CLAVECONCILIA  |072|
|CLAVECORRESP  |072|
|DESCCONCILIA  |Correspnsales Conciliacion|
|DESCCORRESP  |Correspnsales Banorte|
|LocalErrorPath  |/u01/tibco/interfaces/315/bancos/072/error|
|LocalFilePath  |/u01/tibco/interfaces/315/bancos/072|
|LocalProcecedPath  |/u01/tibco/interfaces/315/bancos/072/procesado|
|StatusError  |E|
|StatusInProcess  |P|
|StatusTerminated  |T|
|/CorrespBan/CORRESP_sFTP
|FilePattern  |SM418573ECR*.RES|
|Password  |****|
|Port  |22|
|RemotePathFiles  |/recibido_banorte|
|RemoteProcecedPath  |/ProcesadosTibco|
|Timeout_milseg  |900000|
|URL  |localhost|
|Usuario  |sftpbanorte|
|[/ProjConfig]
|ErrorOut  |/u01/MT940/MT940Error/|
|bankClave  |012MT|
|bankCve  |012|
|copySFTP  |N|
|dateFormat  |yyyyMMdd|
|filePattern  |SALI*.txt|
|inputDir  |/u01/MT940/input/|
|interval  |300|
|outputDir  |/u01/MT940/output/|
|outputDirFinal  |/u01/MT940/outputFinal/|
|queueToStart  |laureate.mt940.start|
|withExpenses  |true|
|/ProjConfig/Accounts
|UAVer  |0186124836|
|UNITEC  |0178632383|
|UVM  |0136732747|
|/ProjConfig/C86Config||Posiciones para obtener los datos de C86
|field1End  |3|
|field1Start  |0|
|field2End  |22|
|field2Start  |2|
|/ProjConfig/DBConnectionUNITEC
|URL  |jdbc:tibcosoftwareinc:oracle://**********|
|password  |****|
|timeout  |350|
|user  |SATURN|
|/ProjConfig/DBConnectionUVM
|URL  |jdbc:tibcosoftwareinc:oracle://**********|
|pass  |****|
|timeout  |350|
|user  |SATURN|
|/ProjConfig/Labels||Labels configurables para archivo simplificado
|debitCreditMark  |C|
|egreso  |EGRESO|
|pagoAlumNoRef  |PAGO ALUMNO NO REF|
|pagoAlumRef  |PAGO ALUMNO REF|
|/ProjConfig/OutputDir
|UAVer  |/u01/tibco/interfaces/002/bancos/|archivos simplificados para Ver hacia banner
|UNITEC  |/u01/tibco/interfaces/315/bancos/|archivos simplificados para UNITEC hacia banner
|UVM  |/u01/tibco/interfaces/001/bancos/||archivos simplificados para UVM hacia banner

## Development

#### Ejecucion Local

Para su ejecucion local es necesario tener preexistente la carpeta:

```sh
C:\u01\MT940
```

Tambien es necesaria la libreria de [SWIFT]:

```sh
pw-swift-core-SRU2023-10.1.12.jar
```

Para procesar un archivo este debe ponerse en  la carpeta:
```sh
C:\u01\MT940\input
 ```
 
 Iniciar el proceso ProcessingMT940 y esto generara dos archivos uno para la carpeta del proceso hacia Banner 
 
  ```sh
  --OutputDir
  --UAVer 
  "/u01/tibco/interfaces/002/bancos/"
  --UNITEC
  "/u01/tibco/interfaces/315/bancos/"
  --UVM 
  "/u01/tibco/interfaces/001/bancos/"
 ```
 
 y otro para el proceso de cargar la informacion en la BD para reportes.
 
 ```sh
 --Variable outputDir
C:\u01\MT940\output
 ```
 
   [SWIFT]: <https://mvnrepository.com/artifact/com.prowidesoftware/pw-swift-core> 
