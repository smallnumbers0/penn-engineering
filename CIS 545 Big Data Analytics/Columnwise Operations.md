
- Focus on operations in Pandas and SQL that work with columns—essential building blocks for data cleaning and transformation.
- Example tables: ‎`company_ceos_df` (executive names) and ‎`exec_df` (CEO names with underscores, birthdays).

**Projection**

- Pull out just the columns you need from a DataFrame.
- In Pandas:

- Double brackets (‎`df[['col1', 'col2']]`) return a DataFrame with selected columns.
- Single brackets (‎`df['col1']`) return a Series (a single column, no column header, more like a list).

- Series are handy for iteration, but DataFrames are better for chaining more operations.

**Applying Functions to Columns**

- Instead of looping through rows (which is inefficient), use ‎`apply()` to operate on all elements of a Series or DataFrame.
- Example: Clean up names by replacing underscores with spaces.

- Define a function (‎`to_space`) and use ‎`series.apply(to_space)`.
- Or, use a lambda function for quick, inline operations: ‎`series.apply(lambda x: x.replace("_", " "))`.

- This approach is faster and can leverage multiple cores/processors.

**Row-wise Operations**

- You can apply functions to rows by using ‎`apply()` on the DataFrame with ‎`axis=1`.
- Example: For each row, replace underscores in the ‘name’ column with spaces.

**Assigning Results Back**

- Often, you’ll want to save the results as a new column:  
    ‎`df['clean_name'] = df['name'].apply(lambda x: x.replace("_", " "))`
- You can also rename columns using ‎`rename(columns={'old': 'new'})`.

**Why Not Iterate Directly?**

- For loops are slow and force single-threaded execution.
- ‎`apply()` lets Pandas optimize and potentially parallelize the work.

**Summary of Pandas Operations**

- Projection (select columns)
- ‎`apply()` (apply functions to columns/rows)
- ‎`rename()` (change column names)
- Assigning new columns

**Equivalent Operations in SQL**

- Use ‎`SELECT` to choose columns:  
    ‎`SELECT col1, col2 FROM table`
- Use expressions and ‎`AS` to create/rename columns:  
    ‎`SELECT name, REPLACE(name, '_', ' ') AS clean_name FROM exec`
- The result can be imported into Pandas as a DataFrame.

**Takeaway**

- Columnwise operations are the foundation for cleaning and transforming data in both Pandas and SQL.
- Efficient use of these operations is key for scalable, maintainable data science workflows.