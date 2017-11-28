# UDF-in-Hive

----
Steps to create UDF in HIVE

* First create JAVA program in Eclipse 
* Import all the JAR files for Hadoop and hive in Build path for JAVA program

```
package udf_hive;

import org.apache.hadoop.hive.ql.exec.UDF;
import org.apache.hadoop.io.Text;

public class replace extends UDF{
private Text result = new Text();

public Text evaluate(String str, String str1, String str2){
	
	String rep = str.replace(str1, str2);
	result.set(rep);
	return result;
}
}

```
* Then export the Java program into JAR file and copy the JAR file location

** Open the Hive terminal 
* Add the JAR file into HIVE using 
** Add JAR 'Location of Jar file'/Jarfilename

* Create Table in Hive 
```
Create table udf (Firstname String, Lastname String)
ROW Format Delimited
Fields Terminated BY ','
Stored as Textfile;
```

* Then Load data local into the table 
```
Load data local inpath 'locaion_of_file' into table udf;
```

* Then Create temporary function 
```
Create temporary function replaceword as 'udf_hive.replace';
```

* Write a query to check the function 

```
Select replaceword(Fitsname,"Harkirat","Harry") from udf;
```

*** We wil get the desired output after using the function. Here I have used Replacefunction, which replace firstname with another name
