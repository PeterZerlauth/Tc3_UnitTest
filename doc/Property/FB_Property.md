# FB_Property

**Type:** `FUNCTION BLOCK`
**Source File:** `Property/FB_Property.TcPOU`

*No documentation found.*

## Methods

### `M_Add` : `BOOL`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Name` | `STRING` |  |
| `Value` | `STRING` |  |

**Implementation:**
```iec
fbStringBuilder.M_Reset();
fbStringBuilder.M_Append('<property name="');
fbStringBuilder.M_Append(Name);
sKey:= fbStringBuilder.M_ToString();
fbStringBuilder.M_Append('" value="');
fbStringBuilder.M_Append(Value);
fbStringBuilder.M_Append('" />');

WHILE nIndex < fbList.P_Length DO
	IF FIND(fbList.M_Item(nIndex), sKey) <> 0 THEN
		fbList.M_Set(nIndex, fbStringBuilder.M_ToString());
		RETURN;
	END_IF
	nIndex:= nIndex +1;
END_WHILE
fbList.M_Add(fbStringBuilder.M_ToString());
M_Add:= TRUE;
```

---
### `M_Reset`
*No documentation found.*

**Implementation:**
```iec
fbStringBuilder.M_Reset();
fbList.M_Clear();
```

---

## Properties

### `P_List`
*No documentation found.*

**Get Implementation:**
```iec
P_List:= fbList;
```

---

## Implementation
```iec
// https://peterzerlauth.com/
```
