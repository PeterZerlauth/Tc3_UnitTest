# FB_File

**Type:** `FUNCTION BLOCK`
**Source File:** `File/FB_File.TcPOU`

*No documentation found.*

## Outputs
| Name | Type | Description |
| --- | --- | --- |
| `eError` | `E_AdsError` |  |

## Local Variables
| Name | Type | Description |
| --- | --- | --- |
| `fbCreateDir` | `FB_CreateDir` |  |
| `fbRead` | `FB_FileRead` |  |
| `fbWrite` | `FB_FileWrite` |  |
| `fbDelete` | `FB_FileDelete` |  |

## Methods

### `M_Append` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Text` | `STRING` |  |

**Implementation:**
```iec
fbWrite();
IF fbWrite.bExecute THEN
	IF fbWrite.bError THEN
		eError:= fbWrite.nErrId;
		fbWrite.bExecute:= FALSE;
	ELSIF fbWrite.bBusy THEN
		;
	ELSE
		M_Append:= TRUE;
		fbWrite.bExecute:= FALSE;
	END_IF
ELSE
	fbWrite.bExecute:= TRUE;
	fbWrite.pWriteBuff:= ADR(Text);
	fbWrite.cbWriteLen:= INT_TO_UDINT(Len(Text));
END_IF
```

---
### `M_AppendLine` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Text` | `STRING` |  |

**Implementation:**
```iec
Text:= Concat(Text, '$R');
M_AppendLine:= M_Append(Text);
```

---
### `M_Close` : `BOOL`
*No documentation found.*

**Implementation:**
```iec
fbClose();
IF fbClose.bExecute THEN
	IF fbClose.hFile = 0 THEN
		fbClose.bExecute:= FALSE;
		M_Close:= TRUE;
	ELSIF fbClose.bError THEN
		fbClose.bExecute:= FALSE;
		eError:= fbClose.nErrId;
	ELSIF fbClose.bBusy THEN
		;
	ELSE
		eError:= E_AdsError.NOERR;	
		fbRead.hFile:= 0;
		fbWrite.hFile:= 0;
		fbClose.hFile:= 0;
		fbClose.bExecute:= FALSE;
		M_Close:= TRUE;
	END_IF
ELSE
	fbClose.bExecute:= TRUE;
END_IF
```

---
### `M_Create` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `PathName` | `STRING` |  |

**Implementation:**
```iec
fbCreateDir();
nTemp := FIND(RIGHT(PathName, LEN(PathName) - nPosition), '\');
if nTemp <> 0 then
	IF fbCreateDir.bExecute THEN
		IF NOT fbCreateDir.bBusy THEN
			nPosition := nPosition + nTemp;
			fbCreateDir.bExecute:= FALSE;
		END_IF
	ELSE
		fbCreateDir.bExecute:= TRUE;
		fbCreateDir.ePath:= PATH_GENERIC;
		fbCreateDir.sPathName:= Left(PathName, nPosition + nTemp);
	END_IF
ELSE
	IF M_Open(PathName) THEN
		M_Create:= TRUE;
		nPosition:= 0;
	END_IF
END_IF
```

---
### `M_Delete` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `PathName` | `STRING` |  |

**Implementation:**
```iec
fbDelete();
IF fbDelete.bExecute THEN
	IF fbDelete.bError THEN
		fbDelete.bExecute:= FALSE;
		M_Delete:= TRUE;
	ELSIF fbDelete.bBusy THEN
		;
	ELSE
		fbDelete.bExecute:= FALSE;
		M_Delete:= TRUE;
	END_IF
ELSE
	fbDelete.bExecute:= TRUE;
	fbDelete.sPathName:= PathName;
	fbDelete.ePath:= E_OpenPath.PATH_GENERIC;
END_IF
```

---
### `M_Load` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `PathName` | `STRING` |  |
| `Value` | `ANY` |  |

**Implementation:**
```iec
fbLoad();
IF fbLoad.bExecute THEN
	IF fbLoad.bError THEN
		eError:= fbLoad.nErrId;
		fbLoad.bExecute:= FALSE;
	ELSIF fbLoad.bBusy THEN
		;
	ELSE
		M_Load:= TRUE;
	END_IF
ELSE
	fbLoad.sPathName:= PathName;
	fbLoad.bExecute:= TRUE;
	fbLoad.pReadBuff:= Value.pValue;
	fbLoad.cbReadLen:= DINT_TO_UDINT(Value.diSize);
END_IF
```

---
### `M_Open` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `PathName` | `STRING` |  |

**Implementation:**
```iec
fbOpen();
IF fbOpen.bExecute THEN
	IF fbOpen.bError THEN
		eError:= fbOpen.nErrId;
		fbOpen.bExecute:= FALSE;
	ELSIF fbOpen.bBusy THEN
		;
	ELSE
		fbRead.hFile:= fbOpen.hFile;
		fbWrite.hFile:= fbOpen.hFile;
		fbClose.hFile:= fbOpen.hFile;
		fbOpen.bExecute:= FALSE;
		M_Open:= TRUE;
	END_IF	
ELSE
	fbOpen.bExecute:= TRUE;
	fbOpen.sPathName:= PathName;
	fbOpen.nMode:= (FOPEN_MODEAPPEND OR FOPEN_MODEPLUS OR FOPEN_MODETEXT);
END_IF
```

---
### `M_Read` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Value` | `ANY` |  |

**Implementation:**
```iec
fbRead();
IF fbRead.bExecute THEN
	IF fbRead.bError THEN
		eError:= fbRead.nErrId;
		fbRead.bExecute:= FALSE;
	ELSIF fbRead.bBusy THEN
		;
	ELSE
		fbRead.bExecute:= FALSE;
		M_Read:= TRUE;
	END_IF
ELSE
	fbRead.bExecute:= TRUE;
	fbRead.pReadBuff:= Value.pValue;
	fbRead.cbReadLen:= DINT_TO_UDINT(Value.diSize);
END_IF
```

---
### `M_Write` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Value` | `ANY` |  |

**Implementation:**
```iec
fbWrite();
IF fbWrite.bExecute THEN
	IF fbWrite.bError THEN
		eError:= fbWrite.nErrId;
		fbWrite.bExecute:= FALSE;
	ELSIF fbWrite.bBusy THEN
		M_Write:= FALSE;
	ELSE
		M_Write:= TRUE;
		fbWrite.bExecute:= FALSE;
	END_IF
ELSE
	fbWrite.bExecute:= TRUE;
	fbRead.pReadBuff:= Value.pValue;
	fbRead.cbReadLen:= DINT_TO_UDINT(Value.diSize);
END_IF
```

---

## Properties

### `P_Error`
*No documentation found.*

**Get Implementation:**
```iec
P_Error:= eError;
```

---

## Implementation
```iec
// https://peterzerlauth.com/
```
