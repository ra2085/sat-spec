
<a name="definitions"></a>
## Definiciones

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


<a name="errorresponse"></a>
### ErrorResponse

|Nombre|Esquema|
|---|---|
|**code**  <br>*obligatorio*|integer|
|**message**  <br>*obligatorio*|string|


<a name="rfcvalidationresponse"></a>
### RfcValidationResponse

|Nombre|Esquema|
|---|---|
|**esValido**  <br>*obligatorio*|boolean|
|**motivo**  <br>*obligatorio*|string|
|**rfc**  <br>*obligatorio*|string|



