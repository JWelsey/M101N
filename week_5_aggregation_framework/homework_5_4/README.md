# Homework 5.4
**Removing Rural Residents**

### Goal

In this problem you will calculate the number of people who live in a zip code in the US where the city starts with a digit. We will take that to mean they don't really live in a city. Once again, you will be using the zip code collection, which you will find in the 'handouts' link in this page. Import it into your mongod using the following command from the command line:
```sh
> mongoimport -d test -c zips --drop zips.json
```
If you imported it correctly, you can go to the test database in the mongo shell and conform that yields 29467 documents.

The project operator can extract the first digit from any field. For example, to extract the first digit from the city field, you could write this query:
```sh
> db.zips.aggregate([
    {$project: 
     {
	first_char: {$substr : ["$city",0,1]},
     }	 
   }
])
```
Using the aggregation framework, calculate the sum total of people who are living in a zip code where the city starts with a digit.

### Solution

```sh
> db.zips.aggregate([
	{
		$project: {first_char: {$substr : ["$city", 0, 1]}, pop: 1}
	},
	{
		$match : {first_char: {$in: ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9"]}}
	},
	{
		$group: {_id: "", score: {$sum: "$pop"}}
	}
])
```
**Answer = 298015**
