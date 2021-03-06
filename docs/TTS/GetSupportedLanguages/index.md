## GetSupportedLanguages

Type
: Function

Sender
: SDL

Purpose
: Get the supported TTS languages

### Request

#### Parameters

|Name|Type|Mandatory|Additional|
|:---|:---|:--------|:---------|

### Response

#### Parameters

|Name|Type|Mandatory|Additional|
|:---|:---|:--------|:---------|
|languages|[Common.Language](../../Common/Enums/index.md#language)|true|array: true<br>minsize: 1<br>maxsize: 100|

### Sequence Diagrams
|||
GetSupportedLanguages
![GetSupportedLanguages](./assets/GetSupportedLanguages.png)
|||

### Example Request

```json
{
	"id" : 19,
	"jsonrpc" : "2.0",
	"method" : "TTS.GetSupportedLanguages"
}
```
### Example Response

```json
{
	"id" : 19,
	"jsonrpc" : "2.0",
	"result" :
	{
		"languages" : [AR-SA, DE-DE, EN-GB, EN-US, ES-ES, FR-FR, IT-IT],
		"code" : 0,
		"method" : "TTS.GetSupportedLanguages"
	}
}
```

### Example Error

```json
{
	"id" : 19,
	"jsonrpc" : "2.0",
	"error" :
	{
		"code" : 11,
		"message" : "The data sent is invalid",
		"data" :
		{
			"method" : "TTS.GetSupportedLanguages"
		}
	}
}
```
