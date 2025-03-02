# Section 1: Prepare the Data

This section focuses on the essential steps of data preparation using Power Query in Power BI.  It covers connecting to various data sources, shaping and transforming data, and ensuring data quality and consistency for analysis. Key topics include data source connectivity, data transformation techniques, parameterization, and choosing the appropriate connection mode.

## Key Concepts (Section 1)

*   **Data Source Connectivity:** Connecting to diverse data sources like databases, files, and cloud services. Understanding connector capabilities and limitations.
*   **Data Transformation (Power Query):**  Using Power Query Editor to clean, shape, and transform data. Common transformations include filtering, sorting, grouping, merging, appending, pivoting, unpivoting, adding calculated columns, and data type conversions.
*   **Data Profiling:**  Analyzing data quality and identifying issues like missing values, errors, and inconsistencies using Power Query's profiling tools.
*   **Parameterization:** Creating and using parameters to make Power Query queries dynamic and reusable.
*   **Connection Modes:** Understanding and choosing between Import, DirectQuery, and Live Connection modes based on data volume, performance needs, and data freshness requirements.
*   **Data Refresh:**  Understanding the implications of different connection modes on data refresh frequency and methods.

## Table 1.1: Data Source Types and Considerations

| Data Source        | Connectivity Modes | Authentication                               | Security Considerations                                  | Performance Notes                                        | Limitations                                                    |
| ------------------ | ------------------- | ------------------------------------------- | -------------------------------------------------------- | ---------------------------------------------------------- | --------------------------------------------------------------- |
| **SQL Server**     | Import, DirectQuery  | Windows, Database, Microsoft Account        | Encryption, Firewall Rules, Data Gateway                   | Generally good performance, DirectQuery dependent on DB speed | DirectQuery limitations on DAX and transformations              |
| **Excel**          | Import               | Windows (if on network), Anonymous (Web)      | File permissions, Secure storage, Data Gateway (if needed) | Import performance good, dependent on file size and complexity | Limited DirectQuery, no Live Connection                        |
| **Web**            | Import               | Anonymous, Basic, Organizational account    | Website security, Data Gateway (if behind firewall)       | Dependent on website responsiveness and data volume          | Web API limitations, data extraction complexity                |
| **Azure Blob Storage** | Import               | Account key, Shared Access Signature (SAS), OAuth2 | Azure security features, Access control (IAM)             | High performance, scalable storage                              | Large datasets can take time to import                           |
| **SharePoint Folder** | Import               | Organizational account                        | SharePoint permissions, Data Gateway (if needed)          | Dependent on SharePoint performance and file count          | Large folders can be slow, complex structure                     |
| **Power BI Datasets**| Live Connection    | Organizational account                        | Power BI Service security, Workspace permissions          | Optimized for Power BI, fast performance                     | Limited transformations, read-only data model, dependent on source dataset performance |

## Table 1.2: Power Query Parameterization Techniques

| Parameter Type | Use Cases                                       | Creation & Usage in Power Query                                       | Benefits                                                                     |
| -------------- | ------------------------------------------------ | ---------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| **Text**       | Filtering data by text values, dynamic file paths | Manage Parameters -> New Parameter, use in filters, source paths, etc. | Flexibility in queries, reusability, user input for dynamic filtering          |
| **Number**     | Filtering data by numerical ranges, top N filters | Manage Parameters -> New Parameter, use in numerical filters, ranges     | Dynamic numerical filtering, control over thresholds and limits              |
| **Date**       | Filtering data by date ranges, reporting periods | Manage Parameters -> New Parameter, use in date filters, date calculations | Dynamic date filtering, control over timeframes, easy period-over-period analysis |
| **List**       | Dropdown lists for user selection, predefined values | Manage Parameters -> New Parameter (List type), use in filters, dropdowns | User-friendly selection of values, enforces data validation, predefined choices |
| **Binary**     | Accessing binary files, images, documents       | Manage Parameters -> New Parameter (Binary type), used for file access | Dynamically access different binary files, flexibility in file handling        |

## Table 1.3: Connection Mode Comparison: Import, DirectQuery, and Live Connection

