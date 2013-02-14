vstest.teamcity.logger
======================

VSTest logger for TeamCity


Why
--
Visual Studio 2012 gives you Fakes & Shims. Unfortunately you must use *vstest.console.exe* 
to run these tests in TeamCity (or *ShimsNotSupportedException* will be thrown in your face) [3]. 
This means no more "Test" tab in build results. __Unles__ you use this logger.

Logger is attached to vstest.console.exe to print output in format required by TeamCity[2]. 
I can't promise antyhing. For me _it just works (I hope)_.


How
--

From Vikram Agrawal blog entry [1]:

There are two requirements for custom test logger

> 1. Implement interface Microsoft.VisualStudio.TestPlatform.ObjectModel.Client.ITestLogger
>		Interface can be found in __“C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CommonExtensions\Microsoft\TestWindow\Microsoft.VisualStudio.TestPlatform.ObjectModel.dll”__
>
> 2. Assembly containing logger implementation to be present in place where extensions are searched like __"C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CommonExtensions\Microsoft\TestWindow\Extensions"__
>		Assembly can be installed with VSIX like test adapters. In that case use /UseVSIXExtensions parameter also.
>

__Usage:__
> vstest.console.exe \<testdll\> /logger:TeamCityLogger


Links
--
1. http://blogs.msdn.com/b/vikramagrawal/archive/2012/07/26/writing-loggers-for-command-line-test-runner-vstest-console-exe.aspx
2. http://confluence.jetbrains.com/display/TCD7/Build+Script+Interaction+with+TeamCity#BuildScriptInteractionwithTeamCity-ReportingTests
3. http://blog.degree.no/2012/09/unit-testing-visual-studio-2012-fakes-in-team-city/