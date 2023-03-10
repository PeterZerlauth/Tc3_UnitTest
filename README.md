# TcTesting
Twincat 3 unit testing

Start with my own simplified unit test lib

* FB_Assert => done;
* FB_Testsuite => done
* FB_Testsuite => done
* Junit Xml format => done
* Twincat error to Testcase => open


![grafik](https://user-images.githubusercontent.com/48495545/221642520-067dda53-0e73-40f4-b141-c089c395d0a3.png)



Example Test result:

<testsuites name="fbTestsuites" tests="19" failures="3" errors="0" skipped="0" assertions="28" time="1.060" timestamp="2023-03-10T14:15:02.191">
<testsuite name="fbTestsuite2" tests="4" failures="0" errors="0" skipped="0" assertions="8" time="0.040" timestamp="2023-03-10T14:15:02.231" file="">
<testcase name="fbTestsuite2.M_Testcase_0" classname="FB_ListSTRING" assertions="3" time="0.0100" file="" line=""/>
<testcase name="fbTestsuite2.M_Testcase_1" classname="FB_ListSTRING" assertions="1" time="0.0100" file="" line=""/>
<testcase name="fbTestsuite2.M_Testcase_2" classname="FB_ListSTRING" assertions="3" time="0.0100" file="" line=""/>
<testcase name="fbTestsuite2.M_Testcase_3" classname="FB_ListSTRING" assertions="1" time="0.0100" file="" line=""/>
</testsuite>
<testsuite name="fbTestsuite1" tests="8" failures="0" errors="0" skipped="0" assertions="13" time="0.080" timestamp="2023-03-10T14:15:02.231" file="">
<testcase name="fbTestsuite1.M_Testcase_0" classname="FB_StringBuilder" assertions="1" time="0.0100" file="" line=""/>
<testcase name="fbTestsuite1.M_Testcase_1" classname="FB_StringBuilder" assertions="2" time="0.0100" file="" line=""/>
<testcase name="fbTestsuite1.M_Testcase_2" classname="FB_StringBuilder" assertions="2" time="0.0100" file="" line=""/>
<testcase name="fbTestsuite1.M_Testcase_3" classname="FB_StringBuilder" assertions="2" time="0.0100" file="" line=""/>
<testcase name="fbTestsuite1.M_Testcase_4" classname="FB_StringBuilder" assertions="2" time="0.0100" file="" line=""/>
<testcase name="fbTestsuite1.M_Testcase_5" classname="FB_StringBuilder" assertions="2" time="0.0100" file="" line=""/>
<testcase name="fbTestsuite1.M_Testcase_6" classname="FB_StringBuilder" assertions="1" time="0.0100" file="" line=""/>
<testcase name="fbTestsuite1.M_Testcase_7" classname="FB_StringBuilder" assertions="1" time="0.0100" file="" line=""/>
</testsuite>
<testsuite name="fbTestsuite3" tests="7" failures="3" errors="0" skipped="0" assertions="7" time="1.000" timestamp="2023-03-10T14:15:02.231" file="">
<testcase name="fbTestsuite3.M_Testcase_0" classname="fbFile" assertions="1" time="0.0600" file="" line=""/>
<testcase name="fbTestsuite3.M_Testcase_1" classname="fbFile" assertions="1" time="0.0300" file="" line=""/>
<testcase name="fbTestsuite3.M_Testcase_2" classname="fbFile" assertions="1" time="0.0300" file="" line=""/>
<testcase name="fbTestsuite3.M_Testcase_3" classname="fbFile" assertions="1" time="0.0500" file="" line=""/>
<testcase name="fbTestsuite3.M_Testcase_4" classname="fbFile" assertions="1" time="0.8300" file="" line="">
<failure message="File content" type="AssertionError">Expected = "TestString" Actual = "TestString TestString "</failure>
</testcase>
<testcase name="fbTestsuite3.M_Testcase_5" classname="fbFile" assertions="1" time="0.0100" file="" line="">
<failure message="fbFile.M_Close()" type="AssertionError"> Expected = "TRUE" Actual = "FALSE</failure>
</testcase>
<testcase name="fbTestsuite3.M_Testcase_6" classname="fbFile" assertions="1" time="0.0100" file="" line="">
<failure message="fbFile.M_Delete()" type="AssertionError"> Expected = "TRUE" Actual = "FALSE</failure>
</testcase>
</testsuite>
</testsuites>
