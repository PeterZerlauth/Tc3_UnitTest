# FB_Testsuite

**Type:** `FUNCTION BLOCK`
**Source File:** `Testsuite/FB_Testsuite.TcPOU`

*No documentation found.*

## Methods

### `M_Execute` : `BOOL`
*No documentation found.*

**Implementation:**
```iec
IF fbTimeout.PT <> T#0S THEN
	fbTimeout(IN:= TRUE);
END_IF
stTestcase.nAssertions:= fbAssert.nAssert;
IF nActual <> nNext THEN
	IF fbAssert.nSkipped <> 0 THEN
			fbBuilder.M_Reset();
			fbBuilder.M_Append('$T$T<testcase name="');
			fbBuilder.M_Append(stTestCase.sName);
			fbBuilder.M_Append('" classname="');
			fbBuilder.M_Append(stTestCase.sClassname);
			fbBuilder.M_Append('" assertions="');
			fbBuilder.M_AppendINT(stTestCase.nAssertions);
			fbBuilder.M_Append('" time="');
			fbBuilder.M_AppendREAL(stTestCase.fTime, 4);
			fbBuilder.M_Append('" file="');
			fbBuilder.M_Append(stTestCase.sFile);
			fbBuilder.M_Append('" line="');
			fbBuilder.M_Append(stTestCase.sLine);
			fbBuilder.M_Append('" >');
			fbList.M_Add(fbBuilder.M_ToString());
			WHILE nIndex < fbAssert.fbList.P_Length DO
				fbList.M_Add(fbAssert.fbList.M_Item(nIndex));
				IF iLogger <> 0 THEN
					iLogger.M_Warning(stTestcase.sName);					
				END_IF
				nIndex:= nIndex + 1;
			END_WHILE
			fbList.M_Add('$T$T</testcase>');
			stTestsuite.nTests:= stTestsuite.nTests + 1;
			stTestsuite.nFailures:= stTestsuite.nFailures + fbAssert.nFailures;
			stTestsuite.nErrors:= stTestsuite.nErrors + fbAssert.nErrors;
			stTestsuite.nSkipped:= stTestsuite.nSkipped + fbAssert.nSkipped;
			stTestsuite.nAssertions:= stTestsuite.nAssertions + fbAssert.nAssert;
			stTestcase.fTime:= 0.0;
			fbTimeout(IN:= FALSE);
			nActual:= nNext;
	ELSIF fbAssert.nPassed = fbAssert.nAssert THEN
		fbBuilder.M_Reset();
		fbBuilder.M_Append('$T$T<testcase name="');
		fbBuilder.M_Append(stTestcase.sName);
		fbBuilder.M_Append('" classname="');
		fbBuilder.M_Append(stTestcase.sClassname);
		fbBuilder.M_Append('" assertions="');
		fbBuilder.M_AppendINT(stTestcase.nAssertions);
		fbBuilder.M_Append('" time="');
		fbBuilder.M_AppendREAL(stTestcase.fTime, 4);
		fbBuilder.M_Append('" file="');
		fbBuilder.M_Append(stTestcase.sFile);
		fbBuilder.M_Append('" line="');
		fbBuilder.M_Append(stTestcase.sLine);
		fbBuilder.M_Append('" />');
		fbList.M_Add(fbBuilder.M_ToString());
	
		stTestsuite.nTests:= stTestsuite.nTests + 1;
		stTestsuite.nFailures:= stTestsuite.nFailures + fbAssert.nFailures;
		stTestsuite.nErrors:= stTestsuite.nErrors + fbAssert.nErrors;
		stTestsuite.nSkipped:= stTestsuite.nSkipped + fbAssert.nSkipped;
		stTestsuite.nAssertions:= stTestsuite.nAssertions + fbAssert.nAssert;
		fbTimeout(IN:= FALSE);
		stTestcase.fTime:= 0.0;
		nActual:= nNext;
	ELSE
		IF fbTimeout.Q THEN
			fbBuilder.M_Reset();
			fbBuilder.M_Append('$T$T<testcase name="');
			fbBuilder.M_Append(stTestCase.sName);
			fbBuilder.M_Append('" classname="');
			fbBuilder.M_Append(stTestCase.sClassname);
			fbBuilder.M_Append('" assertions="');
			fbBuilder.M_AppendINT(stTestCase.nAssertions);
			fbBuilder.M_Append('" time="');
			fbBuilder.M_AppendREAL(stTestCase.fTime, 4);
			fbBuilder.M_Append('" file="');
			fbBuilder.M_Append(stTestCase.sFile);
			fbBuilder.M_Append('" line="');
			fbBuilder.M_Append(stTestCase.sLine);
			fbBuilder.M_Append('" >');
			fbList.M_Add(fbBuilder.M_ToString());
			WHILE nIndex < fbAssert.fbList.P_Length DO
				fbList.M_Add(fbAssert.fbList.M_Item(nIndex));
				IF iLogger <> 0 THEN
					iLogger.M_Error(stTestcase.sName);	
				END_IF
				nIndex:= nIndex + 1;
			END_WHILE
			stTestsuite.nTests:= stTestsuite.nTests + 1;
			stTestsuite.nFailures:= stTestsuite.nFailures + fbAssert.nFailures;
			stTestsuite.nErrors:= stTestsuite.nErrors + fbAssert.nErrors;
			stTestsuite.nSkipped:= stTestsuite.nSkipped + fbAssert.nSkipped;
			stTestsuite.nAssertions:= stTestsuite.nAssertions + fbAssert.nAssert;
			stTestcase.fTime:= 0.0;
			fbTimeout(IN:= FALSE);
			IF stOptions.bAbortOnError THEN
				// Aborted on error in test results
				iLogger.M_Error('Aborted on Error');
				stTestsuite.nFailures:= stTestsuite.nFailures + 1;
				fbList.M_Add('$T$T$T"Aborted on Error"');
				nActual := E_Testcase.Done;
			ELSE
				nActual := nNext;
			END_IF
			fbList.M_Add('$T$T</testcase>');
		END_IF
	END_IF
END_IF
fbRuntime(IN:= TRUE);
stTestsuite.fTime:=  TIME_TO_LREAL(fbRuntime.ET) / 1000.0;
fbAssert.M_Reset();
M_Execute:= nActual = E_Testcase.Done;
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
			fCycleTime:= F_GetCycleTime();	
			stTestsuite.sName:= F_GetName(sInstancePath);
			stTestsuite.nTests:= 0;
			stTestsuite.nFailures:= 0;		
			stTestsuite.nErrors:= 0;	
			stTestsuite.nSkipped:= 0;		
			stTestsuite.nAssertions:= 0;	
			stTestsuite.fTime:= 0.0;
			stTestsuite.sFile:= '';
			stTestsuite.sTimestamp:= SYSTEMTIME_TO_ISO8601(fbGetTime.TIMESTR, 0, FALSE, 3);
			stTestsuite.sTimestamp:= LEFT(stTestsuite.sTimestamp, LEN(stTestsuite.sTimestamp) - 6);
			nState:= 1;
		END_IF
		
	1:
		nActual:= E_Testcase.Start;
		fbRuntime.IN:= True;
		M_Starting:= TRUE;
	
END_CASE
```

