# E_Base

**Type:** `ENUM`
**Source File:** `Base/E_Base.TcDUT`

*No documentation found.*

## Declaration
```iec
{attribute 'qualified_only'}
{attribute 'strict'}
TYPE E_Base :
(
	{attribute 'hide'} 
	Init 	:= 0,
	Starting:= 2,	
	Execute	:= 3,
	Stopping:= 4,
	Aborting:= 5,
	Aborted	:= 6,
	Reset	:= 7,
	Stopped	:= 1
)USINT;
END_TYPE
```
