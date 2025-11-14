# F_GetName

**Type:** `FUNCTION`
**Source File:** `Base/F_GetName.TcPOU`

*No documentation found.*

**Returns:** `STRING`

## Inputs
| Name | Type | Description |
| --- | --- | --- |
| `InstancePath` | `STRING` |  |

## Local Variables
| Name | Type | Description |
| --- | --- | --- |
| `InstancePath` | `STRING` |  |

## Implementation
```iec
// https://peterzerlauth.com/
sName := CONCAT(TwinCAT_SystemInfoVarList._AppInfo.ProjectName, '.');

nPosition := FIND(InstancePath, sName);

IF nPosition > 0 THEN
    F_GetName:= DELETE(InstancePath, nPosition-1 + LEN(sName), 1);
END_IF

nPosition := FIND(F_GetName, sName);

IF nPosition > 0 THEN
    F_GetName:= DELETE(F_GetName, nPosition - 1 + LEN(sName), 1);
END_IF

nPosition:= FIND(STR1 := F_GetName, '.');
F_GetName:= RIGHT(STR := F_GetName, LEN(STR := F_GetName) - nPosition);
```
