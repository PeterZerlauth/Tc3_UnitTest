
# ![check](https://user-images.githubusercontent.com/48495545/228613908-fd86b481-6052-455c-8fd1-57020d1d3b8a.svg) Tc3_UnitTest.library
Unit test Twincat 3, 
a easy to use unit testing framework
Outputs will be stored in standard JUNIT xml file format

- Lightweight
- Repeatable
- Easy to use
- Remote start
- CI/CD pipeline supported
- Small devices supported
- Test and build tool (https://github.com/PeterZerlauth/TcBuild for self hosted agent)

### Example 1
```ST    
// Run
fbTestsuites();

IF bExecute THEN
	fbTestsuites.P_Options.sFilePathName:= 'C:\test\report.xml';
	bExecute:= NOT fbTestsuites.M_Request(E_Base.Execute);
END_IF

// Add Testsuite to Testsuites
fbTestsuites.M_Add(fbTestsuite1);
{region "fbTestsuite1"}
// Run
fbTestsuite1();
CASE fbTestsuite1.P_Testcase OF
	E_Testcase.Start:
		// First test case
		fbBuilder.M_Reset().M_Append('Test').M_ToAny(sValue);
		fbTestsuite1.P_Assert.M_IsTRUE(sValue = 'Test', 'FB_StringBuilder.M_Append()');
		fbTestsuite1.M_Testcase('FB_StringBuilder', T#1S, '', '', E_Testcase.Done);	
	E_Testcase.Done:;
	
END_CASE
```

### Example 2
![grafik](https://github.com/PeterZerlauth/Testing/assets/48495545/a5aa2a5a-661d-4e27-8b67-21b07b98972c)

### Resutls
xml format from https://github.com/testmoapp/junitxml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<testsuites name="fbTestsuites" tests="24" failures="0" errors="0" skipped="0" assertions="33" time="0.300" timestamp="2024-03-15T12:44:54.735">
	<properties>
		<property name="Version" value="1.0.0.3" />
	</properties>
	<testsuite name="fbTestsuite4" tests="3" failures="0" errors="0" skipped="0" assertions="3" time="0.020" timestamp="2024-03-15T12:44:54.775" file="">
		<testcase name="fbTestsuite4.M_Testcase_0" classname="FB_Assert" assertions="1" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite4.M_Testcase_1" classname="FB_Assert" assertions="1" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite4.M_Testcase_2" classname="FB_Assert" assertions="1" time="0.0100" file="" line="" />
	</testsuite>
	<testsuite name="fbTestsuite2" tests="4" failures="0" errors="0" skipped="0" assertions="8" time="0.030" timestamp="2024-03-15T12:44:54.775" file="">
		<testcase name="fbTestsuite2.M_Testcase_0" classname="FB_ListSTRING" assertions="3" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite2.M_Testcase_1" classname="FB_ListSTRING" assertions="1" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite2.M_Testcase_2" classname="FB_ListSTRING" assertions="3" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite2.M_Testcase_3" classname="FB_ListSTRING" assertions="1" time="0.0100" file="" line="" />
	</testsuite>
	<testsuite name="fbTestsuite1" tests="9" failures="0" errors="0" skipped="0" assertions="14" time="0.080" timestamp="2024-03-15T12:44:54.775" file="FB_StringBuilder">
		<properties>
			<property name="Property1" value="Value1" />
			<property name="Property2" value="Value2" />
		</properties>
		<testcase name="fbTestsuite1.M_Testcase_0" classname="FB_StringBuilder" assertions="1" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite1.M_Testcase_1" classname="FB_StringBuilder" assertions="2" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite1.M_Testcase_2" classname="FB_StringBuilder" assertions="2" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite1.M_Testcase_3" classname="FB_StringBuilder" assertions="2" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite1.M_Testcase_4" classname="FB_StringBuilder" assertions="2" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite1.M_Testcase_5" classname="FB_StringBuilder" assertions="2" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite1.M_Testcase_6" classname="FB_StringBuilder" assertions="1" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite1.M_Testcase_7" classname="FB_StringBuilder" assertions="1" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite1.M_Testcase_8" classname="FB_StringBuilder" assertions="1" time="0.0100" file="" line="" />
	</testsuite>
	<testsuite name="fbTestsuite3" tests="8" failures="0" errors="0" skipped="0" assertions="8" time="0.250" timestamp="2024-03-15T12:44:54.775" file="">
		<testcase name="fbTestsuite3.M_Testcase_0" classname="FB_File" assertions="1" time="0.0300" file="" line="" />
		<testcase name="fbTestsuite3.M_Testcase_1" classname="FB_File" assertions="1" time="0.0600" file="" line="" />
		<testcase name="fbTestsuite3.M_Testcase_2" classname="FB_File" assertions="1" time="0.0300" file="" line="" />
		<testcase name="fbTestsuite3.M_Testcase_3" classname="FB_File" assertions="1" time="0.0300" file="" line="" />
		<testcase name="fbTestsuite3.M_Testcase_4" classname="FB_File" assertions="1" time="0.0500" file="" line="" />
		<testcase name="fbTestsuite3.M_Testcase_5" classname="FB_File" assertions="1" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite3.M_Testcase_6" classname="FB_File" assertions="1" time="0.0200" file="" line="" />
		<testcase name="fbTestsuite3.M_Testcase_7" classname="FB_File" assertions="1" time="0.0300" file="" line="" />
	</testsuite>
</testsuites>
```

![grafik](https://github.com/PeterZerlauth/Testing/assets/48495545/e5bd0a1f-5c42-4650-aa56-1a0818cb9795)

