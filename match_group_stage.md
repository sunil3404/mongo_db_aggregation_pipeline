query 1 -> match gender an group by age
db.persons.aggregate([
		     {$match : {gender: "male"}}, 
		     {$group : {_id : "$age"}},
		     {$limit : 5}
                    ]).pretty()


query 2 -> match gender and age > 30 and lt < 40 group by age
db.persons.aggregate([
		     {$match : {gender: "male", age : {$gt : 30 , $lt : 40}}},
		     {$group : {_id : "$age"}},
		     {$limit : 5}
		     ]).pretty()


query 3 -> group by eyeColor

db.persons.aggregate([
	{$group : {_id : "$eyeColor"}}
])

query 4 ->  group By nested fields company.location

db.persons.aggregate([
	{$group : {_id : "$company.location"}},
	{$limit : 2}
]).pretty()


query 5 -> group by multiple fields, name, age , gender

db.persons.aggregate([
	{$group : {_id : {name: "$name", age : "$age" , gender : "$gender"}}},
	{$limit : 3}
])


query 6 -> group by multiple fields eyeColor, favoriteFruit, age
db.persons.aggregate([
	{$group : {_id : { eyeColor: "$eyeColor", age: "$age", favoriteFruit: "$favoriteFruit"}}}
]).pretty()


query 7 -> match fruit banana and group by age and eyeColor
db.persons.aggregate([
	{$match : {favoriteFruit : "banana"}},
	{$group : {_id : {age: "$age", eyeColor: "$eyeColor"}}}
]).pretty()



