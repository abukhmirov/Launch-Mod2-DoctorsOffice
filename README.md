# Mod2 Week3 Assessment

## Setup
1. Fork this repository.
1. You can either work on your clone in GitHub, or open your clone in visual studio.

## Questions (10 Points Possible)

<img alt="erd_for_assessment" src="https://github.com/modelmapper/modelmapper/assets/11747682/60bebb3c-9faa-4f3e-ae0a-7df7dde06784">

[Citation for ERD](https://circle.visual-paradigm.com/hospital/)
1. Use the Doctors Office ERD above to answer the following questions:
    1. How many patients can each doctor have?  They can have multiple patients
    1. How many doctors can each patient have? They can have one doctor
    1. How would you describe the relationship between patients and tests? Be sure to use either one-to-one, one-to-many, or many-to-many in your answer. It is one-to-many. The symbols on the diagram are one-to- next to the patients and many-to- next to tests.
    1. What are the foreign keys in this diagram? They are the doctor_id in patients and patient_id in tests
    1. What is the primary key for the Tests table.  It is the id.
    1. What query would return the number of doctors who have a specialization in "pediatrics"? SELECT COUNT(name) FROM doctors WHERE specialization = 'pediatrics';

<br>

2. What does a join table do? Why would we need one? It is a table that contains columns from multiple tables. It helps us compare the data in the tables inside one table.
3. What is a question that the following query helps answer? It shows the hometowns and how many artists are from those hometowns.
```SQL
SELECT hometown, COUNT(name) FROM artists
GROUP BY hometown;
```

4. I'm trying to write a query to find the average age of all patients, but it's not working. How would you modify this query to get it to work as expected? SELECT AVG(age) FROM patients;
```SQL
SELECT age FROM AVERAGE(patients);
```
5. How would you describe the difference between a `LEFT JOIN` and an `INNER JOIN` A LEFT JOIN is a specific JOIN that shows all contents of one table and only the ones that intersect with the first table from the second table. INNER JOIN shows only the intersecting contents.
 
## Exercise (10 Points Possible)

Follow these steps to setup the assessment:
1. Create a new database named `flight_db` using pgAdmin.
2. Copy [this script](https://launch.turing.edu/module2/assessments/flight_db.txt) and paste it into the query tool to insert records into your database. 
3. Run the following `SELECT` queries individually to get an understanding of the data:
> `SELECT * FROM airlines;`
> `SELECT * FROM flights;`

** If you need help setting up the database, reach out to an instructor! **

Please provide the QUERY (not the answer) that returns each of the following:
1. The flight numbers for all delayed flights (i.e. not on time). SELECT * FROM flights
WHERE on_time = false;
2. The count of delayed flights. SELECT COUNT(id) FROM flights
WHERE on_time = false;
3. The sum of prices for all flights arriving to Raleigh-Durham (`RDU`). SELECT SUM(price) FROM flights
WHERE arrive_city = 'RDU';
4. The average price for all flights in the database. SELECT AVG(price) FROM flights;
5. The average price for all flights arriving to Raleigh-Durham. SELECT AVG(price) FROM flights
WHERE arrive_city = 'RDU';
6. The departure city and number of flights departing from each city. SELECT depart_city, COUNT(id) FROM flights
WHERE arrive_city = 'RDU'
GROUP BY depart_city;
7. The count of airlines in the database. SELECT COUNT(id) FROM airlines;
8. The count of flights in the database. SELECT COUNT(id) FROM flights;
9. The flight number, departure city, arrival city, price, and airline name of each flight. Do not return the airline ID number. SELECT flights.flight_number, flights.depart_city, flights.arrive_city, flights.price, airlines.airline_name FROM flights
JOIN airlines ON airlines.id = airlines.id;
10. The airline name, flight number, and price of each flight on the Delta airline. (Assume that you do not know the ID number of the Delta airline. In a larger database, you would be expected to memorize ID numbers). SELECT airlines.airline_name, flights.flight_number, flights.price FROM flights
JOIN airlines ON airlines.id = airlines.id
WHERE airlines.airline_name = 'Delta';

## Submission

Submit the Assessment Submission form linked in your cohort slack channel!

## Rubric

This assessment has a total of 20 Points. Earning 14 or more points is a pass and will indicate that you are progressing well with the material.

As a reminder, this assessment is for students and instructors to determine if there are any areas that need additional reinforcement!
