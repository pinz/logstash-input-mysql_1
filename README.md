# logstash-input-mysql
A LogStash input plugin for reading from MySQL database tables.
Read rows from an mysql database.

This is most useful in cases where you are logging directly to a table.
Any tables being watched must have an change column that is increasing in value.
This change column can be an int, timestamp, datetime or intastimestamp(bigint).

Example
     <br>input {
       <br>mysql {
         <br>host => "yourhost.atyourdomain"
         <br>db => "yourdb, yourdb2"
         <br>username => "user"
         <br>password => "pass"
         <br>changecol => "id"
         <br>changecoltype => "int"
       <br>}
     <br>}
     <br>output {
        <br>stdout {
        <br>debug => true
       <br>}
     <br>}
     
    <br>options: 
    <br>host - string <br>The host of the MySql Server.
    <br>port - number <br> The port of the MySql Server.
    <br>db - array (required) - The database or databases to read from.
    <br>host - string <br> The host of the MySql DB.
     <br>port - number <br>The port of the MySql Server. Default 3306.
<br>connproperties - hash <br>A hash containing any MYSQL jdbc properties you wish to pass into the connection.
     <br><br>username - string <br>The username for the mysql database.
     <br>password - string <br>The password for the mysql database.
     <br>tables - array <br>The tables to read from.
     <br>columns - array <br>The columns to select. If empty it will select all columns.
          <br>repeatlast - boolean <br>Option to repeat a select with the last returned changecol value. Allows for non distinct <br>changecol values, such as batches. Default false.
     <br>repeatlast_checkcolumn - string <br>Repeat last column to check for new rows. Set this to a distinct value such as a UUID.
     <br>sleepmin - number <br>The minimum time to sleep in between queries. Default 5.
     <br>sleepmax - number <br>The maximum time to sleep in between queries. When the sleep time reaches this value it will reset to the minimum. Default 30.
     <br>changecol - string <br>The change column. This column is tracked so to not repeat rows. Requried.
       changecoltype - string <br>The type of the change column. Currently supported types are int, timestamp, datetime and <br>intastimestamp(bigint) required.
     <br>changecolformat - string <br>The format for the change column. Use this if you have a specific format for a a <br>intastimestamp changecol. Default unused.

