query 1 -> count  all documents

db.persons.aggregate([
	{$count : "allDocumentsCount"},
])




