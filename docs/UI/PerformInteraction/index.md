## PerformInteraction

Type
: Function

Sender
: SDL

Purpose
: Perform a UI Interaction with the User.

### Request

#### Parameters

|Name|Type|Mandatory|Additional|
|:---|:---|:--------|:---------|
|initialText|[Common.TextFieldStruct](../../Common/Structs/index.md#textfieldstruct)|false||
|choiceSet|[Common.Choice](../../Common/Structs/index.md#choice)|false|array: true<br>minsize: 1<br>maxsize: 100|
|vrHelpTitle|String|false|maxlength: 500|
|vrHelp|[Common.VrHelpItem](../../Common/Structs/index.md#vrhelpitem)|false|array: true<br>minsize: 1<br>maxsize: 100|
|timeout|Integer|true|minvalue: 5000<br>maxvalue: 100000|
|interactionLayout|[Common.LayoutMode](../../Common/Enums/index.md#layoutmode)|false||
|appID|Integer|true||

### Response

#### Parameters

|Name|Type|Mandatory|Additional|
|:---|:---|:--------|:---------|
|choiceID|Integer|false|minvalue: 0<br>maxvalue: 2000000000|
|manualTextEntry|String|false|minlength: 0<br>maxlength: 500|

### Sequence Diagrams
|||
PerformInteraction Successful with VR Only
![PerformInteraction](./assets/PerformInteractionVROnly.png)
|||
|||
PerformInteraction Successful with Manual Only
![PerformInteraction](./assets/PerformInteractionManualOnly.png)
|||
|||
PerformInteraction Timeout with Both
![PerformInteraction](./assets/PerformInteractionBothTimeout.png)
|||

### Example Request

```json
{
	"id" : 79,
	"jsonrpc" : "2.0",
	"method" : "UI.PerformInteraction",
	"params" :
	{
		"initialText" :
		{
				 "fieldName" : initialInteractionText,
				 "fieldText" : "Choose the station:"
		},

		"choiceSet" :
		[
			{
				 "choiceID" : 2415,
				 "menuName" : "Sky.FM"
			},

			{
				 "choiceID" : 2416,
				 "menuName" : "Paradise"
			},

			{
				 "choiceID" : 2417,
				 "menuName" : "100 XR"
			}
		],

		"vrHelp" :
		[
				{
				 "text" : "Sky FM",
				 "image" :
					[
				 		"value" : "tmp/SDL/app/Pandora/icon_5410.jpg",
				 		"imageType" : DYNAMIC
					],

				 "position" : 1
				},

				{
				 "text" : "Paradise",
				 "image" :
					[
				 		"value" : "tmp/SDL/app/Pandora/icon_5423.jpeg",
				 		"imageType" : DYNAMIC
					],
				 "position" : 2
				},

				{
				 "text" : "100 XR",
				 "image" :
					[
				 		"value" : "tmp/SDL/app/Pandora/icon_5465.jpeg",
				 		"imageType" : DYNAMIC
					],
				 "position" : 3
				}
		],

		"timeout" : 15000,
		"appID" : 6493
	}
}
```
### Example Response

```json
{
	"id" : 79,
	"jsonrpc" : "2.0",
	"result" :
	{
		"choiceID" : 2416
		"code" : 0,
		"method" : "UI.PerformInteraction"
	}
}
```

### Example Error

```json
{
	"id" : 79,
	"jsonrpc" : "2.0",
	"error" :
	{
		"code" : 10,
		"message" : "Overlay reached the maximum timeout and closed",
		"data" :
		{
			"method" : "UI.PerformInteraction"
		}
	}
}
```
