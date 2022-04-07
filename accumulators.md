Accumulators -> avg(), max(), min(), sum()

Syntax -> { $accumulator : $Expression }


$sum Accumulator
-----------------

query 1 -> group and $sum 

db.persons.aggregate([
	{$group : {_id : "$age" , count : {$sum : 1}}}
])

query 2 -> group by favoriteFruit and count

db.persons.aggregate([
	{$group : {_id : "$favoriteFruit", count : {$sum : 1}}}
])

query 3 -> group by age and count
db.persons.aggregate([
        {$group : {_id : "$age", count : {$sum : 1}}}
])

query 4 - > unwind tags group by tags and count

db.persons.aggregate([
	{$unwind : "$tags"},
	{$group  : {_id : "$tags", count : {$sum : 1}}}
])


Accummulattor $avg 
-------------------

syntax -> {$avg : Expression}

query 1 -> group by eyeColor and use avg accumulator

db.persons.aggregate([
	{$group : {_id : "$eyeColor", avgAge : {$avg : "$age"}}}
])


query 2 -> Avg Age per country

db.persons.aggregate([
	{$group : {_id : "$company.location.country", avgAge : {$avg : "$age"}}}
])

