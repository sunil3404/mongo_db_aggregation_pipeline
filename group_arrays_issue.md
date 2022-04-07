query 1 -> group on arrays

db.persons.aggregate([
	{$match: {tags : {"$size" : 3}}},
	{$group : {_id : "$tags"}}
]).pretty()
