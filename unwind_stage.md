query 1 -> Unwind stage

db.persons.aggregate([
	
	{$unwind : "$tags"}
])

query 2 -> unwind and project

db.persons.aggregate([
	{$limit : 4},
	{$match : {eyeColor : "blue"}},
	{$unwind : "$tags"},
	{$project : {name : 1 , gender: 1, tags: 1}}

])

query 3 -> unwind and group 

db.persons.aggregate([
	{$unwind : "$tags"},
	{$group : {_id : "$tags"}}
])
