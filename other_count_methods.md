count method 1 -> toArray().length

db.persons.aggregate([]).toArray().length

method 2 -> itcount()
db.persons.aggregate([]).itcount()


method 3 -> count stage
db.persons.aggregate([ {$count : "TotalCount"}])

method 4 -> find count method is the wrapper of the Aggregate $count
db.persons.find({}).count()

