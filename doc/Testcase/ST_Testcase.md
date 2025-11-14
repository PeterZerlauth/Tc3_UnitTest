# ST_Testcase

**Type:** `STRUCT`
**Source File:** `Testcase/ST_Testcase.TcDUT`

*No documentation found.*

## Declaration
```iec
TYPE ST_Testcase :
STRUCT
	sName:				STRING(255);	//	name        The name of this test case, often the method name  
	sClassname:			STRING(255);	//	classname   The name of the parent class/folder, often the same as the suite's name
	nAssertions:		DINT; 			//	assertions  Number of assertions checked during test case execution  
	fTime:				LREAL;			//	time        Execution time of the test in seconds            
	sFile:				STRING(255);	//	file        Source code file of this test case              
	sLine:				STRING(255);	//	line        Source code line number of the start of this test case  
END_STRUCT
END_TYPE
```
