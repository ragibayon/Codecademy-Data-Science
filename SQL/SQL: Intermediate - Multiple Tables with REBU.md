# SQL: INTERMEDIATE

## Multiple Tables with REBU

Suppose you are a data analyst at REBU, a ridesharing platform. For a project, you were given three tables:

* **trips** - trips information
* **riders** - users data
* **cars** - autonomous cars

Have fun!

## Problem Statements and Codes

**3. Try out a simple cross join between riders and cars. Is the result useful?**

    SELECT riders.first, riders.last, cars.model 
    FROM riders
    CROSS JOIN cars;

 **We can see the combination of every car models with riders. but this information is not useful.**

**4. Suppose we want to create a Trip Log with the trips and its users. Find the columns to join between trips and riders and combine the two tables using a LEFT JOIN. Let trips be the left table.**

    SELECT trips.id, riders.username 
    FROM trips
    LEFT JOIN riders
    ON riders.id = trips.rider_id;

**5. Suppose we want to create a link between the trips and the cars used during those trips. Find the columns to join on and combine the trips and cars table using an INNER JOIN.**

    SELECT trips.id, cars.model
    FROM trips
    JOIN cars
    ON trips.car_id = cars.id;

**6. The new riders data are in! There are three new users this month. Stack the riders table on top of the new table named riders2.**

    SELECT * FROM riders
    UNION
    SELECT * FROM riders2;

**7. What is the average cost for a trip?**

    SELECT AVG(cost) AS 'Average_cost'
    FROM trips;

**8. REBU is looking to do an email campaign for all the irregular users. Find all the riders who have used REBU less than 500 times!**

    SELECT *
    FROM riders
    where total_trips < 500;

**9. Calculate the number of cars that are active.**

    SELECT COUNT(*) AS 'active_cars'
    FROM cars
    WHERE status = 'active';

**10. It’s safety recall time for cars that have been on the road for a while. Write a query that finds the two cars that have the highest trips_completed.**

    SELECT *
    FROM cars
    ORDER BY trips_completed DESC
    LIMIT 2;
