Syntax -> {$sort : {<field 1> : -1 , field 2 : 1}}

note : -1 -> descending 1 -> ascending

query 1 -> sort all documents By name

db.persons.aggregate([
	{$sort : {name : 1}},
	{$limit:  4}
]).pretty()

query 1 -> sort all documents By age : -1, gender: -1, eyeColor:1
db.persons.aggregate([
        {$sort : {age: -1, gender: -1 , eyeColor: 1}},
        {$limit:  4}
]).pretty()

