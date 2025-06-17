# Overview

This repository contains a Big Data processing project based on the Enron Email Dataset. The project demonstrates the use of PySpark within the Databricks environment to perform distributed data processing, structured extraction, and rule-based spam detection from a semi-structured email corpus. The workflow showcases real-world data engineering techniques for handling text data at scale.

## Task: Enron Email Dataset Analysis Using PySpark

# Objective

The goal of this project is to analyze the Enron email dataset by performing structured data extraction, metadata parsing, and spam detection using PySpark in a Databricks environment. This involves ingesting raw text email data, parsing headers, identifying sender and recipient information, and classifying messages based on simple spam heuristics.

# Key Features

- **Email Parsing**: Extraction of `From:` and `To:` fields from the raw email text using regular expressions.
- **Spam Detection**: Rule-based detection of spam emails using keyword matching (e.g., "win", "cash", "offer", "prize").
- **Data Classification**: Binary column `is_spam` added to flag messages as spam or non-spam.
- **Data Exploration**: 
  - Count of spam vs. non-spam messages.
  - Identification of unique senders and recipients.
  - Overview of email communication structure.
- **SQL Integration**: Use of Spark SQL queries for structured data analysis.
- **Scalable Processing**: Utilization of Apache Spark for distributed, scalable data handling.

# Technologies Used

- **Databricks** for cloud-based notebook execution and distributed computation.
- **Apache Spark (PySpark)** for processing large-scale semi-structured data.
- **Spark SQL** for executing SQL-like operations on DataFrames.
- **Regular Expressions** for text pattern matching and parsing.

# Implementation Steps

- **Data Loading**: The Enron dataset (`emails.csv`) is extracted from a ZIP archive and uploaded to Databricks FileStore.
- **Data Ingestion**: The CSV file is read using `spark.read.csv` with appropriate options for header recognition and multiline support.
- **Preprocessing**:
  - Null or malformed rows are filtered.
  - The `message` field is extracted and used for header parsing.
- **Email Header Parsing**:
  - The sender (`From:`) and recipient (`To:`) are extracted using `regexp_extract`.
  - New columns `senders` and `recipients` are created to hold this information.
- **Spam Detection**:
  - A set of spam-related keywords is defined.
  - Rows are classified as spam (`is_spam = 1`) or non-spam (`is_spam = 0`) based on keyword presence.
- **Analysis and Reporting**:
  - Spam vs. non-spam message count is computed.
  - Unique senders and recipients are identified.
  - Communication patterns between senders and recipients are visualized.

# Output Highlights

- **Total Spam vs. Non-Spam Messages**: Categorization results displayed using PySpark DataFrame and SQL queries.
- **Unique Senders and Recipients**: Identified using distinct counts from parsed columns.
- **Sender → Recipient Analysis**: Visualized and aggregated data showcasing email flows and relationships.
- **Regex Extraction Accuracy**: Structured metadata obtained from unstructured email content.
