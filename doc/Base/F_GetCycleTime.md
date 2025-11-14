# F_GetCycleTime

**Type:** `FUNCTION`
**Source File:** `Base/F_GetCycleTime.TcPOU`

*No documentation found.*

**Returns:** `LREAL`

## Implementation
```iec
// https://peterzerlauth.com/
fbTask();
F_GetCycleTime:= UDINT_TO_LREAL(TwinCAT_SystemInfoVarList._TaskInfo[fbTask.index].CycleTime) / 10000000;
```
