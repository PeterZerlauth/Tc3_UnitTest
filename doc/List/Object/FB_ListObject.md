# FB_ListObject

**Type:** `FUNCTION BLOCK`
**Source File:** `List/Object/FB_ListObject.TcPOU`

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
| `Object` | `I_Object` |  |

**Implementation:**
```iec
IF Object <> 0 THEN
	// First Item
	IF pList = 0 THEN
		nLength:= nLength + 1;
		pList:= __NEW(POINTER TO I_Object,DINT_TO_UDINT(nLength));
	ELSE
		// Item already in List
		IF M_Find(Object) = -1 THEN
			// backup 
			pOldList:= pList;
			// new Length
			nLength:= nLength + 1;
			// new pointer
			pList:= __NEW(POINTER TO I_Object,DINT_TO_UDINT(nLength));
			// restore
			Memcpy(pList,pOldList, SIZEOF(POINTER TO I_Object)*DINT_TO_UDINT(nLength -1));
			// delete old
			__DELETE(pOldList);
		ELSE
			M_Add:= FALSE;	
			RETURN;
		END_IF
	END_IF
	IF pList = 0 THEN
		RETURN;
	END_IF
	// add new Object
	pList[nLength-1]:= Object;
	M_Add:= TRUE;
ELSE
	M_Add:= FALSE;	
END_IF
```

---
### `M_Clear`
*No documentation found.*

**Implementation:**
```iec
IF pList <> 0 THEN
	nLength:= 0;
	__DELETE(pList);
END_IF
```

---
### `M_Find` : `DINT`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Object` | `I_Object` |  |

**Implementation:**
```iec
// Object already in List
M_Find := -1;
WHILE nIndex < nLength DO
    IF (pList[nIndex] = Object) THEN
        M_Find := nIndex;
        RETURN;
    END_IF
	nIndex := nIndex + 1;
END_WHILE
```

---
### `M_Get` : `I_Object`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Index` | `DINT` |  |

**Implementation:**
```iec
IF Index <= nLength THEN
	M_Get:= pList[Index];
END_IF
```

---
### `M_Index` : `DINT`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Object` | `I_Object` |  |

**Implementation:**
```iec
// Object already in List
M_Index := -1;
WHILE nIndex < nLength DO
    IF (pList[nIndex] = Object) THEN
        M_Index := nIndex;
        RETURN;
    END_IF
	nIndex := nIndex + 1;
END_WHILE
```

---
### `M_Remove` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Object` | `I_Object` |  |

**Implementation:**
```iec
IF Object <> 0 THEN
	// First Item
	IF nLength >= 0 THEN
		// Item already in List
		nPosition:= M_Find(Object);
		IF nPosition <> -1 THEN
			// backup 
			pOldList:= pList;
			// new Length
			nLength:= nLength -1;
			// new pointer
			pList:= __NEW(POINTER TO I_Object,DINT_TO_UDINT(nLength));
			// restore lower part
			Memcpy(pList,pOldList, SIZEOF(POINTER TO I_Object) * DINT_TO_UDINT(nPosition));
			//pList[nPosition]:= iObject;
			Memcpy(pList + (SIZEOF(POINTER TO I_Object)*nPosition),pOldList + (SIZEOF(POINTER TO I_Object)*(nPosition + 1)), SIZEOF(POINTER TO I_Object) * DINT_TO_UDINT(nLength - nPosition));
			// delete old
			__DELETE(pOldList);
		ELSE
			M_Remove:= FALSE;	
			RETURN;
		END_IF
	ELSE
		M_Remove:= FALSE;	
		RETURN;
	END_IF
	M_Remove:= TRUE;
ELSE
	M_Remove:= FALSE;	
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
