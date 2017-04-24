
<a name="definitions"></a>
## Definiciones

<a name="actualizacion"></a>
### Actualizacion

|Nombre|Esquema|
|---|---|
|**leida**  <br>*opcional*|boolean|


<a name="comprobanteresponse"></a>
### ComprobanteResponse

|Nombre|Esquema|
|---|---|
|**fechaExpedicion**  <br>*obligatorio*|string|
|**folio**  <br>*opcional*|string|
|**moneda**  <br>*obligatorio*|string|
|**nombreEmisor**  <br>*opcional*|string|
|**nombreReceptor**  <br>*opcional*|string|
|**rfcEmisor**  <br>*obligatorio*|string|
|**rfcReceptor**  <br>*obligatorio*|string|
|**serie**  <br>*opcional*|string|
|**subTotal**  <br>*obligatorio*|number|
|**tipoDeComprobante**  <br>*obligatorio*|string|
|**total**  <br>*obligatorio*|number|
|**uuid**  <br>*obligatorio*|string|
|**version**  <br>*obligatorio*|string|


<a name="envio"></a>
### Envio

|Nombre|Esquema|
|---|---|
|**acEstatus**  <br>*opcional*|string|
|**acFecha**  <br>*opcional*|string|
|**acFolio**  <br>*opcional*|string|
|**acMotivo**  <br>*opcional*|string|
|**acNoRegistro**  <br>*opcional*|integer|
|**acNombreArchivo**  <br>*opcional*|string|
|**acPeriodo**  <br>*opcional*|string|
|**acTipoArch**  <br>*opcional*|string|
|**acTipoEnvio**  <br>*opcional*|string|


<a name="enviosresponse"></a>
### EnviosResponse

|Nombre|Esquema|
|---|---|
|**archivos**  <br>*obligatorio*|< [Envio](#envio) > array|
|**archivosPorPagina**  <br>*obligatorio*|integer|
|**pagina**  <br>*obligatorio*|integer|
|**totalDeArchivos**  <br>*obligatorio*|integer|


<a name="errorresponse"></a>
### ErrorResponse

|Nombre|Esquema|
|---|---|
|**code**  <br>*obligatorio*|integer|
|**message**  <br>*obligatorio*|string|


<a name="folioresponse"></a>
### FolioResponse

|Nombre|Esquema|
|---|---|
|**folio**  <br>*opcional*|string|


<a name="notificacion"></a>
### Notificacion

|Nombre|Esquema|
|---|---|
|**leida**  <br>*opcional*|string|
|**tipoNotificacion**  <br>*opcional*|string|


<a name="notificaciones"></a>
### Notificaciones

|Nombre|Esquema|
|---|---|
|**notificaciones**  <br>*obligatorio*|< [Notificacion](#notificacion) > array|
|**notificacionesPorPagina**  <br>*obligatorio*|integer|
|**pagina**  <br>*obligatorio*|integer|
|**totalNotificaciones**  <br>*obligatorio*|integer|


<a name="rfcvalidationresponse"></a>
### RfcValidationResponse

|Nombre|Esquema|
|---|---|
|**esValido**  <br>*obligatorio*|boolean|
|**motivo**  <br>*obligatorio*|string|
|**rfc**  <br>*obligatorio*|string|