---
### `M_Stopping` : `BOOL`
*No documentation found.*

**Implementation:**
```iec
//    <testsuite name="Tests.Registration" tests="8" failures="1" errors="1" skipped="1" assertions="20" time="16.082687" timestamp="2021-04-02T15:48:23" file="tests/registration.code">
fbBuilder.M_Reset();
fbBuilder.M_Append('$T<testsuite name="');
fbBuilder.M_Append(stTestsuite.sName);
fbBuilder.M_Append('" tests="');
fbBuilder.M_AppendINT(stTestsuite.nTests);
fbBuilder.M_Append('" failures="');
fbBuilder.M_AppendINT(stTestsuite.nFailures);
fbBuilder.M_Append('" errors="');
fbBuilder.M_AppendINT(stTestsuite.nErrors);
fbBuilder.M_Append('" skipped="');
fbBuilder.M_AppendINT(stTestsuite.nSkipped);
fbBuilder.M_Append('" assertions="');
fbBuilder.M_AppendINT(stTestsuite.nAssertions);	
fbBuilder.M_Append('" time="');
fbBuilder.M_AppendREAL(stTestsuite.fTime, 3);
fbBuilder.M_Append('" timestamp="');
fbBuilder.M_Append(stTestsuite.sTimestamp);
fbBuilder.M_Append('" file="');
fbBuilder.M_Append(stTestsuite.sFile);
fbBuilder.M_Append('">');
fbBuilder.M_ToAny(sValue);
fbList.M_Insert(0, sValue);

// add Properties
IF fbProperty.P_List.P_Length > 0 THEN
	fbList.M_Insert(1, '$T$T<properties>');
	nIndex:= 0;
	WHILE nIndex < fbProperty.P_List.P_Length DO
		fbList.M_Insert(2 + nIndex, Concat('$T$T$T', fbProperty.P_List.M_Item(nIndex)));
		nIndex:= nIndex + 1;
	END_WHILE
	fbList.M_Insert(2 + nIndex, '$T$T</properties>');
END_IF

fbList.M_Add('$T</testsuite>');
IF iParent <> 0 THEN
	iParent.P_Data.nTests:= iParent.P_Data.nTests + stTestsuite.nTests;
	iParent.P_Data.nFailures:= iParent.P_Data.nFailures + stTestsuite.nFailures;
	iParent.P_Data.nErrors:= iParent.P_Data.nErrors + stTestsuite.nErrors;
	iParent.P_Data.nSkipped:= iParent.P_Data.nSkipped + stTestsuite.nSkipped;
	iParent.P_Data.nAssertions:= iParent.P_Data.nAssertions + stTestsuite.nAssertions;
	nIndex:= 0;
	WHILE nIndex < fbList.P_Length DO
		iParent.P_List.M_Add(fbList.M_Item(nIndex));
		nIndex:= nIndex + 1;
	END_WHILE
END_IF
fbTimeout(IN:=FALSE);
fbRuntime(IN:=FALSE);
M_Stopping:= TRUE;
```

