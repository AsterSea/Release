# Release
riddle发布版本
# How to use Riddle
Riddle can take a Maven based project (it should contain the complete Maven built project directory and file pom.xml) as input for analysis. The expected running environment is 64-bit Window operating system with JDK 1.7 or 1.8. **As Maven built projects need to download dependencies from Maven Central Repository, Riddle cannot work offline.**

You can run Riddle on our experimental subjects based on the following steps:

**Step 1**: Unzip the plugin-riddle.zip to local directory. Recommended directory structure is:

>> D:\plugin-riddle
     
>>     ├─riddle-1.0.jar : 
     
>>     ├─riddle-1.0.pom
   
>>     ├─soot-1.0.jar
    
>>     ├─apache-maven-3.2.5
   
>>     ├─script.jar

*Note: To facilitate testing, please keep the unzip directory to be consistent with the above example. It should be noted that the location of data (e.g, D:\plugin-decca) is not hardcoded, it can be replaced with user's actual unzip directory in the install commands.*

**Step 2**: Install Riddle

(a) Execute the following Windows CMD command to install soot:

>> D:\plugin-riddle\apache-maven-3.2.5\bin\mvn.bat install:install-file  -Dfile=D:\plugin-riddle\soot-1.0.jar  -DgroupId=neu.lab  -DartifactId=soot -Dversion=1.0 -Dpackaging=jar

(b) Execute the following Windows CMD command to install Decca:

>> D:\plugin-riddle\apache-maven-3.2.5\bin\mvn.bat install:install-file  -Dfile=D:\plugin-riddle\riddle-1.0.jar  -DgroupId=neu.lab  -DartifactId=riddle -Dversion=1.0 -Dpackaging=maven-plugin -DpomFile=D:\plugin-riddle\riddle-1.0.pom

**Step 3**: Detect and assess the dependency conflict issues.

Execute the following Windows CMD command to analyze the project:

>>D:\plugin-riddle\apache-maven-3.2.5\bin\mvn.bat -f=D:\RawData\Issue report dataset\Projects\hadoop-rel-release-3.0.0\hadoop-common-project\hadoop-minikdc\pom.xml -Dmaven.test.skip=true neu.lab:riddle:1.0:printRiskLevel -DresultFilePath=D:\Report\ –e

Then you can get the dependency issue report in your specified directory (e.g., **D:\Report\**).

>>> **Command explanation:**
>>>>(1) -f=pom file : Specify the project under analysis;

>>>>(2) -DresultFilePath=output issue report directory : Output the issue report to the specified folder;


