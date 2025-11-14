# FB_Testsuites

**Type:** `FUNCTION BLOCK`
**Source File:** `Testsuites/FB_Testsuites.TcPOU`

*No documentation found.*

## Methods

### `M_Add` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Testsuite` | `I_Testsuite` |  |

**Implementation:**
```iec
fbListTestsuite.M_Add(Testsuite);
Testsuite.P_Parent:= THIS^;
Testsuite.P_Logger:= fbLogger;
```

---
### `M_Execute` : `BOOL`
*No documentation found.*

**Implementation:**
```iec
M_Execute:= TRUE;
fbTimeout(IN:= TRUE);
WHILE nIndex < fbListTestsuite.P_Length DO
	IF __QUERYINTERFACE(fbListTestsuite.M_Get(nIndex), iTestsuite) THEN
		M_Execute:= M_Execute AND (iTestsuite.P_State = E_Base.Stopped);
	END_IF
	nIndex:= nIndex + 1;
END_WHILE
IF M_Execute THEN
	stTestsuites.fTime:= TIME_TO_LREAL(fbTimeout.ET) / 1000.0;
	fbTimeout(IN:= FALSE);
END_IF
```

---
### `M_Starting` : `BOOL`
*No documentation found.*

**Implementation:**
```iec
CASE nState OF
	0:
		IF 	SUPER^.M_Starting() THEN
			fbList.M_Clear();
			fbProperty.M_Reset();
			stTestsuites.sName:= F_GetName(sInstancePath);
			stTestsuites.nTests:= 0;
			stTestsuites.nFailures:= 0;
			stTestsuites.nErrors:= 0;
			stTestsuites.nSkipped:= 0;
			stTestsuites.nAssertions:= 0;
			stTestsuites.fTime:= 0.0;
			stTestsuites.sTimestamp:= SYSTEMTIME_TO_ISO8601(fbGetTime.TIMESTR, 0, FALSE, 3);
			stTestsuites.sTimestamp:= LEFT(stTestsuites.sTimestamp, LEN(stTestsuites.sTimestamp) - 6);
			nState:= 1;
		END_IF
	
	1:
		WHILE nIndex < fbListTestsuite.P_Length DO
			IF __QUERYINTERFACE(fbListTestsuite.M_Get(nIndex), iTestsuite) THEN
				iTestsuite.M_Request(E_Base.Execute);
			END_IF
			nIndex:= nIndex + 1;
		END_WHILE
		nState:= 2;
		
	2:
		M_Starting:= TRUE;
		
END_CASE
```

---
### `M_Stopping` : `BOOL`
*No documentation found.*

**Implementation:**
```iec
CASE nState OF
	0:
		//<testsuites name="Test run" tests="8" failures="1" errors="1" skipped="1"  assertions="20" time="16.082687" timestamp="2021-04-02T15:48:23">
		fbList.M_Insert(0, '<?xml version="1.0" encoding="UTF-8"?>');
		fbBuilder.M_Reset();
		fbBuilder.M_Append('<testsuites name="');	
		fbBuilder.M_Append(stTestsuites.sName);		
		fbBuilder.M_Append('" tests="');	
		fbBuilder.M_AppendINT(stTestsuites.nTests);
		fbBuilder.M_Append('" failures="');	
		fbBuilder.M_AppendINT(stTestsuites.nFailures);
		fbBuilder.M_Append('" errors="');	
		fbBuilder.M_AppendINT(stTestsuites.nErrors);
		fbBuilder.M_Append('" skipped="');	
		fbBuilder.M_AppendINT(stTestsuites.nSkipped);
		fbBuilder.M_Append('" assertions="');	
		fbBuilder.M_AppendINT(stTestsuites.nAssertions);
		fbBuilder.M_Append('" time="');	
		fbBuilder.M_AppendREAL(stTestsuites.fTime, 3);
		fbBuilder.M_Append('" timestamp="');
		fbBuilder.M_Append(stTestsuites.sTimestamp);
		fbBuilder.M_Append('">');
		fbBuilder.M_ToAny(sValue);
		fbList.M_Insert(1, sValue);
		fbList.M_Add('</testsuites>');
		nState:= 1;
	1:	
		// add Properties
		IF fbProperty.P_List.P_Length > 0 THEN
			fbList.M_Insert(2, '$T<properties>');
			nIndex:= 0;
			WHILE nIndex < fbProperty.P_List.P_Length DO
				fbList.M_Insert(3 + nIndex, Concat('$T$T', fbProperty.P_List.M_Item(nIndex)));
				nIndex:= nIndex + 1;
			END_WHILE
			fbList.M_Insert(3 + nIndex, '$T</properties>');
		END_IF
		nState:= 2;
		
	2:
		fbBuilder.M_Reset();
		fbBuilder.M_Append(stTestsuites.sName);		
		fbBuilder.M_Append(': tests= ');
		fbBuilder.M_AppendINT(stTestsuites.nTests);
		fbBuilder.M_Append(' failures= ');	
		fbBuilder.M_AppendINT(stTestsuites.nFailures);
		fbBuilder.M_Append(' errors= ');	
		fbBuilder.M_AppendINT(stTestsuites.nErrors);
		fbBuilder.M_Append(' skipped= ');	
		fbBuilder.M_AppendINT(stTestsuites.nSkipped);
		fbBuilder.M_Append(' assertions= ');
		fbBuilder.M_AppendINT(stTestsuites.nAssertions);
		fbBuilder.M_ToAny(sValue);
		IF stTestsuites.nFailures <> 0 OR_ELSE stTestsuites.nErrors <> 0 THEN
			fbLogger.M_Error(sValue);
		ELSIF stTestsuites.nSkipped <> 0 THEN
			fbLogger.M_Warning(sValue);
		ELSE
			fbLogger.M_Info(sValue);
		END_IF
		nState:= 3;
			
	3:
		IF fbFile.M_Delete(stOptions.sFilePathName) THEN
			nState:= 4;
		END_IF	
	
	4:
		IF fbFile.M_Create(stOptions.sFilePathName) THEN
			nState:= 5;
			nIndex:= 0;
		END_IF
	
	5:
			IF fbFile.M_AppendLine(fbList.M_Item(nIndex)) THEN
				IF nIndex > fbList.P_Length THEN
					nState:= 6;
				END_IF
				nIndex:= nIndex +1;
			END_IF	
	6:
		M_Stopping:= fbFile.M_Close();	
		
END_CASE
```

---

## Properties

### `P_Data`
*No documentation found.*

**Get Implementation:**
```iec
P_Data ref= stTestsuites;
```
**Set Implementation:**
```iec
P_Data ref= stTestsuites;
```

---
### `P_List`
*No documentation found.*

**Get Implementation:**
```iec
P_List:= fbList;
```

---
### `P_Options`
*No documentation found.*

**Get Implementation:**
```iec
P_Options ref= stOptions;
```
**Set Implementation:**
```iec
P_Options ref= stOptions;
```

---
### `P_Property`
*No documentation found.*

**Get Implementation:**
```iec
P_Property:= fbProperty;
```

---

## Implementation
```iec
// https://peterzerlauth.com/
SUPER^();
```
