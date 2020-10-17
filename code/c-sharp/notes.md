# Notes



my notes: If you want to return something, dont use curly braces, as this destroys the variables after use, so instead we need to instatiate the object. See this link for more details [https://stackoverflow.com/questions/2822687/return-the-variable-used-for-using-inside-the-using-c-sharp](https://stackoverflow.com/questions/2822687/return-the-variable-used-for-using-inside-the-using-c-sharp)

we can dispose of connections differently and more safely using a using [https://stackoverflow.com/questions/41684823/executenonquery-doesnt-work](https://stackoverflow.com/questions/41684823/executenonquery-doesnt-work) [https://stackoverflow.com/questions/21709305/how-to-directly-execute-sql-query-in-c/21709663](https://stackoverflow.com/questions/21709305/how-to-directly-execute-sql-query-in-c/21709663)

.NET Framework vs .NET core vs .NET Standard framework is windows specific, core is for cross platform. both can be used for web/desktop applications, although .NET framework is used for ASP.NET web apps, whereas .NET core is used for ASP.NET core. Its an ecosystem with Standard library being the base for framework, core and xamarin.

Comments can slow down interpreters since they check for lines one at a time, but compilers are much faster at finding out what lines need to be compiled.

to take into account the previous day using a set timespan: 24 - timepsan - current hour

starting an app without debugging is consistent, this has something to do with me using the 32bit version and not the 64bit.

App.Config stores the config files, which is a good place for storing global variables

Install-Package System.Configuration.ConfigurationManager -Version 4.7.0 to install config manager to reference

camelCase for variables and parameters PascalCase for properties \(methods\)

if we use a using for the SQL connection and command, the connection gets disposed whether there is an error or not. just cleaner code.This way Dispose \(which automatically calls Close\) is called when leaving the using, be it in a usual way or by an exception. it works kind of like a try catch finally [https://stackoverflow.com/questions/2854910/difference-between-try-finally-and-try-catch](https://stackoverflow.com/questions/2854910/difference-between-try-finally-and-try-catch)

[https://stackoverflow.com/questions/61092/close-and-dispose-which-to-call](https://stackoverflow.com/questions/61092/close-and-dispose-which-to-call)

dictionaries are not stored in indexes, they can change the order they are output if changed or even unchanged

idict vs dict [https://stackoverflow.com/questions/1595498/a-difference-in-style-idictionary-vs-dictionary](https://stackoverflow.com/questions/1595498/a-difference-in-style-idictionary-vs-dictionary) [https://stackoverflow.com/questions/4724537/what-is-the-difference-between-dictionaryof-string-string-and-idictionaryof](https://stackoverflow.com/questions/4724537/what-is-the-difference-between-dictionaryof-string-string-and-idictionaryof)

Notes with Jude:

* functions do not have to take arguments, they just need a type and a return variable
* void indicates the lack of returning something, so a normal procedure
* seperate functions for open and close
* static methods have to use static variables
* for over for each, for int i is faster
* you can write a class, and reference a function in there with 

  \[new var = \]  classname.functionname\(\);

* close sqlconnections after use - [https://stackoverflow.com/questions/4439409/open-close-sqlconnection-or-keep-open](https://stackoverflow.com/questions/4439409/open-close-sqlconnection-or-keep-open)
* learnt a lot about inheritsm and oop in the first task, with stackoverflow, testing and mainly judes help.

