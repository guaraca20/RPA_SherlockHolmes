*Nombre del proyecto:* UiPath_PlatformXSolutions
* Descripción del proceso:* El compañero digital ingresa a la biblioteca de www.guao.org a descargar un archivo PDF con la colección completa Sherlock Holmes. Al tener descargado el archivo y validar que exista, se realiza una serie de procedimientos realizados en el achivo PDF:
Obtener la cantidad de páginas del archivo.
Obtener el texto completo del archivo.
Obtener el listado de Novelas.
Separar por rangos de páginas las novelas encontradas por medio de expresiones regulares.
Separar los cuentos cortos y almacenarlos en un archivo a parte.

Se ingresa información relevante de los archivos PDFs separados a la base de datos del proceso.

Al terminar el procesamiento con el archivo PDF, se realiza la generación del reporte (archivo Excel) obteniendo los datos de la tabla de base de datos.

### REFrameWork Template ###
**Robotic Enterprise Framework**

### Detalles ###

1. **INITIALIZE PROCESS**
 + ./Framework/*InitiAllSettings* - Lee los datos de Configuración del archivo Config.xlsx
 + ./Framework/*InitiAllApplications* - Realiza la navegación y descarga del archivo PDF, y lo guarda en la carpeta "Data\Output\Descargas\"

2. **GET TRANSACTION DATA**
 + ./Framework/*GetTransactionData* - NO trabaja Queue, se ha comentado la actividad de Obtener item de la Queue, y se creó un DataTable temporal.

3. **PROCESS TRANSACTION**
 + *Process* - Realiza el procesamiento del archivo PDF descargado (Lee, obtiene paginas, separa archivos por lotes, se encuentra patrones en el PDF por medio de expresiones regular)
 + ./Framework/*SetTransactionStatus* - Updates the status of the processed transaction (Orchestrator transactions by default): Success, Business Rule Exception or System Exception

4. **END PROCESS**
 + ./Framework/*CloseAllApplications* - Realiza la generación del reporte por medio de una consulta SQL a la tabla de BD, obtiene los datos en un DataTable


### Dependencias ###
UiPath.Database.Activities=2.0.0
UiPath.Excel.Activities=3.1.1
UiPath.PDF.Activities=3.23.1-preview
UiPath.System.Activities=25.8.0
UiPath.Testing.Activities=25.4.0
UiPath.UIAutomation.Activities=25.10.8

### Aplicaciones necesarias ###
1. Navegador Chrome


### Base de Datos ###
Sql Server


### Desarrollador ###
Anderson Guaraca Iturriago
