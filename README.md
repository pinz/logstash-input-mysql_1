# logstash-input-mysql
A LogStash input plugin for reading from MySQL database tables.
Read rows from an mysql database.

This is most useful in cases where you are logging directly to a table.
Any tables being watched must have an change column that is increasing in value.
This change column can be an int, timestamp, datetime or intastimestamp(bigint).

Example
     input {
       mysql {
         host => "yourhost.atyourdomain"
         db => "yourdb, yourdb2"
         username => "user"
         password => "pass"
         changecol => "id"
         changecoltype => "int"
       }
     }
     output {
        stdout {
        debug => true
       }
     }