| Feature                         | Import                                     | DirectQuery                                   | Live Connection                             |
| ------------------------------- | ------------------------------------------ | --------------------------------------------- | --------------------------------------------- |
| **Data Storage**                 | Data is imported and stored in Power BI model | Metadata only, queries sent to source        | Metadata only, queries sent to source dataset |
| **Data Freshness**               | Dependent on refresh schedule              | Real-time (as current as source database)   | Real-time (as current as source dataset)     |
| **Report Performance**            | Fast for visuals, slower initial import     | Slower visuals (dependent on source)        | Fast, optimized source dataset performance     |
| **Data Volume Handling**          | Limited by Power BI Pro/Premium model size  | Large datasets supported (source database limits) | Large datasets supported (source dataset)       |
| **Feature Set (Power Query)**   | Full Power Query capabilities                  | Limited transformations available              | Very limited transformations                    |
| **DAX Functionality**             | Full DAX functionality                          | Some DAX features may be limited or perform poorly | Very limited DAX capabilities (primarily for measures) |
| **Compatibility**               | Wide range of data sources                 | Limited to specific data sources              | Power BI Datasets, Analysis Services, Azure Analysis Services |
| **Complexity of Setup**          | Moderate                                   | Higher complexity (query optimization, gateway setup)     | Lower complexity (pre-modeled dataset)        |
| **Resource Consumption (Power BI)** | Higher (data storage in-memory)                 | Lower (metadata storage)                    | Lower (metadata storage)                    |
| **Source System Load**           | Lower (data loaded once during refresh)        | Higher (queries sent on each interaction)     | Lower (optimized source dataset)              |
| **Scalability**                 | Power BI capacity scales                 | Source database needs to scale                | Source dataset capacity scales                |
| **Initial Data Load Time**        | Slower, full data load                          | Fast, metadata only load                     | Fast, metadata only load                     |
| **Limitations**                 | Data refresh latency, model size limits     | Performance impact on source, feature limitations | Limited modeling and transformation, dependency on source dataset |
| **Typical Use Cases**            | Interactive analysis, rich visualizations, smaller to medium datasets | Real-time dashboards, large databases, data governance | Reusing existing Power BI datasets, connecting to Analysis Services models |

## Table 1.4: Merge Kind Comparisons

| Merge Kind          | Description                                                                 | Example Scenario                                                                  |
| ------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| **Left Outer**      | All rows from the left table, matching rows from the right table.  Nulls for non-matches from the right. | Combine Sales Transactions (left) with Customer Details (right) - see all sales, include customer info where available. |
| **Right Outer**     | All rows from the right table, matching rows from the left table. Nulls for non-matches from the left. | Combine Product Details (right) with Sales Transactions (left) - see all products, include sales data where available. |
| **Full Outer**      | All rows from both tables. Nulls where rows don't have a match in the other table. | Combine Customer List A and Customer List B to get a complete list of unique customers. |
| **Inner**           | Only rows that have matches in both tables, based on the join columns.        | Combine Sales Transactions and Product Catalog to analyze sales only for products in the catalog. |
| **Left Anti**       | Only rows from the left table that do *not* have a match in the right table.    | Identify customers in Customer Table who *haven't* made any sales in Sales Transactions. |
| **Right Anti**      | Only rows from the right table that do *not* have a match in the left table.   | Identify products in Product Catalog that have *not* been sold in Sales Transactions. |

## Table 1.5: Popular Pre-processing Techniques (Power Query)

| Technique                  | Description                                                                 | Example                                                                         |
| -------------------------- | --------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| **Filtering Rows**         | Selecting specific rows based on criteria.                                  | Keep only sales records from the last year.                                       |
| **Removing Columns**       | Deleting unnecessary columns to simplify the dataset.                         | Remove columns like "Order ID" if not needed for analysis.                      |
| **Changing Data Types**    | Converting columns to appropriate data types (Text, Number, Date, etc.).   | Ensure "Order Date" column is recognized as a Date data type.                  |
| **Replacing Values**       | Substituting specific values with others.                                   | Replace "N/A" with "Unknown" in a "Region" column.                              |
| **Splitting Columns**      | Dividing a single column into multiple columns.                              | Split "Full Name" column into "First Name" and "Last Name" columns.             |
| **Merging Columns**        | Combining multiple columns into a single column.                              | Merge "City" and "State" columns into a "Location" column.                     |
| **Pivoting Columns**       | Transforming unique values in a column into new columns.                      | Pivot "Year" column to create separate columns for each year's sales data.      |
| **Unpivoting Columns**     | Transforming column headers into column values.                             | Unpivot year columns to create "Year" and "Sales" columns for time-series data.  |
| **Adding Custom Columns**  | Creating new columns based on formulas or conditional logic.                  | Add a "Profit Margin" column calculated from "Revenue" and "Cost" columns.    |
| **Grouping Rows**          | Summarizing data by grouping rows based on one or more columns.             | Group sales data by "Region" to calculate total sales per region.                |
| **Appending Queries**      | Combining rows from multiple tables with the same structure.                 | Append sales data from different regional files into a single sales table.      |
| **Merging Queries**        | Combining columns from two tables based on matching columns (join operation). | Merge sales transactions with customer details using a "Customer ID" column.   |

