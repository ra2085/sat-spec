
<a name="paths"></a>
## Recursos

<a name="buzon-tributario_resource"></a>
### Buzón Tributario

<a name="buzon-tributario-rfc-bandeja-get"></a>
#### GET /buzon-tributario/{rfc}/bandeja

##### Descripción
Listar notificaciones


##### Parámetros

|Tipo|Nombre|Descripción|Esquema|
|---|---|---|---|
|**Path**|**rfc**  <br>*obligatorio*|RFC del contribuyente|string|


##### Respuestas

|Código HTTP|Descripción|Esquema|
|---|---|---|
|**200**|Listado de notificaciones|[Notificaciones](#notificaciones)|
|**404**|RFC no encontrado|Sin contenido|


##### Produce

* `application/json`


<a name="buzon-tributario-rfc-bandeja-idnotificacion-put"></a>
#### PUT /buzon-tributario/{rfc}/bandeja/{idNotificacion}

##### Descripción
Actualizar notificación


##### Parámetros

|Tipo|Nombre|Descripción|Esquema|
|---|---|---|---|
|**Path**|**idNotificacion**  <br>*obligatorio*|Notificación a actualizar|string|
|**Path**|**rfc**  <br>*obligatorio*|RFC del contribuyente|string|
|**Body**|**body**  <br>*obligatorio*||[Actualizacion](#actualizacion)|


##### Respuestas

|Código HTTP|Descripción|Esquema|
|---|---|---|
|**200**|Notificación actualizada|Sin contenido|
|**400**|Error de actualización|[ErrorResponse](#errorresponse)|


##### Consume

* `application/json`


##### Produce

* `application/json`


<a name="contabilidad-electronica_resource"></a>
### Contabilidad Electrónica

<a name="contabilidad-electronica-rfc-acuses-folio-get"></a>
#### GET /contabilidad-electronica/{rfc}/acuses/{folio}

##### Descripción
Descargar Acuse


##### Parámetros

|Tipo|Nombre|Descripción|Esquema|
|---|---|---|---|
|**Path**|**folio**  <br>*obligatorio*|Folio del acuse a descargar|string|
|**Path**|**rfc**  <br>*obligatorio*|RFC del contribuyente|string|
|**Query**|**acuseTipo**  <br>*obligatorio*|Tipo de Acuse|< enum (Recibido, Estatus) > array|


##### Respuestas

|Código HTTP|Descripción|Esquema|
|---|---|---|
|**200**|Descarga de Archivo de Acuse|file|
|**404**|Acuse no encontrado|Sin contenido|


##### Produce

* `application/octet-stream`


<a name="contabilidad-electronica-rfc-envios-post"></a>
#### POST /contabilidad-electronica/{rfc}/envios

##### Descripción
Envíar archivo


##### Parámetros

|Tipo|Nombre|Descripción|Esquema|
|---|---|---|---|
|**Path**|**rfc**  <br>*obligatorio*|RFC del contribuyente|string|
|**FormData**|**Archivo**  <br>*obligatorio*|Archivo a envíar|file|


##### Respuestas

|Código HTTP|Descripción|Esquema|
|---|---|---|
|**200**|Folio del acuse de recibido|[FolioResponse](#folioresponse)|
|**400**|Error de envío|[ErrorResponse](#errorresponse)|


##### Consume

* `multipart/form-data`


##### Produce

* `application/json`


<a name="consultar-envios"></a>
#### GET /contabilidad-electronica/{rfc}/envios

##### Descripción
Consultar Envíos


##### Parámetros

|Tipo|Nombre|Descripción|Esquema|
|---|---|---|---|
|**Path**|**rfc**  <br>*obligatorio*|RFC del contribuyente|string|
|**Query**|**anio**  <br>*obligatorio*|Periodo Fiscal|integer|
|**Query**|**archivoTipo**  <br>*obligatorio*|Tipo de Archivo|< enum (CT, B, PL, XF, XC) > array|
|**Query**|**desde**  <br>*opcional*|Número de archivos a omitir|integer|
|**Query**|**estatus**  <br>*obligatorio*|Estatus|< enum (Recibido, Aceptado, Rechazado) > array|
|**Query**|**hasta**  <br>*opcional*|Número de archivos a recuperar|integer|
|**Query**|**mesDesde**  <br>*obligatorio*|Mes inicial|integer|
|**Query**|**mesFin**  <br>*obligatorio*|Mes fin|integer|


##### Respuestas

|Código HTTP|Descripción|Esquema|
|---|---|---|
|**200**|Listado de envíos|[EnviosResponse](#enviosresponse)|
|**400**|Error de busqueda|[ErrorResponse](#errorresponse)|


##### Produce

* `application/json`


<a name="contabilidad-electronica-rfc-xmls-folio-get"></a>
#### GET /contabilidad-electronica/{rfc}/xmls/{folio}

##### Descripción
Descargar xml


##### Parámetros

|Tipo|Nombre|Descripción|Esquema|
|---|---|---|---|
|**Path**|**folio**  <br>*obligatorio*|Folio del Acuse perteneciente al XML|string|
|**Path**|**rfc**  <br>*obligatorio*|RFC del contribuyente|string|


##### Respuestas

|Código HTTP|Descripción|Esquema|
|---|---|---|
|**200**|Archivo de XML enviado|file|
|**404**|XML no encontrado|Sin contenido|


##### Produce

* `application/xml`


<a name="operaciones-con-cfdi_resource"></a>
### Operaciones Con CFDI

<a name="comprobantes-get"></a>
#### Obtener listado de comprobantes de un emisor.
```
GET /comprobantes
```


##### Descripción
Obtener un listado paginado de comprobantes que le hayan emitido y haya emitido un contribuyente activo.


##### Parámetros

|Tipo|Nombre|Descripción|Esquema|Valor por defecto|
|---|---|---|---|---|
|**Query**|**estado**  <br>*opcional*|filtro estado del comprobante.|enum (vigente, cancelado)||
|**Query**|**fechaEmisionFinal**  <br>*opcional*|rango final de búsqueda sobre fecha de emisión de CFDIs|string (date-time)||
|**Query**|**fechaEmisionInicial**  <br>*opcional*|rango inicial de búsqueda sobre fecha de emisión de CFDIs|string (date-time)||
|**Query**|**folio**  <br>*opcional*|filtro de comprobantes por folio de control interno del contribuyente|string||
|**Query**|**formaPago**  <br>*opcional*|filtro de comprobantes por la clave de la forma de pago de los bienes o servicios amparados por CFDI|string||
|**Query**|**limit**  <br>*opcional*|límite de resultados por página|integer|`20`|
|**Query**|**lugarExpedicion**  <br>*opcional*|filtro de comprobantes por el código postal del lugar de expedición del CFDI|string||
|**Query**|**metodoPago**  <br>*opcional*|filtro de comprobantes por clave del método de pago que aplica para CFDI|enum (PUE, PID, PPD)||
|**Query**|**moneda**  <br>*opcional*|filtro de comprobantes por clave de la moneda utilizada para expresar los montos en CFDI|string||
|**Query**|**noCertificado**  <br>*opcional*|filtro de comprobantes por el número de serie del certificado de sello digital que ampara a CFDI|string||
|**Query**|**offset**  <br>*opcional*|cursor de resultados por página|integer|`0`|
|**Query**|**rfcEmisor**  <br>*opcional*|filtro de comprobantes por RFC del Emisor|string||
|**Query**|**rfcReceptor**  <br>*opcional*|filtro de comprobantes por RFC del Receptor|string||
|**Query**|**serie**  <br>*opcional*|filtro de comprobnates por serie de control interno del contribuyente|string||
|**Query**|**tipoComprobante**  <br>*opcional*|filtro de comprobantes por clave del efecto del CFDI|enum (I, E, T, N, P)||
|**Query**|**uuid**  <br>*opcional*|búsqueda de comprobante por UUID|string||


##### Respuestas

|Código HTTP|Descripción|Esquema|
|---|---|---|
|**200**|Listado de resultados encontrados.|< [ComprobanteResponse](#comprobanteresponse) > array|
|**default**|Error inesperado al intentar procesar la solicitud|[ErrorResponse](#errorresponse)|


<a name="comprobantes-rfcemisor-acusecancelacion-uuid-pdf-get"></a>
#### Solictar acuse de cancelación.
```
GET /comprobantes/{rfcEmisor}/acusecancelacion/{uuid}.pdf
```


##### Descripción
Solicitar archivo que representa el acuse de cancelación para un CFDI.


##### Parámetros

|Tipo|Nombre|Descripción|Esquema|
|---|---|---|---|
|**Path**|**rfcEmisor**  <br>*obligatorio*|Clave del RFC propietario del CFDI (emisor o receptor)|string|
|**Path**|**uuid**  <br>*obligatorio*|Identificador único de timbre fiscal digital que corresponde a un CFDI|string|


##### Respuestas

|Código HTTP|Descripción|Esquema|
|---|---|---|
|**200**|Archivo asociado encontrado exitosamente.|file|
|**404**|No se ha encontrado el archivo asociado solicitado.|Sin contenido|
|**default**|Error inesperado al intentar procesar la solicitud|[ErrorResponse](#errorresponse)|


<a name="comprobantes-rfcemisor-uuid-tipoarchvo-get"></a>
#### Descargar archivos asociados a CFDI
```
GET /comprobantes/{rfcEmisor}/{uuid}.{tipoArchvo}
```


##### Descripción
Solicitar la descarga de archivos asociados a CFDI.


##### Parámetros

|Tipo|Nombre|Descripción|Esquema|
|---|---|---|---|
|**Path**|**rfcEmisor**  <br>*obligatorio*|Clave del RFC propietario del CFDI (emisor o receptor)|string|
|**Path**|**tipoArchvo**  <br>*obligatorio*|tipo de archivo asociado al CFDI|enum (pdf, xml)|
|**Path**|**uuid**  <br>*obligatorio*|Identificador único de timbre fiscal digital que corresponde a un CFDI|string|


##### Respuestas

|Código HTTP|Descripción|Esquema|
|---|---|---|
|**200**|Archivo asociado encontrado exitosamente.|file|
|**404**|No se ha encontrado el archivo asociado solicitado.|Sin contenido|
|**default**|Error inesperado al intentar procesar la solicitud|[ErrorResponse](#errorresponse)|


##### Produce

* `application/octet-stream`


<a name="timbrado-de-cfdi_resource"></a>
### Timbrado De CFDI

<a name="timbrado-rfcemisor-post"></a>
#### Solicitud de timbrado de comprobantes.
```
POST /timbrado/{rfcEmisor}
```


##### Descripción
Enviar una solicitud en forma de CFDI sellado para que sea timbrado por el SAT.


##### Parámetros

|Tipo|Nombre|Descripción|Esquema|
|---|---|---|---|
|**Path**|**rfcEmisor**  <br>*obligatorio*|Clave del RFC propietario del CFDI (emisor)|string|
|**FormData**|**xmlSellado**  <br>*obligatorio*|XML que representa un CFDI que se desea timbrar.|file|


##### Respuestas

|Código HTTP|Descripción|Esquema|
|---|---|---|
|**200**|CFDI timbrado exitosamente.|file|


##### Consume

* `multipart/form-data`


##### Produce

* `application/xml`


<a name="validacion-rfc_resource"></a>
### Validación RFC

<a name="rfcs-post"></a>
#### Validar RFC.
```
POST /rfcs
```


##### Descripción
Solicitar la validación de claves del Registro Federal de Contribuyentes.


##### Parámetros

|Tipo|Nombre|Esquema|
|---|---|---|
|**FormData**|**rfc**  <br>*obligatorio*|string|


##### Respuestas

|Código HTTP|Descripción|Esquema|
|---|---|---|
|**200**|Solicitud procesada exitosamente|[RfcValidationResponse](#rfcvalidationresponse)|
|**default**|Error inesperado al intentar procesar la solicitud|[ErrorResponse](#errorresponse)|


##### Consume

* `application/x-www-form-urlencoded`



