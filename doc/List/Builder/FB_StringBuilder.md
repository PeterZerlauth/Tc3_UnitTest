# FB_StringBuilder

**Type:** `FUNCTION BLOCK`
**Source File:** `List/Builder/FB_StringBuilder.TcPOU`

*No documentation found.*

## Methods

### `FB_exit` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `bInCopyCode` | `BOOL` | if TRUE, the exit method is called for exiting an instance that is copied afterwards (online change). |

**Implementation:**
```iec
M_Reset();
```

---
### `M_Append` : `I_StringBuilder`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Value` | `STRING` |  |

**Implementation:**
```iec
// First Item
IF pString = 0 THEN
	nLength:= nValue;
	pString:= __NEW(STRING(1), (nLength + 1));
	CONCAT2(pString, pValue, pString, nLength + 1);
ELSE
	// new Length
	nLength:= nLength + nValue;
	// new pointer
	pString:= __NEW(STRING(1), (SIZEOF(STRING(1)) * (nLength + 1)));
	// copy to
	CONCAT2(pOldList, pValue, pString, nLength + 1);
	// delete old
	__DELETE(pOldList);

END_IF
M_Append:= THIS^;
```

---
### `M_AppendBOOL` : `I_StringBuilder`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Value` | `BOOL` |  |

**Implementation:**
```iec
M_Append(BOOL_TO_STRING(Value));
M_AppendBOOL:= THIS^;
```

---
### `M_AppendINT` : `I_StringBuilder`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Value` | `LINT` |  |

**Implementation:**
```iec
M_Append(LINT_TO_STRING(Value));
M_AppendINT:= THIS^;
```

---
### `M_AppendREAL` : `I_StringBuilder`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Value` | `LREAL` |  |

**Implementation:**
```iec
M_Append(LREAL_TO_FMTSTR(Value, Decimals, TRUE));
M_AppendREAL:= THIS^;
```

---
### `M_Contains` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Value` | `STRING` |  |

**Implementation:**
```iec
M_Contains:= M_Find(Value) <> 0;
```

---
### `M_Find` : `UDINT`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Value` | `STRING` |  |

**Implementation:**
```iec
M_Find:= FIND2(pString, adr(Value));
```

---
### `M_Insert` : `I_StringBuilder`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Position` | `UDINT` |  |

**Implementation:**
```iec
IF nLength > Position AND Position <> 0 THEN
	// new Length
	nLength:= nLength + nValue;
	// new pointer
	pString:= __NEW(STRING(1), (SIZEOF(STRING(1)) * (nLength + 1)));
	// insert
	INSERT2(pOldList, pValue, pString, nLength + 1, Position -1);
	// delete old
	__DELETE(pOldList);
END_IF
M_Insert:= THIS^;
```

---
### `M_Reset` : `I_StringBuilder`
*No documentation found.*

**Implementation:**
```iec
__DELETE(pString);
nLength:= 0;
M_Reset:= THIS^;
```

---
### `M_ToAny` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Value` | `ANY` |  |

**Implementation:**
```iec
Memset(Value.pValue, 0, DINT_TO_UDINT(Value.diSize));
Memcpy(Value.pValue, pString, nLength + 1);
```

---
### `M_ToString` : `STRING`
*No documentation found.*

**Implementation:**
```iec
Memcpy(Adr(M_ToString), pString, nLength + 1);
```

---

## Properties

### `P_Length`
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
