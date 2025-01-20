
# Tc3_UnitTest
![Tc3_UnitTest](https://github.com/user-attachments/assets/8ab612b7-68f3-472e-9218-c5f387c51c5c)
.library
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
```st    
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

## Self Test Result
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

## Example Test Result
```xml
<?xml version="1.0" encoding="UTF-8"?>
<testsuites name="fbTestsuites" tests="51" failures="0" errors="0" skipped="0" assertions="65" time="0.027" timestamp="2024-10-11T12:25:55.551">
	<testsuite name="fbListObject.fbTestsuite" tests="11" failures="0" errors="0" skipped="0" assertions="11" time="0.010" timestamp="2024-10-11T12:25:55.556" file="">
		<properties>
			<property name="object" value="FB_ListObject" />
			<property name="name" value="Peter Zerlauth" />
		</properties>
		<testcase name="fbListObject.fbTestsuite.M_Testcase_0" classname="FB_ListObject" assertions="1" time="0.0010" file="fbList.P_Length" line="" />
		<testcase name="fbListObject.fbTestsuite.M_Testcase_10" classname="FB_ListObject" assertions="1" time="0.0010" file="fbList.M_Add(fbObject)" line="" />
		<testcase name="fbListObject.fbTestsuite.M_Testcase_20" classname="FB_ListObject" assertions="1" time="0.0010" file="fbList.P_Length" line="" />
		<testcase name="fbListObject.fbTestsuite.M_Testcase_30" classname="FB_ListObject" assertions="1" time="0.0010" file="fbList.M_Find(fbObject)" line="" />
		<testcase name="fbListObject.fbTestsuite.M_Testcase_40" classname="FB_ListObject" assertions="1" time="0.0010" file="fbList.M_Index(1)" line="" />
		<testcase name="fbListObject.fbTestsuite.M_Testcase_50" classname="FB_ListObject" assertions="1" time="0.0010" file="fbList.M_Remove(fbObject" line="" />
		<testcase name="fbListObject.fbTestsuite.M_Testcase_60" classname="FB_ListObject" assertions="1" time="0.0010" file="fbList.P_Length" line="" />
		<testcase name="fbListObject.fbTestsuite.M_Testcase_70" classname="FB_ListObject" assertions="1" time="0.0010" file="fbList.M_Add(fbObject)" line="" />
		<testcase name="fbListObject.fbTestsuite.M_Testcase_80" classname="FB_ListObject" assertions="1" time="0.0010" file="fbList.P_Length" line="" />
		<testcase name="fbListObject.fbTestsuite.M_Testcase_90" classname="FB_ListObject" assertions="1" time="0.0010" file="fbList.M_Clear()" line="" />
		<testcase name="fbListObject.fbTestsuite.M_Testcase_100" classname="FB_ListObject" assertions="1" time="0.0010" file="fbList.P_Length" line="" />
	</testsuite>
	<testsuite name="fbListComponent.fbTestsuite" tests="11" failures="0" errors="0" skipped="0" assertions="11" time="0.010" timestamp="2024-10-11T12:25:55.556" file="">
		<properties>
			<property name="object" value="FB_ListComponent" />
			<property name="name" value="Peter Zerlauth" />
		</properties>
		<testcase name="fbListComponent.fbTestsuite.M_Testcase_0" classname="FB_ListComponent" assertions="1" time="0.0010" file="fbList.P_Length" line="" />
		<testcase name="fbListComponent.fbTestsuite.M_Testcase_10" classname="FB_ListComponent" assertions="1" time="0.0010" file="fbList.M_Add(fbObject)" line="" />
		<testcase name="fbListComponent.fbTestsuite.M_Testcase_20" classname="FB_ListComponent" assertions="1" time="0.0010" file="fbList.P_Length" line="" />
		<testcase name="fbListComponent.fbTestsuite.M_Testcase_30" classname="FB_ListComponent" assertions="1" time="0.0010" file="fbList.M_Find(fbObject)" line="" />
		<testcase name="fbListComponent.fbTestsuite.M_Testcase_40" classname="FB_ListComponent" assertions="1" time="0.0010" file="fbList.M_Index(1)" line="" />
		<testcase name="fbListComponent.fbTestsuite.M_Testcase_50" classname="FB_ListComponent" assertions="1" time="0.0010" file="fbList.M_Remove(fbObject" line="" />
		<testcase name="fbListComponent.fbTestsuite.M_Testcase_60" classname="FB_ListComponent" assertions="1" time="0.0010" file="fbList.P_Length" line="" />
		<testcase name="fbListComponent.fbTestsuite.M_Testcase_70" classname="FB_ListComponent" assertions="1" time="0.0010" file="fbList.M_Add(fbObject)" line="" />
		<testcase name="fbListComponent.fbTestsuite.M_Testcase_80" classname="FB_ListComponent" assertions="1" time="0.0010" file="fbList.P_Length" line="" />
		<testcase name="fbListComponent.fbTestsuite.M_Testcase_90" classname="FB_ListComponent" assertions="1" time="0.0010" file="fbList.M_Clear()" line="" />
		<testcase name="fbListComponent.fbTestsuite.M_Testcase_100" classname="FB_ListComponent" assertions="1" time="0.0010" file="fbList.P_Length" line="" />
	</testsuite>
	<testsuite name="fbListString.fbTestsuite" tests="13" failures="0" errors="0" skipped="0" assertions="13" time="0.012" timestamp="2024-10-11T12:25:55.556" file="">
		<properties>
			<property name="object" value="FB_ListString" />
			<property name="name" value="Peter Zerlauth" />
		</properties>
		<testcase name="fbListString.fbTestsuite.M_Testcase_0" classname="FB_ListString" assertions="1" time="0.0010" file="fbList.P_Length" line="" />
		<testcase name="fbListString.fbTestsuite.M_Testcase_10" classname="FB_ListString" assertions="1" time="0.0010" file="fbList.M_Add(test)" line="" />
		<testcase name="fbListString.fbTestsuite.M_Testcase_20" classname="FB_ListString" assertions="1" time="0.0010" file="fbList.P_Length" line="" />
		<testcase name="fbListString.fbTestsuite.M_Testcase_30" classname="FB_ListString" assertions="1" time="0.0010" file="fbList.M_Find(test)" line="" />
		<testcase name="fbListString.fbTestsuite.M_Testcase_40" classname="FB_ListString" assertions="1" time="0.0010" file="fbList.M_Index(1)" line="" />
		<testcase name="fbListString.fbTestsuite.M_Testcase_50" classname="FB_ListString" assertions="1" time="0.0010" file="fbList.M_Remove(fbObject" line="" />
		<testcase name="fbListString.fbTestsuite.M_Testcase_60" classname="FB_ListString" assertions="1" time="0.0010" file="fbList.P_Length" line="" />
		<testcase name="fbListString.fbTestsuite.M_Testcase_70" classname="FB_ListString" assertions="1" time="0.0010" file="fbList.M_Add(test)" line="" />
		<testcase name="fbListString.fbTestsuite.M_Testcase_80" classname="FB_ListString" assertions="1" time="0.0010" file="fbList.P_Length" line="" />
		<testcase name="fbListString.fbTestsuite.M_Testcase_90" classname="FB_ListString" assertions="1" time="0.0010" file="fbList.M_Clear()" line="" />
		<testcase name="fbListString.fbTestsuite.M_Testcase_100" classname="FB_ListString" assertions="1" time="0.0010" file="fbList.P_Length" line="" />
		<testcase name="fbListString.fbTestsuite.M_Testcase_110" classname="FB_ListString" assertions="1" time="0.0010" file="fbList.M_Add(test)" line="" />
		<testcase name="fbListString.fbTestsuite.M_Testcase_120" classname="FB_ListString" assertions="1" time="0.0010" file="fbList.P_Length" line="" />
	</testsuite>
	<testsuite name="fbMembers.fbTestsuite" tests="8" failures="0" errors="0" skipped="0" assertions="16" time="0.019" timestamp="2024-10-11T12:25:55.556" file="">
		<properties>
			<property name="object" value="FB_Members" />
			<property name="name" value="Peter Zerlauth" />
		</properties>
		<testcase name="fbMembers.fbTestsuite.M_Testcase_0" classname="FB_Members" assertions="1" time="0.0010" file="fbList.P_Length" line="" />
		<testcase name="fbMembers.fbTestsuite.M_Testcase_10" classname="FB_Members" assertions="3" time="0.0010" file="fbList.M_Add(fbObject)" line="" />
		<testcase name="fbMembers.fbTestsuite.M_Testcase_20" classname="FB_Members" assertions="2" time="0.0030" file="fbList.M_Start()" line="" />
		<testcase name="fbMembers.fbTestsuite.M_Testcase_30" classname="FB_Members" assertions="2" time="0.0030" file="fbList.M_Stop()" line="" />
		<testcase name="fbMembers.fbTestsuite.M_Testcase_40" classname="FB_Members" assertions="2" time="0.0030" file="fbList.M_Reset()" line="" />
		<testcase name="fbMembers.fbTestsuite.M_Testcase_50" classname="FB_Members" assertions="2" time="0.0030" file="fbList.M_Start()" line="" />
		<testcase name="fbMembers.fbTestsuite.M_Testcase_60" classname="FB_Members" assertions="2" time="0.0030" file="fbList.M_Abort()" line="" />
		<testcase name="fbMembers.fbTestsuite.M_Testcase_70" classname="FB_Members" assertions="2" time="0.0030" file="fbList.M_Reset()" line="" />
	</testsuite>
	<testsuite name="fbComponentTests.fbTestsuite" tests="8" failures="0" errors="0" skipped="0" assertions="14" time="0.021" timestamp="2024-10-11T12:25:55.556" file="">
		<properties>
			<property name="object" value="FB_Component" />
			<property name="name" value="Peter Zerlauth" />
		</properties>
		<testcase name="fbComponentTests.fbTestsuite.M_Testcase_0" classname="FB_Component" assertions="1" time="0.0010" file="fbComponent.M_Request(E_Request.Reset)" line="" />
		<testcase name="fbComponentTests.fbTestsuite.M_Testcase_10" classname="FB_Component" assertions="2" time="0.0030" file="fbComponent.M_Request(E_Request.Reset)" line="" />
		<testcase name="fbComponentTests.fbTestsuite.M_Testcase_20" classname="FB_Component" assertions="2" time="0.0030" file="fbComponent.M_Request(E_Request.Abort)" line="" />
		<testcase name="fbComponentTests.fbTestsuite.M_Testcase_30" classname="FB_Component" assertions="2" time="0.0030" file="fbComponent.M_Request(E_Request.Reset)" line="" />
		<testcase name="fbComponentTests.fbTestsuite.M_Testcase_40" classname="FB_Component" assertions="2" time="0.0030" file="fbComponent.M_Request(E_Request.Reset)" line="" />
		<testcase name="fbComponentTests.fbTestsuite.M_Testcase_50" classname="FB_Component" assertions="2" time="0.0030" file="fbComponent.M_Request(E_Request.Stop)" line="" />
		<testcase name="fbComponentTests.fbTestsuite.M_Testcase_60" classname="FB_Component" assertions="2" time="0.0030" file="fbComponent.M_Request(E_Request.Reset)" line="" />
		<testcase name="fbComponentTests.fbTestsuite.M_Testcase_70" classname="FB_Component" assertions="1" time="0.0030" file="fbComponent.P_Event.M_Abort(Abort, 1)" line="" />
	</testsuite>
</testsuites>
```

![grafik](https://github.com/PeterZerlauth/Testing/assets/48495545/e5bd0a1f-5c42-4650-aa56-1a0818cb9795)



