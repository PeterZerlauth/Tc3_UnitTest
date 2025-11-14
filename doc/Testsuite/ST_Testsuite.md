# ST_Testsuite

**Type:** `STRUCT`
**Source File:** `Testsuite/ST_Testsuite.TcDUT`

*No documentation found.*

## Declaration
```iec
TYPE ST_Testsuite :
STRUCT
	sName:				STRING(255):= 'testsuite'; 	// Name OF the entire test run
	nTests:				DINT;						// tests       Total number of tests in this suite          
	nFailures:			DINT;						// failures    Total number of failed tests in this suite   
	nErrors:			DINT;						// errors      Total number of errored tests in this suite 
	nSkipped:			DINT;						// skipped     Total number of skipped tests in this suite            
	nAssertions:		DINT;						// assertions  Total number of assertions for all tests in this suite  
	fTime: 				LREAL;						// time        Aggregated time of all tests in this file in seconds  (100ns)   
	sTimestamp:			STRING(39);					// timestamp   Date and time of when the test suite was executed (in ISO 8601 format)  
	sFile:				STRING(255);				// file        Source code file of this test suite
END_STRUCT
END_TYPE
```
