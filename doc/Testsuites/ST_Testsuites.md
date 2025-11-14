# ST_Testsuites

**Type:** `STRUCT`
**Source File:** `Testsuites/ST_Testsuites.TcDUT`

*No documentation found.*

## Declaration
```iec
TYPE ST_Testsuites :
STRUCT
	sName:				STRING(255); 				// Name OF the entire test run
	nTests:				DINT;						// Total number of tests in this file
	nFailures:			dINT;						// Total number of failed tests in this file
	nErrors:			dINT;						// Total number of errored tests in this file
	nSkipped:			dINT;						// Total number of skipped tests in this file
	nAssertions:		dINT;						// Total number of assertions for all tests in this file
	fTime:				LREAL;						// Aggregated time of all tests in this file in seconds
	sTimestamp:			STRING(39);					// timestamp   Date and time of when the test suite was executed (in ISO 8601 format)
END_STRUCT
END_TYPE
```
