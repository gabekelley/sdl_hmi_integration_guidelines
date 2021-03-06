## Alert

Type
: Function

Sender
: SDL

Purpose
: Display an alert message on the HMI

### Request

#### Parameters

|Name|Type|Mandatory|Additional|
|:---|:---|:--------|:---------|
|alertStrings|[Common.TextFieldStruct](../../Common/Structs/index.md#textfieldstruct)|true|array: true<br>minsize: 0<br>maxsize: 3|
|duration|Integer|true|minvalue: 3000<br>maxvalue: 10000|
|softButtons|[Common.SoftButton](../../Common/Structs/index.md#softbutton)|false|array: true<br>minsize: 0<br>maxsize: 4|
|progressIndicator|Boolean|false||
|alertType|[Common.AlertType](../../Common/Enums/index.md#alerttype)|true||
|appID|Integer|true||

### Response

#### Parameters

|Name|Type|Mandatory|Additional|
|:---|:---|:--------|:---------|
|tryAgainTime|Integer|false|minvalue: 0<br>maxvalue: 2000000000|

### Sequence Diagrams
|||
Alert with PlayTone and Speak
![Alert](./assets/AlertPlayToneSpeak.png)
|||
|||
Alert closed by DEFAULT_ACTION
![Alert](./assets/AlertDefaultAction.png)
|||
|||
Alert closed by STEAL_FOCUS
![Alert](./assets/AlertStealFocus.png)
|||
|||
Alert Aborted by VR Session
![Alert](./assets/AlertAborted.png)
|||
|||
Alert Rejected
![Alert](./assets/AlertRejected.png)
|||
|||
Alert BOTH UI Closed before TTS finishes Speaking
![Alert](./assets/AlertTTS.png)
|||

### Example Request

```json
{
	"id" : 92,
	"jsonrpc" : "2.0",
	"method" : "UI. Alert",
	"params" :
	{
		"alertStrings" :
		[
			{
				 "fieldName" : alertText1,
				 "fieldText" : "WARNING"
			},
			{
				 "fieldName" : alertText2,
				 "fieldText" : "Hard weather conditions"
			}
		],
		"duration" : 5000,
		"softButtons" :
		{
			"type" : TEXT,
			"text" : "OK",
			"softButtonID" : 697,
			"systemAction" : DEFAULT_ACTION
		},
      "alertType": "BOTH",
		"appID" : 65539
	}
}
```
### Example Response

```json
{
	"id" : 92,
	"jsonrpc" : "2.0",
	"result" :
	{
		"code" : 0,
		"method" : "UI.Alert"
	}
}
```

### Example Error

```json
{
	"id" : 92,
	"jsonrpc" : "2.0",
	"error" :
	{
		"code" : 4,
		"message" : "The requested command was rejected.",
		"data" :
		{
			"tryAgainTime" : 10000,
			"method" : "UI.Alert"
		}
	}
}
```
