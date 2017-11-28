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
