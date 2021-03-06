# Final Exam: Question 6

### Goal

Suppose you have a collection of students of the following form:
```sh
{
	"_id" : ObjectId("50c598f582094fb5f92efb96"),
	"first_name" : "John",
	"last_name" : "Doe",
	"date_of_admission" : ISODate("2010-02-21T05:00:00Z"),
	"residence_hall" : "Fairweather",
	"has_car" : true,
	"student_id" : "2348023902",
	"current_classes" : [
		"His343",
		"Math234",
		"Phy123",
		"Art232"
	]
}
```
Now suppose that basic inserts into the collection, which only include the last name, first name and student_id, are too slow (we can't do enough of them per second from our program). What could potentially improve the speed of inserts. Check all that apply.

### Solution

- Add an index on last_name, first_name if one does not already exist. **False**
- Remove all indexes from the collection, leaving only the index on _id in place. **True**
- Provide a hint to MongoDB that it should not use an index for the inserts. **False**
- Set w=0, j=0 on writes. **True**
- Build a replica set and insert data into the secondary nodes to free up the primary nodes. **False**
