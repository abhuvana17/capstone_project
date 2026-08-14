# Data Pipeline Module

## Overview

This module implements an end-to-end book data pipeline.

The pipeline performs:

1. Web scraping
2. Data cleaning
3. Data validation
4. Currency conversion
5. SQLite database loading
6. SQL analysis
7. Pandas JOIN comparison

## Source

Books are scraped from Books to Scrape.

## Dataset

The pipeline produces at least 60 book rows across at least 3 categories.

## Columns

- title
- category
- price_gbp
- rating
- in_stock
- price_inr

## Data Types

- price_gbp: float
- rating: integer from 1 to 5
- in_stock: boolean
- price_inr: float

## Currency Conversion

The project uses the following fixed project-defined rate:

**1 GBP = 105.50 INR**

This is a fixed rate with no date reference.

price_inr is calculated as:

price_inr = price_gbp * 105.50

## Cleaning Decisions

- Removed pound/currency symbols from prices.
- Converted prices to float.
- Converted rating words One-Five to integers 1-5.
- Converted stock status to Boolean.
- Removed duplicate title/category combinations.
- Removed rows with missing required values.
- Removed invalid ratings.
- Calculated price_inr using the fixed 105.50 rate.

## SQLite Database

The database file is books.db.

Two tables are implemented:

### categories

- category_id: Primary Key
- category_name: Unique and NOT NULL

### books

- book_id: Primary Key
- title: NOT NULL
- category_id: Foreign Key referencing categories(category_id)
- price_gbp
- rating
- in_stock
- price_inr

SQLite foreign-key enforcement is enabled.

## SQL Queries

The project contains more than five SQL queries.

They cover:

- SELECT
- WHERE
- AND
- DISTINCT
- LIKE
- BETWEEN
- IN
- ORDER BY
- LIMIT
- GROUP BY
- HAVING
- JOIN
- COUNT
- AVG
- MIN
- MAX
- SUM
- CASE

## JOIN Comparison

The JOIN is performed using both pd.read_sql() and pd.merge().

The outputs are displayed side by side and programmatically compared.

The expected result is:

Same shape: True

Same values: True

## Files

- data_pipeline_project.ipynb - Complete executable notebook
- books_cleaned.csv - Cleaned dataset
- books.db - SQLite database
- sql_output.txt - SQL queries and outputs
- join_comparison.txt - JOIN comparison
- README.md - Documentation

## Installation

Install the following packages:

pip install requests beautifulsoup4 pandas

## Running

Open data_pipeline_project.ipynb in Google Colab.

Run all four cells from top to bottom.

The notebook automatically scrapes, cleans, validates, creates the database, runs SQL queries, performs the JOIN comparison, and generates the output files.