---
### `M_Testcase` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Classname` | `STRING` |  |
| `Timeout` | `TIME` | Timeout as time |
| `File` | `STRING` |  |
| `Line` | `STRING` |  |
| `Next` | `INT` | Next Testcase as int |

**Implementation:**
```iec
stTestcase.sName:= CONCAT(CONCAT(CONCAT(stTestsuite.sName,'.'), 'M_Testcase_'), INT_TO_STRING(nActual));
stTestcase.sClassname:= Classname;
stTestcase.nAssertions:= fbAssert.fbList.P_Length;
stTestcase.sFile:= File;
stTestcase.sLine:= Line;
stTestcase.fTime:= stTestcase.fTime + fCycleTime;
fbTimeout.PT:= Timeout;
nNext:= Next;
```

---

## Properties

### `P_Assert`
*No documentation found.*

**Get Implementation:**
```iec
P_Assert:= fbAssert;
```

---
### `P_File`
*No documentation found.*

**Get Implementation:**
```iec
P_File:= stTestsuite.sFile;
```
**Set Implementation:**
```iec
stTestsuite.sFile:= P_File;
```

---
### `P_List`
*No documentation found.*

**Get Implementation:**
```iec
P_List:= fbList;
```

---
### `P_Logger`
*No documentation found.*

**Get Implementation:**
```iec
P_Logger:= iLogger;
```
**Set Implementation:**
```iec
iLogger:= P_Logger;
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
### `P_Parent`
*No documentation found.*

**Get Implementation:**
```iec
P_Parent:= iParent;
```
**Set Implementation:**
```iec
iParent:= P_Parent;
```

---
### `P_Property`
*No documentation found.*

**Get Implementation:**
```iec
P_Property:= fbProperty;
```

---
### `P_Testcase`
*No documentation found.*

**Get Implementation:**
```iec
P_Testcase:= nActual;
```

---

## Implementation
```iec
// https://peterzerlauth.com/
SUPER^();
```
