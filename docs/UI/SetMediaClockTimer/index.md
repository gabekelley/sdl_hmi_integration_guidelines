## SetMediaClockTimer

Type
: Function

Sender
: SDL

Purpose
: Set a value and update mode for the media clock of a media application.

### Request

#### Parameters

|Name|Type|Mandatory|Additional|
|:---|:---|:--------|:---------|
|startTime|[Common.TimeFormat](../../Common/Structs/index.md#timeformat)|false||
|endTime|[Common.TimeFormat](../../Common/Structs/index.md#timeformat)|false||
|updateMode|[Common.ClockUpdateMode](../../Common/Enums/index.md#clockupdatemode)|true||
|appID|Integer|true||

### Response

#### Parameters

This RPC has no additional parameter requirements

### Sequence Diagrams
|||
SetMediaClockTimer COUNTUP and COUNTDOWN for Full and Background applications
![SetMediaClockTimer](./assets/SetMediaClockTimerUpDownFullBackground.png)
|||
|||
SetMediaClockTimer Pause and Resume for Active Application
![SetMediaClockTimer](./assets/SetMediaClockTimerPauseResumeActive.png)
|||
|||
SetMediaClockTimer COUNTDOWN for a deactivated application
![SetMediaClockTimer](./assets/SetMediaClockTimerDownDeactivate.png)
|||

### Example Request

```json
{
	"id" : 109,
	"jsonrpc" : "2.0",
	"method" : "UI.SetMediaClockTimer",
	"params" :
	{
		"startTime" :
		{
				 "hours" : 0,
				 "minutes" : 18,
				 "seconds" : 17
		},
		"updateMode" : "COUNTUP",
		"appID" : 65146
	}
}
```
### Example Response

```json
{
	"id" : 109,
	"jsonrpc" : "2.0",
	"result" :
	{
		"code" : 0,
		"method" : "UI.SetMediaClockTimer"
	}
}
```

### Example Error

```json
{
	"id" : 109,
	"jsonrpc" : "2.0",
	"error" :
	{
		"code" : 11,
		"message" : "Invalid data",
		"data" :
		{
			"method" : "UI.SetMediaClockTimer"
		}
	}
}
```
