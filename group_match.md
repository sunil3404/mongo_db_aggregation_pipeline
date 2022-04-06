query 1 -> group by age, eyecolor and than match age gt 30 and lt 35

db.persons.aggregate([
	{$group : {_id : {age: "$age", eyeColor: "$eyeColor"}}},
	{$match : {"_id.age": {$gt : 30 , $lt : 35}}}
])

query 2 -> group by age, eyeColor and than match by eyeColor

db.persons.aggregate([
	{$group : {_id : {age: "$age", eyeColor: "$eyeColor"}}},
	{$match : {"_id.eyeColor" : "brown"}}
])

query 3 -> group By age, eyecolor and than match age gt 30 and age lt 35 for only male gender

db.persons.aggregate([
	{$group : {_id : {age : "$age" , eyeColor: "$eyeColor", gender: "$gender"}}},
	{$match : {"_id.age" : {$gt : 30, $lt : 35}, "_id.gender" : "male"}}
])


