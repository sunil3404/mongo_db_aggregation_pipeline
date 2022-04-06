query 1 -> gorup by age and count age
db.persons.aggregate([
	{$group : {_id : "$age"}},
	{$count : "distinceAgeCount"}
])

query 2 -> gorup by eyecolor and count eyecolor
db.persons.aggregate([
	{$group : {_id : "$eyeColor"}},
	{$count : "eyeColorCount"}
])

query 3 -> group by eyeColor and gender
db.persons.aggregate([
	{$group : {_id : { eyeColor : "$eyeColor", gender: "$gender"}}},
	{$count : "distinctEyeColoeAndGender"}
])
query 4 -> match age > gte 30 and group by eyeColor and age
db.persons.aggregate([
	{$match : {age :{$gte : 25 }}},
	{$group : {_id : {eyeColor : "$eyeColor" , age: "$age"}}},
	{$count : "eyeColorAndGender"}
])
query 5 -> group by company -> location -> country and count countries

db.persons.aggregate([
	{$group : {_id : "$company.location.country"}}, 
	{$count : "country"}
])
