query 1 -> project stage 
Note ->  0 for fieldname will not display
	 1 for fieldname will display

db.persons.aggregate([
	{$project : {_id: 0, name : 1, age:1}},
])

query 2 -> display all other fields except eyecolor and age
db.persons.aggregate([
	{$project : {eyeColor: 0, age: 0, "company.title": 0}},
	{$limit : 2}
]).pretty()

query 3 ->  giving a new column name to  age and project it 
db.persons.aggregate([
	{$project : {_id: 0, name: 1, newAge : "$age"}}
])

query 4 -> Project only name and company.location.country
db.persons.aggregate([
	{$project: { name: 1, "company.location.country" : 1}},
	{$limit :1 }
]).pretty()

query 5 -> match eyeColor which is not blue

db.persons.aggregate([
	{$match : {eyeColor: {$ne : "blue"}}},
	{$group : {_id : "$eyeColor"}}
])

query 6 -> match eyeColor and project name and gender

db.persons.aggregate([
	{$match : {eyeColor : "blue"}},
	{$project : {eyeColor: 1, name: 1, gender: 1}}
])


query 7 -> Project data with new Field names

db.persons.aggregate([
	{$project :{
		   _id : 0,
                   index : 1,
		   name: 1, 
		   personInfo: {
		   "eyes" : "$eyeColor",
	           "country" : "$company.location.country"
		   	} 
		   }
	},{$limit :1 }
]).pretty()
