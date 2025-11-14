# FB_Base

**Type:** `FUNCTION BLOCK`
**Source File:** `Base/FB_Base.TcPOU`

*No documentation found.*

## Methods

### `M_Aborted` : `BOOL`
*No documentation found.*

---
### `M_Aborting` : `BOOL`
*No documentation found.*

---
### `M_Execute` : `BOOL`
*No documentation found.*

---
### `M_Init` : `BOOL`
*No documentation found.*

**Implementation:**
```iec
M_Init:= True;
```

---
### `M_Request` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `eState` | `E_Base` |  |

**Implementation:**
```iec
eRequest:= eState;
M_Request:= this^.eState = eRequest;
```

---
### `M_Starting` : `BOOL`
*No documentation found.*

**Implementation:**
```iec
IF fbGetTime.START THEN
	IF fbGetTime.BUSY THEN
		;
	ELSE
		fbGetTime.START:= FALSE;
		M_Starting:= TRUE;
	END_IF
ELSE
	fbGetTime.START:= TRUE;
END_IF
```

---
### `M_Stopped` : `BOOL`
*No documentation found.*

---
### `M_Stopping` : `BOOL`
*No documentation found.*

**Implementation:**
```iec
M_Stopping:= True;
```

---

## Properties

### `P_State`
*No documentation found.*

**Get Implementation:**
```iec
P_State:= eState;
```

---

## Implementation
```iec
// https://peterzerlauth.com/
// Prevent double calls
IF nCycleCount <> TwinCAT_SystemInfoVarList._TaskInfo[GETCURTASKINDEXEX()].CycleCount THEN
	nCycleCount:= TwinCAT_SystemInfoVarList._TaskInfo[GETCURTASKINDEXEX()].CycleCount;
	
	fbGetTime();
	
	CASE eState OF
		E_Base.Init:
			IF M_Init() THEN
				eState:= E_Base.Stopped;
				nState:= 0;
			END_IF
			
		E_Base.Stopped:
			IF M_Stopped() THEN
				eState:= E_Base.Starting;
				nState:= 0;
			ELSE
				CASE eRequest OF
					E_Base.Starting, E_Base.Execute:
						eState:= E_Base.Starting;
						nState:= 0;
				END_CASE
			END_IF
			
		E_Base.Starting:
			IF M_Starting() THEN
				eState:= E_Base.Execute;
				nState:= 0;
			END_IF
			
		E_Base.Execute:
			IF M_Execute() THEN
				eState:= E_Base.Stopping;
				nState:= 0;
			ELSE
				CASE eRequest OF
					E_Base.Stopping, E_Base.Stopped:
						eState:= E_Base.Stopping;
						nState:= 0;
				END_CASE
			END_IF
			
		E_Base.Stopping:
			IF M_Stopping() THEN
				eState:= E_Base.Stopped;
				nState:= 0;
			END_IF
	
		E_Base.Aborting:
			IF M_Aborting() THEN
				eState:= E_Base.Aborted;
				nState:= 0;
			END_IF
		
		E_Base.Aborted:
			IF M_Aborted() THEN
				eState:= E_Base.Aborted;
				nState:= 0;
			ELSE
				CASE eRequest OF
					E_Base.Reset:
						eState:= E_Base.Starting;
						nState:= 0;
				END_CASE
			END_IF
			
	END_CASE
	
	eRequest:= eState;
END_IF
```
