query 1 -> group By favorite Fruit
db.persons.aggregate([
	{$group : {_id : "$favoriteFruit"}},
	{$sort  : {_id : 1}}
])

query 2 -> group By age and sort by Id

db.persons.aggregate([
	{$group : {_id : "$age"}},
	{$sort : {_id : 1}}
])

query 3 -> group By eyeColor and favoriteFruit and sort by _id.eyeColor and _id.favoriteFruit

db.persons.aggregate([
	{$group : {_id : {eyeColor : "$eyeColor", favoriteFruit: "$favoriteFruit"}}},
	{$sort  : {"_id.eyeColor" : 1, "_id.favoriteFruit":-1}}
])

query 4 -> match by age gt 25 group By eyeColor and favoriteFruit and sort by _id.eyeColor and _id.favoriteFruit

db.persons.aggregate([
	{$match : {age : {$gte : 25 }}},
	{$group : {_id : {eyeColor : "$eyeColor", favoriteFruit: "$favoriteFruit"}}},
	{$sort :  {"_id.eyeColor" : 1 , "_id.favoriteFruit" : -1}}
])
