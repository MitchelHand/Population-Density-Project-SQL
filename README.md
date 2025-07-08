# Data Analysis Portfolio: SQL Proficiency

## Overview

This repository showcases my proficiency in SQL for data extraction, transformation, and analysis, particularly with complex queries involving relational databases. The examples provided demonstrate my ability to derive meaningful insights from large datasets, a critical skill for data-driven decision-making.

## Key Skills Demonstrated

* 📊 **Advanced SQL Querying:** Crafting complex SQL queries involving joins, subqueries, aggregation functions, and conditional logic.

* ⚙️ **Data Manipulation and Transformation:** Effectively using SQL functions (`ROUND`, `AVG`) to transform raw data into actionable metrics.

* 🗄️ **Relational Database Understanding:** Demonstrating a solid grasp of database schema (e.g., `World` database with `city` and `country` tables) and relationships between tables.

* ⚡ **Performance Optimization (Implicit):** Structuring queries efficiently for better performance.

* 🧠 **Data Interpretation:** Extracting and presenting data in a clear and insightful manner.

## Project Examples

### 1. Global Economic and Population Insights: GDP Per Capita Analysis

This query focuses on analyzing the economic standing of countries relative to their population, specifically identifying cities within countries that exceed the global average GDP per capita.

**Objective:** To retrieve city and country information, along with their respective populations and calculated GDP per capita, for countries whose GDP per capita is above the global average.

**SQL Syntax:**

```
SELECT
    city.Name AS City,
    city.CountryCode,
    country.Name AS Country,
    city.Population AS CityPopulation,
    ROUND(country.GNP / country.Population, 2) AS GDPPerCapita
FROM
    city
JOIN
    country ON city.CountryCode = country.Code
WHERE
    country.Population > 0
    AND country.GNP IS NOT NULL
    AND (country.GNP / country.Population) > (
        SELECT AVG(GNP / Population)
        FROM country
        WHERE Population > 0 AND GNP IS NOT NULL
    )
ORDER BY GDPPerCapita DESC;

```

**Insights & Methods:**

* **Joins:** Utilizes an `INNER JOIN` between the `city` and `country` tables on `CountryCode` to combine related data.

* **Subquery for Aggregation:** Employs a subquery to calculate the `AVG(GNP / Population)` across all relevant countries, demonstrating the ability to use aggregated results as a comparison benchmark.

* **Calculated Fields:** Creates a new `GDPPerCapita` field by dividing `GNP` by `Population` and rounding it to two decimal places, showcasing data transformation skills.

* **Filtering:** Filters out countries with zero population or null GNP values to ensure data integrity and meaningful calculations. The `WHERE` clause also applies the condition to select countries with above-average GDP per capita.

* **Ordering:** Orders the results by `GDPPerCapita` in descending order, allowing for easy identification of top-performing economies.

### 2. Population Density Analysis

This query focuses on calculating population density for various countries, providing insights into how densely populated different regions are.

**Objective:** To calculate and display the population density for countries, ordered by density.

**SQL Syntax (as provided in screenshot):**

```
SELECT
    Name AS Country,
    Population,
    SurfaceArea,
    ROUND(Population / SurfaceArea, 2) AS PopulationDensity
FROM
    country
WHERE
    Population IS NOT NULL AND SurfaceArea > 0
ORDER BY
    PopulationDensity ASC
LIMIT 70;

```

**Insights & Methods:**

* **Direct Calculation:** Directly calculates `PopulationDensity` by dividing `Population` by `SurfaceArea`.

* **Data Cleaning:** Filters out records where `Population` is `NULL` or `SurfaceArea` is zero, preventing division-by-zero errors and ensuring accurate density calculations.

* **Ordering and Limiting:** Orders the results by `PopulationDensity` in ascending order and limits the output to the first 70 records, useful for quickly reviewing the least densely populated areas.

## Tools and Environment

* 💻 **MySQL Workbench:** The screenshot demonstrates the use of MySQL Workbench, indicating familiarity with a professional database management tool for writing, executing, and visualizing SQL queries and their results.

* 📝 **SQL (Structured Query Language):** Core language used for all data interactions.

* 🌍 **World Database:** Experience working with a common, real-world dataset, showcasing adaptability to different data schemas.

## Conclusion

These examples highlight my analytical capabilities and strong command of SQL, enabling me to extract, analyze, and present complex data effectively. I am eager to apply these skills in a challenging data-driven environment.

**Contact:** Mitchel Hand @ [LinkedIn Profile Link](https://www.linkedin.com/notifications/?filter=all) / mitchelhanddesign@hotmail.com

![image](https://github.com/user-attachments/assets/163757f4-5fa1-468b-b2cf-cc7889881e0c)
