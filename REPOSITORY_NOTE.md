# Repository Note: Data Manipulation in R

## Overview
This repository contains comprehensive educational resources for **data management, cleaning, and manipulation in R**. It demonstrates practical data handling techniques using real-world malaria surveillance data extracted from DHIS2.

## Repository Details
- **Owner:** Yalemzewod
- **Repository:** Data_manupilation_in_r
- **Language:** HTML (interactive documentation)
- **Primary Format:** Quarto Document (.qmd)
- **Status:** Active (Last updated: April 6, 2026)
- **Created:** February 22, 2023

## Key Topics Covered

### 1. Data Import
- Reading .xlsx (Excel) files
- Reading .dta (Stata) files
- Understanding data formats and structures

### 2. Data Cleaning
- Removing unwanted text and special characters
- Renaming columns for consistency
- Name matching and standardization
- Grouping and labeling categorical variables

### 3. Data Reshaping
- Long to wide format transformation using `pivot_wider()`
- Wide to long format transformation using `pivot_longer()`
- Understanding tidy data principles

### 4. Data Exploration
- Generating summary statistics
- Creating exploratory tables
- Understanding data distributions and patterns

## Sample Showcase: Data Manipulation Workflow

### Example: Malaria Surveillance Data Processing

```r
# Step 1: Load required libraries
library(readxl)
library(tidyr)
library(dplyr)

# Step 2: Import DHIS2 malaria surveillance data
malaria_data <- read_excel("malaria_surveillance.xlsx")

# Step 3: Data Cleaning
malaria_clean <- malaria_data %>%
  # Remove missing values
  filter(!is.na(case_count)) %>%
  # Rename columns for clarity
  rename(
    case_number = case_count,
    report_date = date_reported,
    region = administrative_region
  ) %>%
  # Standardize region names
  mutate(region = str_trim(str_to_title(region)))

# Step 4: Reshape to wide format (by month)
malaria_wide <- malaria_clean %>%
  pivot_wider(
    names_from = month,
    values_from = case_number,
    values_fill = 0
  )

# Step 5: Data Exploration
summary(malaria_wide)
head(malaria_wide)
```

## Output Files
- **Data manupulation in r.html** - Interactive HTML documentation for browser viewing
- **Data manupulation in r.qmd** - Quarto source document with embedded R code
- **README.md** - Quick reference guide

## Use Cases
✓ Learning R data manipulation fundamentals  
✓ Understanding epidemiological data workflows  
✓ Mastering tidyverse functions (dplyr, tidyr)  
✓ Real-world data cleaning scenarios  
✓ DHIS2 health surveillance data processing  

## Getting Started
1. View the interactive HTML file for a guided walkthrough
2. Explore the .qmd source for reproducible code examples
3. Apply the techniques to your own datasets
4. Reference specific sections for data manipulation tasks

## Learning Objectives
By working through this repository, you will:
- Understand data import procedures for different file formats
- Apply effective data cleaning strategies
- Master data reshaping techniques
- Perform exploratory data analysis
- Handle real surveillance data workflows

---
*This repository serves as an educational resource for data professionals working with health surveillance and epidemiological datasets.*
