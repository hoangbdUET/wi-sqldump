# Mysql Dump

This repo is 100% clone from https://github.com/webcaetano/mysqldump.git

Create a backup from MySQL

## Installation

```
npm install mysqldump
```

Example 
```javascript
var mysqlDump = require('wi-sqldump');

mysqlDump({
	host: 'localhost',
	user: 'root',
	password: '',
	database: 'test',
	dest:'./data.sql' // destination file
},function(err){
	// create data.sql file;
})
```

Full Options Example :

```javascript
var mysqlDump = require('wi-sqldump');

mysqlDump({
	host: 'localhost',
	user: 'root',
	password: '',
	database: 'test',
	tables:['players'], // only these tables
	where: {'players': 'id < 1000'}, // Only test players with id < 1000
	ifNotExist:true, // Create table if not exist
	disableForeignKeyChecks: true, //Adds SET foreign_key_checks = 0; at the file begin
	dest:'./data.sql' // destination file
},function(err){
	// create data.sql file;
})
```


## Options


#### host

Type: `String`

Url to Mysql host. `Default: localhost`

#### port

Type: `String`

Port to Mysql host. `Default: 3306`

#### user

Type: `String`

The MySQL user to authenticate as.

#### password

Type: `String`

The password of that MySQL user

#### database

Type: `String`

Name of the database to dump.

#### tables 

Type: `Array`

Array of tables that you want to backup.

Leave Blank for All. `Default: [] ALL`

#### schema 

Type: `Boolean`

Output table structure `Default: true`;

#### data 

Type: `Boolean`

Output table data for ALL tables `Default: true`;

#### where
Type: `Object`

Where clauses to limit dumped data `Example: where: {'users': 'id < 1000'}`

Combine with `data: false` to only dump tables with where clauses  `Default: null`;

#### ifNotExist 

Type: `Boolean`

Create tables if not exist method `Default: true`;

#### dropTable 

Type: `Boolean`

Drop tables if exist `Default: false`;

#### disableForeignKeyChecks 

Type: `Boolean`

Adds SET foreign_key_checks = 0; at the begin of the generated file `Default: false`;

#### getDump 

Type: `Boolean`

Return dump as a raw data on callback instead of create file `Default: false`;

#### dest 

Type: `String`

Output filename with directories `Default: './data.sql'`;

#### socketPath

Type: `String`

Path to a unix domain socket to connect to. When used `host` and `port` are ignored.