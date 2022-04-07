query 1 ->  limit 100, match -> age > 27 and group By country

db.persons.aggregate([
	{$limit : 100}, 
	{$match : {age : {$gt : 27}}},
	{$group : {_id  : "$company.location.country"}}
])
