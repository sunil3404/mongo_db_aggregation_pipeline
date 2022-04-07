Unary Operator  - are used on the broader stage like match or project
--------------- 

$type , $or 

$lt   , $gt

$and  , $multiply

type  - gives the type of field
----------------------------------  
syntax -> {$type : expression } ex : {$type : "$age"} 

query -> $type and $project

db.persons.aggregate([

	{$project : {_id: 0, name : 1, 
		     eyeColorType : {$type : "$eyeColor"},
		     ageType : {$type : "$age"},
		     tagsType: {$type : "$tags"},
		     companyType: {$type : "$company"}}}
])


$out -  writes aggregate utput to the new mongo DB collections
--------------------------------------------------------------


syntax -> {$out : <new Collection Name>}


query 1 -> group by age and eye Color

db.persons.aggregate([
	{$limit : 100},
	{$group : {_id :{eyeColor : "$eyeColor", age: "$age", name: "$name"}}},
	{$out : "outCollection"}
]) 



