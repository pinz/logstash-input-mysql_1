# logstash-input-mysql
A LogStash input plugin for reading from MySQL database tables.
Read rows from an mysql database.

This is most useful in cases where you are logging directly to a table.
Any tables being watched must have an change column that is increasing in value.
This change column can be an int, timestamp, datetime or intastimestamp(bigint).

####Example

logstash config:
```
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
```
####options: 
#####1.host - string The host of the MySql Server.
#####1.port - number The port of the MySql Server.
#####1.db - array (required) The database or databases to read from.
#####1.host - string  The host of the MySql DB.
#####1.port - number The port of the MySql Server. Default 3306.
#####1.connproperties - hash A hash containing any MYSQL jdbc properties you wish to pass into the connection.
1.#####username - string The username for the mysql database.
1.#####password - string The password for the mysql database.
1.#####tables - array The tables to read from.
1.#####columns - array The columns to select. If empty it will select all columns.
1.#####repeatlast - boolean Option to repeat a select with the last returned changecol value. Allows for non distinct changecol values, such as batches. Default false.
1.#####repeatlast_checkcolumn - string Repeat last column to check for new rows. Set this to a distinct value such as a UUID.
1.#####sleepmin - number The minimum time to sleep in between queries. Default 5.
1.#####sleepmax - number The maximum time to sleep in between queries. When the sleep time reaches this value it will reset to the minimum. Default 30.
1.#####changecol - string The change column. This column is tracked so to not repeat rows. Requried.
1.#####changecoltype - string The type of the change column. Currently supported types are int, timestamp, datetime and intastimestamp(bigint) required.
1.changecolformat - string The format for the change column. Use this if you have a specific format for a a intastimestamp changecol. Default unused.

