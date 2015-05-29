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


