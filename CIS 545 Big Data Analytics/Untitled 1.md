In pandas, what is the key difference between using single brackets versus double brackets for projection?
- **A:** Single brackets return a DataFrame; double brackets return a Series.
- **B:** Single brackets return a Series; double brackets return a DataFrame.
- **C:** Both return a DataFrame, but single brackets preserve the index.
- **D:** Both return a Series, but double brackets keep column names.  
**Answer:** B  Single brackets like exec_df[‘name’] return a **Series**  while double brackets like exec_df[[[[‘name’, ‘birthday’]]]] return a **DataFrame** containing the listed columns and the index.


Why is using apply on a Series preferable to writing a Python for‑loop?
- **A:** apply allows you to use GPU acceleration while for loops cannot use GPUs.
- **B:** apply allows pandas to optimize execution while explicit loops force sequential execution increasing overhead.
- **C:** apply has increased overhead and runs sequential
- **D:** Its not, for loops can route work through C code paths and process whole chunks at once
Answer: B **apply** lets pandas decide how to execute across data. Iteratng with a for loop enforces sequential exeuction and can be slower using a single-core.

Which join returns only rows where the key values match in both tables?
- A: Left outer join
- B: Right outer join
- C: Full outer join
- D: Inner join
Answer: D **inner join** outputs only matched pairs while outer joins include unmatched rows from the data

What is the difference between record linking and deduplication?
- A: record linking merges all duplicate rows within one table while deduplication links across tables
- B: Record linking joins across different tables based on similarity while deduplication merges duplicates within the same table
- C: Both are functionally identical but use different libraries
- D: Deduplication always uses exact string equality; record linking uses only edit distance
Answer B **Record linking** is joining 2 different tables when entities are similar while depduplication merges duplications in the same table into one

For the word "midterm", how many unique 4 gram usbstrings are generated?
- A: 1
- B: 3
- C: 7
- D: 10
Answer D 
