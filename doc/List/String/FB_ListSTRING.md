# FB_ListSTRING

**Type:** `FUNCTION BLOCK`
**Source File:** `List/String/FB_ListSTRING.TcPOU`

*No documentation found.*

## Local Variables
| Name | Type | Description |
| --- | --- | --- |
| `pList` | `POINTER` |  |
| `nLength` | `DINT` |  |

## Methods

### `FB_exit` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `bInCopyCode` | `BOOL` | if TRUE, the exit method is called for exiting an instance that is copied afterwards (online change). |

**Implementation:**
```iec
M_Clear();
```

---
### `M_Add` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Value` | `STRING` |  |

**Implementation:**
```iec
// First Item
IF pList = 0 THEN
	nLength:= nLength + 1;
	pList:= __NEW(POINTER TO STRING(255), SIZEOF(STRING(255)));
ELSE
	// backup 
	pOldList:= pList;
	// new Length
	nLength:= nLength + 1;
	// new pointer
	pList:= __NEW(POINTER TO STRING(255),DINT_TO_UDINT(SIZEOF(STRING(255)) * nLength));
	// restore
	Memcpy(pList,pOldList, DINT_TO_UDINT(SIZEOF(STRING(255)) *(nLength -1)));
	// delete old
	__DELETE(pOldList);
END_IF

// add new Object
IF pList = 0 THEN
	RETURN;
END_IF
pList[nLength-1]:= Value;
M_Add:= TRUE;
```

---
### `M_Clear` : `BOOL`
*No documentation found.*

**Implementation:**
```iec
IF pList <> 0 THEN
	nLength:= 0;
	__DELETE(pList);
	M_Clear:= TRUE;
END_IF
```

---
### `M_Find` : `DINT`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Value` | `STRING` |  |

**Implementation:**
```iec
// Object already in List
M_Find := -1;
WHILE nIndex < nLength DO
    IF pList[nIndex] = Value THEN
        M_Find := nIndex;
        RETURN;
    END_IF
	nIndex := nIndex + 1;
END_WHILE
```

---
### `M_Index` : `DINT`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Value` | `STRING` |  |

**Implementation:**
```iec
// Object already in List
M_Index := -1;
WHILE nIndex < nLength DO
  IF pList[nIndex] = Value THEN
        M_Index := nIndex;
        RETURN;
    END_IF
	nIndex := nIndex + 1;
END_WHILE
```

---
### `M_Insert` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Position` | `DINT` |  |

**Implementation:**
```iec
IF nLength > Position THEN
	// backup 
	pOldList:= pList;
	// new Length
	nLength:= nLength + 1;
	// new pointer
	pList:= __NEW(POINTER TO STRING(255),DINT_TO_UDINT(SIZEOF(STRING(255)) * nLength));
	// restore
	Memcpy(pList, pOldList, DINT_TO_UDINT(SIZEOF(STRING(255)) *(nLength -1)));
	MemMove(pList + DINT_TO_UDINT(SIZEOF(STRING(255)) * (Position + 1)), pList + DINT_TO_UDINT(SIZEOF(STRING(255)) * Position), DINT_TO_UDINT(SIZEOF(STRING(255)) * (nLength - Position + 1)));
	// delete old
	__DELETE(pOldList);
ELSE
	M_Insert:= FALSE;	
	RETURN;
END_IF
// add new Object
pList[Position]:= Value;
M_Insert:= TRUE;
```

---
### `M_Item` : `STRING`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Index` | `DINT` |  |

**Implementation:**
```iec
IF Index < (nLength) THEN
	M_Item:= pList[Index];
END_IF
```

---
### `M_Remove` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Position` | `DINT` |  |

**Implementation:**
```iec
// First Item
IF nLength >= Position THEN
	// backup 
	pOldList:= pList;
	// new Length
	nLength:= nLength -1;
	// new pointer
	pList:= __NEW(POINTER TO STRING(255),DINT_TO_UDINT(SIZEOF(STRING(255)) * nLength));
	// restore lower part
	Memcpy(pList,pOldList, SIZEOF(POINTER TO STRING(255)) * DINT_TO_UDINT(Position));
	//pList[nPosition]:= iObject;
	Memcpy(pList + (SIZEOF(STRING(255))*Position),pOldList + (SIZEOF(STRING(255))*(Position + 1)), SIZEOF(STRING(255)) * DINT_TO_UDINT(nLength - Position));
	// delete old
	__DELETE(pOldList);
ELSE
	M_Remove:= FALSE;	
	RETURN;
END_IF
M_Remove:= TRUE;
```

---
### `M_Set` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Index` | `DINT` |  |

**Implementation:**
```iec
IF Index < (nLength) THEN
	pList[Index]:= Value;
END_IF
```

---

## Properties

### `P_Length` : `DINT`
*No documentation found.*

**Get Implementation:**
```iec
P_Length:= nLength;
```

---

## Implementation
```iec
// https://peterzerlauth.com/
```
