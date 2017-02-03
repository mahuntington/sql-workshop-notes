#Lab - MySQL

## Goal

Find out how many flights go from NYC to Paris

## Stretch Goals

- Do this so that just the number appears as the result of only one SQL statement
- Which airlines travel from NYC to Paris?
- Find all the flights that leave NYC.  Give me a list of how many go to each destination city.

## Hints

- The routes table has a column called `origin_id` and another called `destination_id`.  These map to the `id` column in the airport table.
- You're going to have to use the airports table twice in the same SQL statement.  In order to tell which airport is the `destination` and which is the `origin`, you're going to have to temporarily rename the airports table like so:

	```sql
		/* note that once you rename a table, you MUST refer to it by its new name */
		SELECT * FROM airports AS origin WHERE origin.city = 'New York';
		/* later on in the SQL statement, when dealing with the destination, you should do the same for airports AS destination */
	```
