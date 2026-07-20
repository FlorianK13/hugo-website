---
date: "2026-07-20"
draft: false
title: "LinkML SQL Validator: Validating Databases with a data model"
---

The [LinkML SQL Validator](https://linkml.io/linkml/generators/sqlvalidation.html) is a generator I recently contributed to LinkML. It takes a LinkML schema and compiles its constraints (cardinality, value ranges, enumerations, pattern matching, etc.) into plain SQL queries, which can then be run against any relational database to find rows that violate the schema — without needing to load the data into a specific validation framework first.

The idea for this project is to put that generator to use for the Common Information Model (CIM), the data model used across the electric utility industry to describe power grids. By expressing the relevant parts of CIM as a LinkML schema and running the SQL Validator against it, invalid or inconsistent grid model data can be detected directly in the database with plain SQL — making it easy to integrate validation into existing pipelines without extra tooling.

### More information

- [LinkML SQL Validator Documentation](https://linkml.io/linkml/generators/sqlvalidation.html)
- [My notes on the CIM](/posts/2025/wtf-cim/)
