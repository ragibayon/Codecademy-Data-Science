# SQL: Intermediate

## Treds in Startups

Howdy! It’s your first day as a [TechCrunch](https://techcrunch.com) reporter. Your first task is to write an article on the rising trends in the startup world. To get you started with your research, your boss emailed you a project.sqlite file that contains a table called startups. It is a portfolio of some of the biggest names in the industry. Write queries with aggregate functions to retrieve some interesting insights about these companies.

What are you waiting for? Let’s get started!

## Problem Statements and Codes

**1. Getting started, take a look at the startups table:**

    SELECT * 
    FROM startups;

**2. Calculate the total number of companies in the table.**

    SELECT COUNT(*)
    FROM startups;

**3. We want to know the total value of all companies in this table. Calculate this by getting the SUM() of the valuation column.**

    SELECT SUM(valuation)
    FROM startups;

**4. What is the highest amount raised by a startup? Return the maximum amount of money raised.**

    SELECT name, MAX(valuation)
    FROM startups;

**5. Edit the query so that it returns the maximum amount of money raised, during ‘Seed’ stage.**

    SELECT name, MAX(valuation)
    FROM startups
    WHERE stage = 'Seed';

**6. In what year was the oldest company on the list founded?**

    SELECT name, MIN(founded)
    FROM startups;

**7. Return the average valuation.**

    SELECT AVG(valuation)
    FROM startups;

**8. Return the average valuation, in each category.**

    SELECT category, AVG(valuation)
    FROM startups
    GROUP BY category;

**9. Return the average valuation, in each category. Round the averages to two decimal places.**

    SELECT category, ROUND(AVG(valuation), 2)
    FROM startups
    GROUP BY category;

 **10. Return the average valuation, in each category. Round the averages to two decimal places. Lastly, order the list FROM highest averages to lowest.**

    SELECT category, ROUND(AVG(valuation), 2) AS AVG_valuation
    FROM startups
    GROUP BY category
    ORDER BY AVG_valuation DESC;

**11. First, return the name of each category with the total number of companies that belong to it.**

    SELECT category, COUNT(name) AS total_companies
    FROM startups
    GROUP BY category;

**12. Next, filter the result to only include categories that have more than three companies in them. What are the most competitive markets?**

    SELECT category, COUNT(name) AS total_companies
    FROM startups
    GROUP BY category
    HAVING total_companies > 3
    ORDER BY total_companies DESC;

**13. What is the average size of a startup in each location?**

    SELECT location, AVG(employees) AS size
    FROM startups
    GROUP BY location
    ORDER BY size DESC;

**14. What is the average size of a startup in each location, with average sizes above 500?**

    SELECT location, AVG(employees) AS size
    FROM startups
    GROUP BY location
    HAVING size > 500
    ORDER BY size DESC;
