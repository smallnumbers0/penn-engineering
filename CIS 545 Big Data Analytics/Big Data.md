## **Common Myths in Big Data Analytics**

- Many believe big data is just about collecting lots of data, running algorithms, and scaling up computation.
- Reality: The process is much more complex; raw data is rarely ready for direct analysis.

- **Key Challenges in Big Data**

- Data often needs to be modeled, cleaned, and integrated before analysis.
- Managing and assembling data is as important as building predictive models.
- The process involves multiple computational fields: distributed computing, distributed algorithms, machine learning, and data ethics.

- **Course Structure**

- Two main parts:

1. **Part 1:** Handling raw data (structuring, cleaning, integrating)
2. **Part 2:** Building machine learning models on processed data

- **Initial Data Handling**

- Raw data: observations/measurements from the real world.
- Tasks:

1. Structure the data
2. Clean and integrate from multiple sources
3. Transform into a usable format (like a large spreadsheet)
4. Feature extraction for modeling (descriptive, inferential, predictive)

 **Defining “Big” in Big Data**

- No fixed threshold (not just about number of rows or total size).
- Data is “big” if:

1. Too complex for a human to fully comprehend
2. Has many parameters, complex relationships, or high dimensionality
3. Doesn’t fit in a single computer’s memory (e.g., >16GB)

 **Analysis Beyond Brute Force**

- Big data requires more than naive algorithms.
- Need for scalable, efficient, and intelligent computational techniques.
- Must use multiple machines, handle high-dimensional and fast-changing (high-velocity) data.

 **Importance of Context and Metadata**

- Data without context is meaningless (e.g., three bytes: 66, 105, 103 could mean anything).
- Metadata, typing, and provenance (origin of data) are critical for understanding and using data properly.
- Example: Knowing what a table’s columns represent and the population sampled is key for fair, representative analysis.

 

 **Preprocessing and Integration**

- Data may come from tables, PDFs, or images; must be extracted, cleaned, and modeled.
- Linking data from different sources (co-registration/record linking) is often necessary.
- Example: Combining cat images, gene sequences, and breed data; linking taxi pickup/dropoff locations to neighborhoods.

- **Record Linking and Co-Registration**

- Connecting complementary data about the same entities (e.g., linking GPS coordinates to addresses and neighborhoods).
- Enables richer, more meaningful analysis.

- **Distributed and Fragmented Data**

- Big data is often scattered across systems, organizations, file types, and databases.
- Extraction, modeling, cleaning, and linking are needed to unify data for analysis.

- **Exploratory Data Analysis**

- Early analysis of source data files helps verify correct integration and extraction steps.

 **Summary**

- The first part of the course focuses on transforming messy, scattered data into structured, integrated datasets ready for analysis.
- Understanding the context, provenance, and structure of data is essential for effective big data analytics.