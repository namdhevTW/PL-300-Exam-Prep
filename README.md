# Microsoft PL-300 Exam Study Summary: Data Analyst Associate
This document provides a comprehensive study summary for the Microsoft PL-300 exam, "Data Analyst Associate." It is organized into the four main sections of the exam, summarizing key concepts, techniques, and best practices. Each section includes relevant tables to highlight and compare important topics for exam preparation.

# Comprehensive PL-300 Exam Preparation

This document summarizes key information for the PL-300 exam, organized by typical exam sections, including data preparation, data modeling, data visualization and analysis, and deployment/maintenance.
This does not substitute for the official Microsoft Learn course. Hence I am requesting the audience to <ins>**go through the below before referring**</ins> to the exam summary:
*   **[Microsoft learn course](https://learn.microsoft.com/en-us/training/courses/pl-300t00#course-syllabus)**
*   **[Take practice tests and score a minimum of 85% before going through this list](https://learn.microsoft.com/en-us/credentials/certifications/data-analyst-associate//?practice-assessment-type=certification)** 

Review these concepts, techniques, and best practices, and utilize the tables for quick reference and comparison during your exam preparation. Good luck!

**Table of Contents**

 *   [Section 1: Prepare the Data](Section%201%20(Prepare%20the%20data)/section-1.md)
     *   [Key Concepts (Section 1)](Section%201%20(Prepare%20the%20data)/section-1.md#key-concepts-section-1)
     *   [Table 1.1: Data Source Types and Considerations](Section%201%20(Prepare%20the%20data)/section-1.md#table-11-data-source-types-and-considerations)
     *   [Table 1.2: Power Query Parameterization Techniques](Section%201%20(Prepare%20the%20data)/section-1.md#table-12-power-query-parameterization-techniques)
     *   [Table 1.3: Connection Mode Comparison: Import, DirectQuery, and Live Connection](Section%201%20(Prepare%20the%20data)/section-1.md#table-13-connection-mode-comparison-import-directquery-and-live-connection)
     *   [Table 1.4: Merge Kind Comparisons](Section%201%20(Prepare%20the%20data)/section-1.md#table-14-merge-kind-comparisons)
     *   [Table 1.5: Popular Pre-processing Techniques (Power Query)](Section%201%20(Prepare%20the%20data)/section-1.md#table-15-popular-pre-processing-techniques-power-query)
 *   [Section 2: Model the Data](Section%202%20(Model%20the%20data)/section-2.md)
     *   [Key Concepts (Section 2)](Section%202%20(Model%20the%20data)/section-2.md#key-concepts-section-2)
     *   [Table 2.1: Relationship Cardinality and Cross-filter Direction](Section%202%20(Model%20the%20data)/section-2.md#table-21-relationship-cardinality-and-cross-filter-direction)
     *   [Table 2.2: Relationship Types: Active vs. Inactive](Section%202%20(Model%20the%20data)/section-2.md#table-22-relationship-types-active-vs-inactive)
     *   [Table 2.3: DAX Evaluation Context: Filter Context vs. Row Context](Section%202%20(Model%20the%20data)/section-2.md#table-23-dax-evaluation-context-filter-context-vs-row-context)
     *   [Table 2.4: Popular DAX Functions and Usage](Section%202%20(Model%20the%20data)/section-2.md#table-24-popular-dax-functions-and-usage)
     *   [Table 2.5: Performance Optimization Techniques (Power BI---Modeling)](Section%202%20(Model%20the%20data)/section-2.md#table-25-performance-optimization-techniques-power-bi--modeling)
     *   [Table 2.6: RLS Types Comparison](Section%202%20(Model%20the%20data)/section-2.md#table-26-rls-types-comparison)
     *   [Table 2.7: RLS Implementation Steps](Section%202%20(Model%20the%20data)/section-2.md#table-27-rls-implementation-steps)
 *   [Section 3: Visualize and Analyze the Data](Section%203%20(Visualize%20and%20Analyze%20the%20Data)/section-3.md)
     *   [Key Concepts (Section 3)](Section%203%20(Visualize%20and%20Analyze%20the%20Data)/section-3.md#key-concepts-section-3)
     *   [Table 3.1: Report Interactivity Features](Section%203%20(Visualize%20and%20Analyze%20the%20Data)/section-3.md#table-31-report-interactivity-features)
     *   [Table 3.2: Filtering Methods in Power BI Reports](Section%203%20(Visualize%20and%20Analyze%20the%20Data)/section-3.md#table-32-filtering-methods-in-power-bi-reports)
     *   [Table 3.3: Accessibility Best Practices for Power BI Reports](Section%203%20(Visualize%20and%20Analyze%20the%20Data)/section-3.md#table-33-accessibility-best-practices-for-power-bi-reports)
     *   [Table 3.4: Visualization Table](Section%203%20(Visualize%20and%20Analyze%20the%20Data)/section-3.md#table-34-visualization-table)
     *   [Table 3.5: Capability Comparison: Power BI Desktop vs. Power BI Service](Section%203%20(Visualize%20and%20Analyze%20the%20Data)/section-3.md#table-35-capability-comparison-power-bi-desktop-vs-power-bi-service)
     *   [Table 3.6: Visual Calculation Types and Use Cases](Section%203%20(Visualize%20and%20Analyze%20the%20Data)/section-3.md#table-36-visual-calculation-types-and-use-cases)
     *   [Visual Calculation Types and Use Cases](Section%203%20(Visualize%20and%20Analyze%20the%20Data)/section-3.md#visual-calculation-types-and-use-cases)
 *   [Section 4: Deploy and Maintain Assets](Section%204%20(Deploy%20and%20Maintain%20Assets)/section-4.md)
     *   [Key Concepts (Section 4)](Section%204%20(Deploy%20and%20Maintain%20Assets)/section-4.md#key-concepts-section-4)
     *   [Dataflows](Section%204%20(Deploy%20and%20Maintain%20Assets)/section-4.md#dataflows)
     *   [Content Endorsement and Certification](Section%204%20(Deploy%20and%20Maintain%20Assets)/section-4.md#content-endorsement-and-certification)
     *   [Table 4.1: Workspace Roles and Permissions](Section%204%20(Deploy%20and%20Maintain%20Assets)/section-4.md#table-41-workspace-roles-and-permissions)
     *   [Table 4.2: Data Refresh Types and Configuration](Section%204%20(Deploy%20and%20Maintain%20Assets)/section-4.md#table-42-data-refresh-types-and-configuration)
     *   [Table 4.3: Gateway Types: On-premises vs. Personal Gateway](Section%204%20(Deploy%20and%20Maintain%20Assets)/section-4.md#table-43-gateway-types-on-premises-vs-personal-gateway)
     *   [Table 4.4: Capability Comparison: Power BI Pro vs. Premium](Section%204%20(Deploy%20and%20Maintain%20Assets)/section-4.md#table-44-capability-comparison-power-bi-pro-vs-premium)
     *   [Table 4.5: Performance Optimization Techniques (Power BI---Deployment--Maintenance)](Section%204%20(Deploy%20and%20Maintain%20Assets)/section-4.md#table-45-performance-optimization-techniques-power-bi--deployment--maintenance)
     *   [Table 4.6: Dataflow Concepts and Comparison](Section%204%20(Deploy%20and%20Maintain%20Assets)/section-4.md#table-46-dataflow-concepts-and-comparison)
     *   [Table 4.7: Content Endorsement and Certification Comparison](Section%204%20(Deploy%20and%20Maintain%20Assets)/section-4.md#table-47-content-endorsement-and-certification-comparison)
