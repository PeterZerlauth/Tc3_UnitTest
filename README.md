# Tc3_Testing.library
Unit testing Twincat 3
A easy to use unit testing framework
Outputs will be stored in standard JUNIT xml file format


### Docs
https://peterzerlauth.github.io/Testing/

### Example
```pascal
// Run
fbTestsuites();

IF bExecute THEN
	fbTestsuites.P_FilePathName:= 'C:\test\report.xml';
	bExecute:= NOT fbTestsuites.M_Request(E_Base.Execute);
END_IF

//// Add Testsuite to Testsuites
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

### Resutls
xml format from https://github.com/testmoapp/junitxml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<testsuites name="fbTestsuites" tests="21" failures="0" errors="0" skipped="0" assertions="30" time="0.300" timestamp="2023-03-24T22:37:21.777">
	<testsuite name="fbTestsuite2" tests="4" failures="0" errors="0" skipped="0" assertions="8" time="0.030" timestamp="2023-03-24T22:37:21.817" file="">
		<testcase name="fbTestsuite2.M_Testcase_0" classname="FB_ListSTRING" assertions="3" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite2.M_Testcase_1" classname="FB_ListSTRING" assertions="1" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite2.M_Testcase_2" classname="FB_ListSTRING" assertions="3" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite2.M_Testcase_3" classname="FB_ListSTRING" assertions="1" time="0.0100" file="" line="" />
	</testsuite>
	<testsuite name="fbTestsuite1" tests="9" failures="0" errors="0" skipped="0" assertions="14" time="0.080" timestamp="2023-03-24T22:37:21.817" file="">
		<testcase name="fbTestsuite1.M_Testcase_0" classname="FB_StringBuilder" assertions="1" time="0.0100" file="" line="__POSITION()" />
		<testcase name="fbTestsuite1.M_Testcase_1" classname="FB_StringBuilder" assertions="2" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite1.M_Testcase_2" classname="FB_StringBuilder" assertions="2" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite1.M_Testcase_3" classname="FB_StringBuilder" assertions="2" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite1.M_Testcase_4" classname="FB_StringBuilder" assertions="2" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite1.M_Testcase_5" classname="FB_StringBuilder" assertions="2" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite1.M_Testcase_6" classname="FB_StringBuilder" assertions="1" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite1.M_Testcase_7" classname="FB_StringBuilder" assertions="1" time="0.0100" file="" line="" />
		<testcase name="fbTestsuite1.M_Testcase_8" classname="FB_StringBuilder" assertions="1" time="0.0100" file="" line="" />
	</testsuite>
	<testsuite name="fbTestsuite3" tests="8" failures="0" errors="0" skipped="0" assertions="8" time="0.250" timestamp="2023-03-24T22:37:21.817" file="">
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


<a href="https://www.buymeacoffee.com/9wjvwz24g6b"><img src="https://img.buymeacoffee.com/button-api/?text=Buy me a beer&emoji=🍺&slug=9wjvwz24g6b&button_colour=5F7FFF&font_colour=ffffff&font_family=Cookie&outline_colour=000000&coffee_colour=FFDD00" /></a>



Shield: [![CC BY-NC-SA 4.0][cc-by-nc-sa-shield]][cc-by-nc-sa]

This work is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg
