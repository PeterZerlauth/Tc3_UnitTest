# FB_Assert

**Type:** `FUNCTION BLOCK`
**Source File:** `Assert/FB_Assert.TcPOU`

*No documentation found.*

## Outputs
| Name | Type | Description |
| --- | --- | --- |
| `fbList` | `FB_ListSTRING` |  |
| `nPassed` | `DINT` |  |
| `nFailures` | `DINT` |  |

## Methods

### `M_Assert`
*No documentation found.*

**Implementation:**
```iec
IF nSkipped = 0 THEN
	nAssert:= nAssert + 1;
END_IF
```

---
### `M_Equals` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Expected` | `ANY` | Expected as udint |
| `Actual` | `ANY` | Actual as udint |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();

fbJson.ResetDocument();
sDatatypeExpected:= fbJsonDataType.GetDatatypeNameByAddress(nData:= DINT_TO_UDINT(Expected.diSize), pData:= Expected.pValue);
fbJsonDataType.AddJsonValueFromSymbol(fbJson, sDatatypeExpected, DINT_TO_UDINT(Expected.diSize), Expected.pValue);
fbJson.CopyDocument(sJsonExpected, SIZEOF(sJsonExpected));

fbJson.ResetDocument();
sDatatypeActual:= fbJsonDataType.GetDatatypeNameByAddress(nData:= DINT_TO_UDINT(Actual.diSize), pData:= Actual.pValue);
fbJsonDataType.AddJsonValueFromSymbol(fbJson, sDatatypeActual, DINT_TO_UDINT(Actual.diSize), Actual.pValue);
fbJson.CopyDocument(sJsonActual, SIZEOF(sJsonActual));

IF sDatatypeExpected <> sDatatypeActual THEN
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = ');
	fbBuilder.M_Append(sDatatypeExpected);
	fbBuilder.M_Append(' Actual = ');
	fbBuilder.M_Append(sDatatypeActual);
	M_Failure(fbBuilder.M_ToString(), Message);
ELSIF sJsonExpected <> sJsonActual THEN
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = ');
	fbBuilder.M_Append(sJsonExpected);
	fbBuilder.M_Append(' Actual = ');
	fbBuilder.M_Append(sJsonActual);
	M_Failure(fbBuilder.M_ToString(), Message);
END_IF
M_Equals:= THIS^;
```

---
### `M_Equals_Array_LREAL` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Tolerance` | `LREAL` | Tolerance as lreal |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Equals_Array_LREAL:= THIS^;
M_Assert();
IF LOWER_BOUND(Expected, 1) <> LOWER_BOUND(Actual, 1) THEN
	M_Failure('', Message);
ELSIF UPPER_BOUND(Expected, 1) <> UPPER_BOUND(Actual, 1) THEN
	M_Failure('', Message);
ELSE
	FOR nIndex:= LOWER_BOUND(Expected, 1) TO UPPER_BOUND(Expected, 1) DO
		IF ABS(Expected[nIndex] - Actual[nIndex]) > ABS(Tolerance) THEN	
			fbBuilder.M_Reset();
			fbBuilder.M_Append('Index = [');
			fbBuilder.M_Append(DINT_TO_STRING(nIndex));
			fbBuilder.M_Append('] Expected = ]');
			fbBuilder.M_Append(LREAL_TO_STRING(Expected[nIndex]));
			fbBuilder.M_Append('] Actual = [');
			fbBuilder.M_Append(LREAL_TO_STRING(Actual[nIndex]));
			fbBuilder.M_Append('] Tolerance = ]');
			fbBuilder.M_Append(LREAL_TO_STRING(Tolerance));
			fbBuilder.M_Append(']');
			M_Failure(fbBuilder.M_ToString(), Message);
			RETURN;
		END_IF
	END_FOR
	M_Passed();
END_IF
```

---
### `M_Equals_Array_REAL` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Tolerance` | `REAL` | Tolerance as real |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Equals_Array_REAL:= THIS^;
M_Assert();
IF LOWER_BOUND(Expected, 1) <> LOWER_BOUND(Actual, 1) THEN
	M_Failure('', Message);
ELSIF UPPER_BOUND(Expected, 1) <> UPPER_BOUND(Actual, 1) THEN
	M_Failure('', Message);
