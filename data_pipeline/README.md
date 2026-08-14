
# Data Pipeline Project

## Overview

This project automatically scrapes book data from Books to Scrape,
cleans the data using pandas, calculates INR prices, stores the data
in SQLite, and performs SQL analysis.

## Fixed GBP to INR Rate

1 GBP = 105.50 INR

This is a fixed project-defined conversion rate and is not based on
a date-specific exchange rate.

## Dataset

The pipeline automatically collects at least 60 books from at least
3 categories.

## Columns

- title
- category
- price_gbp
- rating
- in_stock
- price_inr

## Cleaning Decisions

1. Removed the pound symbol from prices.
2. Converted prices to float.
3. Converted ratings One-Five to integers 1-5.
4. Converted stock status to Boolean.
5. Removed duplicate title/category combinations.
6. Removed invalid or missing prices and ratings.
7. Calculated price_inr using 105.50.

## Database

Two tables are used:

categories:
- category_id PRIMARY KEY
- category_name

books:
- book_id PRIMARY KEY
- title
- category_id FOREIGN KEY
- price_gbp
- rating
- in_stock
- price_inr

## SQL

The notebook demonstrates:

SELECT, WHERE, AND, DISTINCT, LIKE, BETWEEN, IN,
ORDER BY, LIMIT, GROUP BY, HAVING, JOIN,
aggregate functions and CASE.

## Pandas JOIN

The same join is performed using:

pd.read_sql()

and

pd.merge()

The notebook verifies that both outputs match.

## Files Generated

- books_cleaned.csv
- books.db
- sql_output.txt
- join_comparison.txt


## Pipeline Status
Scraping, cleaning and validation completed.