Sample data 
{
	"_id" : ObjectId("624c4c5e97f000012eacf07a"),
	"index" : 1,
	"name" : "Kitty Snow",
	"isActive" : false,
	"registered" : ISODate("2018-01-23T04:46:15Z"),
	"age" : 38,
	"gender" : "female",
	"eyeColor" : "blue",
	"favoriteFruit" : "apple",
	"company" : {
		"title" : "DIGITALUS",
		"email" : "kittysnow@digitalus.com",
		"phone" : "+1 (949) 568-3470",
		"location" : {
			"country" : "Italy",
			"address" : "154 Arlington Avenue"
		}
	},
	"tags" : [
		"ut",
		"voluptate",
		"consequat",
		"consequat"
	]
}
# Use database

use hieradb

db.persons.insertMany([copy paste data from Persons.json])


stage 1 -> $match
-----------------------

# query 1 -> match age
db.persons.aggregate({$match : {"age" : 30}}, {$limit : 1})

# query 2 -> match age > $age and limit the result to 1
db.persons.aggregate({$match : {"age" : {$gt : 25}}}, {$limit : 1})


# query 3 -> match company.title and limit the result to 1 
db.persons.aggregate({$match : {"company.title" : "DIGITALUS"}}, {$limit : 1})

# query 4 -> match company.location.country and limit the result to 1 
db.persons.aggregate({$match : {"company.location.country" : "Italy"}}, {$limit : 1})
