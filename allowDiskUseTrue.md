allowDiskUse : true

- > All aggregation stages can use maxinmum of 100 MB of RAM

- > Server will return error if RAM limit is exceeded 

- > Following option will enable MongoDB to write stages data to temporal files
	-: {allowDiskUse: true}

example - => db.persons.aggregate([] , {allowDiskUse :true})
