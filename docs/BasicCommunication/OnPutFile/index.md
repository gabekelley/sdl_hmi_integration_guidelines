## OnPutFile

Type
: Notification

Sender
: SDL

Purpose
: Inform the HMI that a file has been uploaded into a shared folder by an application.

### Notification

#### Parameters

|Name|Type|Mandatory|Additional|
|:---|:---|:--------|:---------|
|offset|Integer|false|minvalue: 0<br>maxvalue: 100000000000|
|length|Integer|false|minvalue: 0<br>maxvalue: 100000000000|
|fileSize|Integer|false|minvalue: 0<br>maxvalue: 100000000000|
|FileName|String|true|maxlength: 255|
|syncFileName|String|true|maxlength: 255|
|fileType|[Common.FileType](../../Common/Enums/index.md#filetype)|true||
|persistentFile|Boolean|false||

### Sequence Diagrams
|||
Put File used before referencing RPC
![OnPutFile](./assets/OnPutFileBeforeRPC.png)
|||
|||
Put File used after referencing RPC
![OnPutFile](./assets/OnPutFileAfterRPC.png)
|||
|||
System Request file upload using Put File
![OnPutFile](./assets/OnPutFileSystemRequest.png)
|||

#### JSON Example Notification
```json
{
	"jsonrpc" : "2.0",
	"method" : "BasicCommunication.OnPutFile"
  {
     "fileName":"/fs/sharedFolder/app1_device1/icon.jpg",
     "fileType":"GRAPHIC_JPEG"
    }
}
```
