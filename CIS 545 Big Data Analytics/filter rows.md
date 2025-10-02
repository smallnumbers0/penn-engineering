**Rows vs. Columns in Tables**

- Columns have unique names (schema); rows are just tuples of values.
- To work with rows, you filter based on the values they contain.

**Filtering Rows in Pandas**

- Use predicates (conditions) to test each row for inclusion.
- Example: To find the row where ‎`clean_name == "Julie Sweet"`:

- Create a mask (series of True/False) by testing the condition on the column.
- Use this mask to select only matching rows from the DataFrame.
- This produces a filtered DataFrame with just the rows you want.

**Composing Operations**

- You can combine filtering and projection:

- Filter for rows with a specific value, then select (project) just the columns you care about.
- Example: Filter for Julie Sweet, then project the ‎`page` column.

**Filtering Rows in SQL**

- Use ‎`SELECT ... FROM ... WHERE ...` to filter directly in the query.
- Example:  
    ‎`SELECT * FROM temp_exec WHERE clean_name = 'Julie Sweet';`

- Or project a column:  
    ‎`SELECT page FROM temp_exec WHERE clean_name = 'Julie Sweet';`

**Dropping Rows with Missing Data**

- In Pandas, use ‎`dropna()` to remove rows with missing values.

- Can be applied across all columns or just specific ones (e.g., ‎`born` column).

- In SQL, filter with ‎`WHERE born IS NOT NULL`.

**Setting Indexes**

- Use ‎`set_index()` in Pandas to make a column the DataFrame index for easier reference.

**Summary of Table Operations**

- Projection: select columns.
- Selection/filtering: sub-select rows by condition.
- Apply: compute values over columns.
- Update: add new columns with computed values.
- SQL: select columns and filter rows with expressions.