ELSE
	FOR nIndex:= LOWER_BOUND(Expected, 1) TO UPPER_BOUND(Expected, 1) DO
		IF ABS(Expected[nIndex] - Actual[nIndex]) > ABS(Tolerance) THEN	
			fbBuilder.M_Reset();
			fbBuilder.M_Append('Index = [');
			fbBuilder.M_Append(DINT_TO_STRING(nIndex));
			fbBuilder.M_Append('] Expected = ]');
			fbBuilder.M_Append(REAL_TO_STRING(Expected[nIndex]));
			fbBuilder.M_Append('] Actual = "');
			fbBuilder.M_Append(REAL_TO_STRING(Actual[nIndex]));
			fbBuilder.M_Append('] Tolerance = [');
			fbBuilder.M_Append(REAL_TO_STRING(Tolerance));
			fbBuilder.M_Append(']');
			M_Failure(fbBuilder.M_ToString(), Message);
			RETURN;
		END_IF
	END_FOR
	M_Passed();
END_IF
```

---
### `M_Equals_BOOL` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Expected` | `BOOL` | Expected as bool |
| `Actual` | `BOOL` | Actual as bool |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();
IF Expected = Actual THEN
	M_Passed();
ELSE
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = [');
	fbBuilder.M_Append(BOOL_TO_STRING(Expected));
	fbBuilder.M_Append('] Actual = [');
	fbBuilder.M_Append(BOOL_TO_STRING(Actual));
	fbBuilder.M_Append(']');
	M_Failure(fbBuilder.M_ToString(), Message);
END_IF
M_Equals_BOOL:= THIS^;
```

---
### `M_Equals_BYTE` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Expected` | `BYTE` | Expected as byte |
| `Actual` | `BYTE` | Actual as byte |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();
IF Expected = Actual THEN
	M_Passed();
ELSE
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = [');
	fbBuilder.M_Append(BYTE_TO_STRING(Expected));
	fbBuilder.M_Append('] Actual = [');
	fbBuilder.M_Append(BYTE_TO_STRING(Actual));
	fbBuilder.M_Append(']');
	M_Failure(fbBuilder.M_ToString(), Message);
END_IF
M_Equals_BYTE:= THIS^;
```

---
### `M_Equals_DINT` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Expected` | `DINT` | Expected as dint |
| `Actual` | `DINT` | Actual as dint |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();
IF Expected = Actual THEN
	M_Passed();
ELSE
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = [');
	fbBuilder.M_Append(DINT_TO_STRING(Expected));
	fbBuilder.M_Append('] Actual = [');
	fbBuilder.M_Append(DINT_TO_STRING(Actual));
	fbBuilder.M_Append(']');
	M_Failure(fbBuilder.M_ToString(), Message);
END_IF
M_Equals_DINT:= THIS^;
```

---
### `M_Equals_INT` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Expected` | `INT` | Expected as int |
| `Actual` | `INT` | Actual as int |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();
IF Expected = Actual THEN
	M_Passed();
ELSE
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = [');
	fbBuilder.M_Append(INT_TO_STRING(Expected));
	fbBuilder.M_Append('] Actual = [');
	fbBuilder.M_Append(INT_TO_STRING(Actual));
	fbBuilder.M_Append(']');
	M_Failure(fbBuilder.M_ToString(), Message);
END_IF
M_Equals_INT:= THIS^;
```

---
### `M_Equals_LINT` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Expected` | `LINT` | Expected as lint |
| `Actual` | `LINT` | Actual as lint |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();
IF Expected = Actual THEN
	M_Passed();
ELSE
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = [');
	fbBuilder.M_Append(LINT_TO_STRING(Expected));
	fbBuilder.M_Append('] Actual = [');
	fbBuilder.M_Append(LINT_TO_STRING(Actual));
	fbBuilder.M_Append(']');
	M_Failure(fbBuilder.M_ToString(), Message);
END_IF
M_Equals_LINT:= THIS^;
```

---
### `M_Equals_LREAL` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Expected` | `LREAL` | Expected as lreal |
| `Actual` | `LREAL` | Actual as lreal |
| `Tolerance` | `LREAL` | Tolerance as lreal |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();
IF LrealIsNaN(Expected) THEN
	M_Failure('', Concat('Expected is NaN', Message));
ELSIF LrealIsNaN(Actual) THEN
	M_Failure('', Concat('Actual is NaN', Message));	
ELSIF LrealIsNaN(Tolerance) THEN
	M_Failure('', Concat('Tolerance is NaN', Message));	
ELSIF ABS(Expected - Actual) <= ABS(Tolerance) THEN
	M_Passed();
ELSE
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = [');
	fbBuilder.M_Append(LREAL_TO_STRING(Expected));
	fbBuilder.M_Append('] Actual = [');
	fbBuilder.M_Append(LREAL_TO_STRING(Actual));
	fbBuilder.M_Append('] Tolerance = [');
	fbBuilder.M_Append(LREAL_TO_STRING(Tolerance));
	fbBuilder.M_Append(']');
	M_Failure(fbBuilder.M_ToString(), Message);
END_IF
M_Equals_LREAL:= THIS^;
```

---
### `M_Equals_REAL` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Expected` | `REAL` | Expected as real |
| `Actual` | `REAL` | Actual as real |
| `Tolerance` | `REAL` | Tolerance as real |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();
IF RealIsNaN(Expected) THEN
	M_Failure('', Concat('Expected is NaN', Message));
ELSIF RealIsNaN(Actual) THEN
	M_Failure('', Concat('Actual is NaN', Message));	
ELSIF RealIsNaN(Tolerance) THEN
	M_Failure('', Concat('Tolerance is NaN', Message));	
ELSIF ABS(Expected - Actual) <= ABS(Tolerance) THEN
	M_Passed();
ELSE
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = [');
	fbBuilder.M_Append(LREAL_TO_STRING(Expected));
	fbBuilder.M_Append('] Actual = [');
	fbBuilder.M_Append(LREAL_TO_STRING(Actual));
	fbBuilder.M_Append('] Tolerance = [');
	fbBuilder.M_Append(LREAL_TO_STRING(Tolerance));
	fbBuilder.M_Append(']');
	M_Failure(fbBuilder.M_ToString(), Message);
END_IF
M_Equals_REAL:= THIS^;
```

---
### `M_Equals_STRING` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Expected` | `STRING` |  |
| `Actual` | `STRING` |  |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();
IF Expected = Actual THEN
	M_Passed();
ELSE
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = [');
	fbBuilder.M_Append(Expected);
	fbBuilder.M_Append('] Actual = [');
	fbBuilder.M_Append(Actual);
	fbBuilder.M_Append(']');
	M_Failure(fbBuilder.M_ToString(), Message);
END_IF
M_Equals_STRING:= THIS^;
```

---
### `M_Equals_TIME` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Expected` | `TIME` | Expected as time |
| `Actual` | `TIME` | Actual as time |
| `Tolerance` | `TIME` | Tolerance as time |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();
IF ABS(Expected - Actual) <= ABS(Tolerance) THEN
	M_Passed();
ELSE
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = [');
	fbBuilder.M_Append(TIME_TO_STRING(Expected));
	fbBuilder.M_Append('] Actual = [');
	fbBuilder.M_Append(TIME_TO_STRING(Actual));
	fbBuilder.M_Append('] Tolerance = [');
	fbBuilder.M_Append(TIME_TO_STRING(Tolerance));
	fbBuilder.M_Append(']');
	M_Failure(fbBuilder.M_ToString(), Message);
END_IF
M_Equals_TIME:= THIS^;
```

---
### `M_Equals_UDINT` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Expected` | `UDINT` | Expected as udint |
| `Actual` | `UDINT` | Actual as udint |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();
IF Expected = Actual THEN
	M_Passed();
ELSE
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = [');
	fbBuilder.M_Append(UDINT_TO_STRING(Expected));
	fbBuilder.M_Append('] Actual = [');
	fbBuilder.M_Append(UDINT_TO_STRING(Actual));
	fbBuilder.M_Append(']');
	M_Failure(fbBuilder.M_ToString(), Message);
END_IF
M_Equals_UDINT:= THIS^;
```

---
### `M_Equals_UINT` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Expected` | `UINT` | Expected as uint |
| `Actual` | `UINT` | Actual as uint |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();
IF Expected = Actual THEN
	M_Passed();
ELSE
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = [');
	fbBuilder.M_Append(UINT_TO_STRING(Expected));
	fbBuilder.M_Append('] Actual = [');
	fbBuilder.M_Append(UINT_TO_STRING(Actual));
	fbBuilder.M_Append(']');
	M_Failure(fbBuilder.M_ToString(), Message);
END_IF
M_Equals_UINT:= THIS^;
```

---
### `M_Equals_ULINT` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Expected` | `ULINT` | Expected as ulint |
| `Actual` | `ULINT` | Actual as ulint |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();
IF Expected = Actual THEN
	M_Passed();
ELSE
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = [');
	fbBuilder.M_Append(ULINT_TO_STRING(Expected));
	fbBuilder.M_Append('] Actual = [');
	fbBuilder.M_Append(ULINT_TO_STRING(Actual));
	fbBuilder.M_Append(']');
	M_Failure(fbBuilder.M_ToString(), Message);
END_IF
M_Equals_ULINT:= THIS^;
```

---
### `M_Equals_UXINT` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Expected` | `UXINT` | Expected as udint |
| `Actual` | `UXINT` | Actual as udint |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();
IF Expected = Actual THEN
	M_Passed();
ELSE
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = [');
	fbBuilder.M_Append(TO_STRING(Expected));
	fbBuilder.M_Append('] Actual = [');
	fbBuilder.M_Append(TO_STRING(Actual));
	fbBuilder.M_Append(']');
	M_Failure(fbBuilder.M_ToString(), Message);
END_IF
M_Equals_UXINT:= THIS^;
```

---
### `M_Equals_WSTRING` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Expected` | `WSTRING` |  |
| `Actual` | `WSTRING` |  |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();
IF Expected = Actual THEN
	M_Passed();
ELSE
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = [');
	fbBuilder.M_Append(WSTRING_TO_STRING(Expected));
	fbBuilder.M_Append('] Actual = [');
	fbBuilder.M_Append(WSTRING_TO_STRING(Actual));
	fbBuilder.M_Append(']');
	M_Failure(fbBuilder.M_ToString(), Message);
END_IF
M_Equals_WSTRING:= THIS^;
```

---
### `M_Equals_XINT` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Expected` | `XINT` | Expected as udint |
| `Actual` | `XINT` | Actual as udint |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();
IF Expected = Actual THEN
	M_Passed();
ELSE
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = [');
	fbBuilder.M_Append(TO_STRING(Expected));
	fbBuilder.M_Append('] Actual = [');
	fbBuilder.M_Append(TO_STRING(Actual));
	fbBuilder.M_Append(']');
	M_Failure(fbBuilder.M_ToString(), Message);
END_IF
M_Equals_XINT:= THIS^;
```

---
### `M_Equals_XWORD` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Expected` | `XWORD` | Expected as udint |
| `Actual` | `XWORD` | Actual as udint |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();
IF Expected = Actual THEN
	M_Passed();
ELSE
	fbBuilder.M_Reset();
	fbBuilder.M_Append('Expected = [');
	fbBuilder.M_Append(TO_STRING(Expected));
	fbBuilder.M_Append('] Actual = [');
	fbBuilder.M_Append(TO_STRING(Actual));
	fbBuilder.M_Append(']');
	M_Failure(fbBuilder.M_ToString(), Message);
END_IF
M_Equals_XWORD:= THIS^;
```

---
### `M_Error` : `STRING`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Data` | `STRING` |  |
| `Message` | `STRING` |  |

**Implementation:**
```iec
IF nSkipped = 0 THEN
	fbBuilder.M_Reset();
	fbBuilder.M_Append('$T$T$T<error message="');
	fbBuilder.M_Append(Message);
	fbBuilder.M_Append('" type="ArithmeticError">');
	fbBuilder.M_Append(Data);	
	fbBuilder.M_Append('</error>');
	fbList.M_Add(fbBuilder.M_ToString());
	nErrors:= nErrors + 1;
END_IF
```

---
### `M_Failure` : `STRING`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Data` | `STRING` |  |
| `Message` | `STRING` |  |

**Implementation:**
```iec
IF nSkipped = 0 THEN
	fbBuilder.M_Reset();
	fbBuilder.M_Append('$T$T$T<failure message="');
	fbBuilder.M_Append(Message);
	fbBuilder.M_Append('" type="AssertionError">');
	fbBuilder.M_Append(Data);
	fbBuilder.M_Append('</failure>');
	fbList.M_Add(fbBuilder.M_ToString());
	nFailures:= nFailures + 1;
END_IF
```

---
### `M_IsTRUE` : `I_Assert`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Actual` | `BOOL` | Actual as bool |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Assert();
IF Actual THEN
	M_Passed();
ELSE
	M_Failure('Actual = "FALSE"', Message);
END_IF
M_IsTRUE:= THIS^;
```

---
### `M_Passed`
*No documentation found.*

**Implementation:**
```iec
IF nSkipped = 0 THEN
	nPassed:= nPassed + 1;
END_IF
```

---
### `M_Reset` : `I_Assert`
*No documentation found.*

**Implementation:**
```iec
fbList.M_Clear();
nAssert:= 0;
nPassed:= 0;
nSkipped:= 0;
nFailures:= 0;
nErrors:= 0;
M_Reset:= THIS^;
```

---
### `M_Skip` : `STRING`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Message` | `STRING` |  |

**Implementation:**
```iec
fbList.M_Clear();
nAssert:= 0;
nPassed:= 0;
nFailures:= 0;
nErrors:= 0;
fbBuilder.M_Reset();
fbBuilder.M_Append('$T$T$T<skipped message="');
fbBuilder.M_Append(Message);
fbBuilder.M_Append('" />');
fbList.M_Add(fbBuilder.M_ToString());
nSkipped:= nSkipped + 1;
```

---

## Implementation
```iec
// https://peterzerlauth.com/
```
