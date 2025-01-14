Mineotaur is a visual analytics tool for high-throughput / high-content microscopy screens developed at the Univeristy of Cambridge, UK at the 
<a href="http://www.gen.cam.ac.uk/research-groups/carazo-salas" target="_blank">Carazo Salas group</a> of the Department of Genetics by <a href="http://www.inf.unideb.hu/~antal.balint" target="_blank">Bálint Antal</a>.
<!--You can find more information on Mineotaur at http://www.mineotaur.org where you can try out our <a href="http://demo.mineotaur.org" target="_blank">demo</a> or download the latest binary version.
-->
You can find more information on Mineotaur at http://www.mineotaur.org where you can download the latest binary version.

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

<h3>Mineotaur installation:</h3>

1.	Download the latest jar file from http://www.mineotaur.org.
2.	Create a property file, a data file and a label file (see documentation and example input data)
3.	Start the data import with the following command:
java -jar &lt;path_to_jar file&gt; -import mineotaur.input chia_sample.tsv chia_labels.ts
4.	After the database creation is completed you can start your Mineotaur instance with the following command:
java –jar &lt;path_to_jar file&gt; -start <instance_name>
5.	You can start querying at http://127.0.0.1:8080 in your browser.

<h3>Import data</h3>
The graph model for each Mineotaur instance can be generated by providing a CSV (comma separated value) file in the following format:  <br/>
First line: column headers. These will serve as the property names for their respective object types in the database.              <br/>
Second line: object names. These describe the names of the objects of interest to be stored in the database. The property in each column described in the first line will be associated with the object described here.<br/>
Third line: property types. These describe the data types of the properties for each column. The possible values are:<br/>
<ul>
<li>TEXT: the column contains a text. Stored as a metadata. </li>
<li>NUMBER: the column contains a number, thus it will be become a queryable information if stored in a descriptive object. </li>
<li>ID: identifier of the object. Multiple ID properties can be set to an object. </li>
</ul>
Each line after the third provides a descriptive object instance. <br/>
To provide annotation for the grouping objects, an additional input file providing the labels is needed. The first n column describe the IDs for the grouping object. All other columns provide a binary value for a label (1=the grouping object possesses the annotation, 0=otherwise).

<!--
REST access
The server side can be accessed programmatically from any programming language or framework capable of handling HTTP requests and responses and JSON (i.e. Java, Python, Matlab, Bash, etc.). The REST service can be accessed in the following way:
http://&lt;server_url&gt;/query?type={scatter|distribution}&level={group|descriptive}&action={json|embed|share}&property1=<property>&[property2=<property>]&[filter={filter_property}]*&[groupObjects={group_objects}]*&[hits={hits}]
Parameters:
Type: Type of the query.
Level: whether the grouping (e.g. gene) or descriptive (e.g. cell) level information is queried
Action: whether the data is used by application (json) or it will be embedded or shared. For REST access, choose json.
Property: the features to be queried
Filter: the filter property to be used
GroupObject = the list of group objects to be included in the query
Hits = the type of hits to be considered in the query
-->

