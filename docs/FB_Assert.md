## Function Block: FB_Assert

### Description
The `FB_Assert` function block provides assertion capabilities for verifying expected values against actual values during runtime. It aids in automated testing and debugging processes by detecting discrepancies between expected and actual values.

### Inputs
- **None**

### Outputs
- **fbList:** A list of assertion results in string format.
- **nAssert:** Number of assertions executed.
- **nPassed:** Number of assertions passed.
- **nSkipped:** Number of assertions skipped.
- **nFailures:** Number of assertion failures.
- **nErrors:** Number of errors encountered during assertion execution.

### Methods
1. **M_Assert**: Increments the assertion counter (`nAssert`) when executed.
2. **M_Equals**: Compares two values of any data type (`Expected` and `Actual`) and logs a failure if they are not equal. Supports various data types including integers, floating-point numbers, strings, and arrays.
3. **M_Equals_ANY_Old**: Compares two values of any data type (`Expected` and `Actual`) and logs a failure if they are not equal. Deprecated in favor of the more versatile `M_Equals` method.
4. **M_Equals_Array_BOOL**: Compares two arrays of boolean values (`Expected` and `Actual`) and logs a failure if any elements differ.
5. **M_Equals_Array_BYTE**: Compares two arrays of byte values (`Expected` and `Actual`) and logs a failure if any elements differ.
6. **M_Equals_Array_DINT**: Compares two arrays of DINT values (`Expected` and `Actual`) and logs a failure if any elements differ.
7. **M_Equals_Array_INT**: Compares two arrays of INT values (`Expected` and `Actual`) and logs a failure if any elements differ.
8. **M_Equals_Array_LINT**: Compares two arrays of LINT values (`Expected` and `Actual`) and logs a failure if any elements differ.
9. **M_Equals_Array_LREAL**: Compares two arrays of LREAL values (`Expected` and `Actual`) within a specified tolerance and logs a failure if any elements differ outside the tolerance.
10. **M_Equals_Array_REAL**: Compares two arrays of REAL values (`Expected` and `Actual`) within a specified tolerance and logs a failure if any elements differ outside the tolerance.
11. **M_Equals_BOOL**: Compares two boolean values (`Expected` and `Actual`) and logs a failure if they are not equal.
12. **M_Equals_BYTE**: Compares two byte values (`Expected` and `Actual`) and logs a failure if they are not equal.
13. **M_Equals_DINT**: Compares two DINT values (`Expected` and `Actual`) and logs a failure if they are not equal.
14. **M_Equals_INT**: Compares two INT values (`Expected` and `Actual`) and logs a failure if they are not equal.
15. **M_Equals_LINT**: Compares two LINT values (`Expected` and `Actual`) and logs a failure if they are not equal.
16. **M_Equals_LREAL**: Compares two LREAL values (`Expected` and `Actual`) within a specified tolerance and logs a failure if they are not within the tolerance.
17. **M_Equals_REAL**: Compares two REAL values (`Expected` and `Actual`) within a specified tolerance and logs a failure if they are not within the tolerance.
18. **M_Equals_STRING**: Compares two string values (`Expected` and `Actual`) and logs a failure if they are not equal.
19. **M_Equals_TIME**: Compares two TIME values (`Expected` and `Actual`) within a specified tolerance and logs a failure if they are not within the tolerance.
20. **M_Equals_UDINT**: Compares two UDINT values (`Expected` and `Actual`) and logs a failure if they are not equal.
21. **M_Equals_UINT**: Compares two UINT values (`Expected` and `Actual`) and logs a failure if they are not equal.
22. **M_Equals_ULINT**: Compares two ULINT values (`Expected` and `Actual`) and logs a failure if they are not equal.
23. **M_Equals_UXINT**: Compares two UXINT values (`Expected` and `Actual`) and logs a failure if they are not equal.

### Usage
- Instantiate the `FB_Assert` function block in your TwinCAT 3 project.
- Call the appropriate method to perform the desired assertion.
- Check the output variables to determine the assertion results.
- Integrate assertions into your automated testing or debugging processes to ensure code correctness.
