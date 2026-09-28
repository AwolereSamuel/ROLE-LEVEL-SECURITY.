# EXECUTIVE SUMMARY 

This report presents the development and implementation of a Power BI-based Business Sales Dashboard with Row-Level Security (RLS). The solution was developed to provide an interactive environment for monitoring sales performance while ensuring that users can access only the business information authorized for their respective locations. The Power BI solution integrates sales information with user and geographic mapping structures to support both business intelligence reporting and controlled data access. The dashboard provides key performance indicators covering total sales, total quantity, total orders, average order value, and total products. It also provides analytical views of sales performance across time, states and cities, products, categories, and sales channels.

A major component of the solution is the implementation of dynamic Row-Level Security. The security design uses the identity of the logged-in Power BI user to determine the geographical data that the user is permitted to access. This approach provides a more scalable alternative to manually creating separate security rules for individual users or locations. The report also documents the distinction between static and dynamic RLS, the purpose of USERPRINCIPALNAME(), and the expected behavior when a user's identity is not present in the authorized user-mapping table.

Overall, the solution demonstrates the application of Power BI for interactive business reporting, data visualization, geographic sales analysis, and controlled access to business information. Further enhancements recommended include the introduction of profitability measures, growth analysis, stronger RLS testing documentation, data-quality controls, and additional executive-level performance indicators.

## PROBLEM STATEMENT

Organizations generate large volumes of sales data from different products, locations, customers, and sales channels. When such data is stored and analyzed without an effective business intelligence solution, management may experience difficulty in obtaining timely and meaningful information about sales performance. Traditional methods of reviewing raw datasets or manually preparing reports can also make it difficult to identify trends, compare geographical performance, monitor products, and evaluate the contribution of different sales channels. Another major challenge is the management of access to sensitive business information. In an organization operating across different states or regions, not every employee should have unrestricted access to all sales records. For example, a regional manager may require access to the sales information of a particular state without necessarily having access to the sales information of other regions. Without appropriate access controls, sensitive business information may be unnecessarily exposed to unauthorized users.

The absence of an interactive reporting and security solution can therefore result in several challenges, including difficulty in monitoring sales performance, limited visibility into regional and product-level performance, inefficient decision-making, and potential exposure of confidential business information. To address these challenges, a Power BI-based Business Sales Dashboard with Row-Level Security was developed. The solution transforms sales data into interactive visual reports containing key performance indicators, geographical analysis, product analysis, category analysis, channel analysis, and time-based sales trends. In addition, dynamic Row-Level Security is incorporated to restrict users to the business information they are authorized to access.

The project therefore addresses two major business requirements: effective sales-performance analysis and controlled access to business data.

## OBJECTIVES

The purpose of this report is to document the development of the Power BI Sales Dashboard and its associated Row-Level Security implementation.

The report provides information on:

(i) The structure of the Power BI solution.

(ii) The sales-performance dashboard.

(iii) The key performance indicators used.

(iv) The analytical visualizations developed.

(v) The implementation of Row-Level Security.

(vi) The distinction between static and dynamic RLS.

(vii) The role of USERPRINCIPALNAME().

(viii) User-access scenarios.

(ix) Areas for further improvement.

(x) Recommendations for future development.

## TOOLS AND TECHNOLOGIES

The following tools and technologies were used or are relevant to the implementation of the Power BI solution.

1. Microsoft Power BI Desktop

Microsoft Power BI Desktop is the primary development platform used for creating the sales dashboard.

It provides capabilities for:

- Data modelling

- Data transformation

- Data visualization

- Dashboard development

- DAX calculations

- Relationship management

- Row-Level Security configuration

Power BI provides the environment in which the sales dataset is transformed into an interactive business intelligence solution.

2. Power Query

Power Query is used within Power BI for data preparation and transformation.

It can be used to perform operations such as:

- Removing unnecessary records

- Renaming columns

- Changing data types

- Handling missing values

- Standardizing data

- Creating calculated transformation columns

- Preparing datasets before loading them into the data model

Proper data preparation is important because the quality of the dashboard depends heavily on the quality and consistency of the underlying data.

3. DAX - Data Analysis Expressions

DAX (Data Analysis Expressions) is used to create calculations and analytical measures within Power BI.

The project uses DAX concepts for calculating and displaying business performance indicators.

Examples include:

- Total Sales

- Total Quantity

- Total Orders

- Average Order Value

- Total Products

DAX is also important to the security implementation, particularly through the use of:

USERPRINCIPALNAME()

This function enables the report to identify the current user's identity and use that information as part of the dynamic RLS implementation.

4. Power BI Data Model

The Power BI data model provides the structural foundation of the project.

The model incorporates business information relating to:

- Sales

- Users

- Geographic/state mapping

- Security relationships

The relationships between these components allow sales information to be filtered according to the authorized user.

The conceptual security flow is:

User Identity → User Mapping → State/Region → Sales Records

5. Row-Level Security

Row-Level Security (RLS) is the principal security technology applied in the project.

RLS controls the rows of data that individual users are allowed to view.

The project demonstrates the concept of dynamic RLS, where a user's identity determines the information that becomes available to that user.

This is particularly useful for organizations where managers or employees are responsible for specific geographical regions.

6. USERPRINCIPALNAME()

The DAX function:

USERPRINCIPALNAME()

is used as part of the dynamic RLS architecture.

It returns the User Principal Name of the current user.

The value can then be matched against the user-mapping table to determine the user's authorized geographical area.

For example:

User UPN
   ↓
Authorized State
   ↓
State Mapping
   ↓
Sales Records

This approach eliminates the need to manually create an independent security filter for every individual user.

7. Power BI Visualizations

The dashboard makes use of different Power BI visualization types to communicate sales information.

These include:

- KPI cards

- Line charts

- Bar/column charts

- Donut charts

- Matrix visual

- Slicers

Each visualization serves a specific analytical purpose.

8. Power BI Service

The Power BI Service is relevant to the deployment and administration stage of the solution.

After publishing the report, the Power BI Service can be used for:

- Report sharing

- Dataset management

- Workspace management

- RLS role assignment

- User access management

- Security testing

The Power BI Service therefore provides the environment through which the developed report can be made available to authorized organizational users.

## ROW LEVEL SECURITY (RLS)

DYNAMIC ROW-LEVEL SECURITY

Dynamic RLS determines access based on the identity of the current user.

Instead of creating a separate role for every geographical location, the user's identity is matched against a user-mapping table.

A common implementation uses:

Users[Email] = USERPRINCIPALNAME()

The user's identity is then associated with an authorized state or region.

This approach provides a more scalable security structure.

The conceptual flow is:

Logged-in User

      ↓

USERPRINCIPALNAME()

      ↓

Users Table

      ↓

Authorized State

      ↓

State Mapping

      ↓

Sales Table

      ↓

Authorized Sales Records

## CONCLUSION

The Power BI Sales Dashboard and Row-Level Security project provides a practical solution for transforming sales data into an interactive business intelligence environment while incorporating controlled access to sensitive business information. The dashboard provides users with important information about sales performance through key performance indicators, geographical analysis, product analysis, category analysis, sales-channel analysis, and time-based reporting. The use of interactive slicers further enables users to investigate specific aspects of business performance based on their reporting requirements.

The implementation of Row-Level Security adds an important security dimension to the solution. Through dynamic RLS and the use of USERPRINCIPALNAME(), the system can associate a user's identity with an authorized geographical area and restrict access to the corresponding sales records. This approach provides a scalable foundation for managing access in organizations where users have different reporting responsibilities. Although the current solution provides a strong foundation, further improvements can increase its value as an enterprise business intelligence solution. These improvements include introducing profitability and growth measures, strengthening data-quality controls, conducting comprehensive RLS testing, improving security documentation, and expanding the dashboard with additional management-level insights.

In conclusion, the project demonstrates the practical application of Power BI, DAX, data modelling, interactive visualization, and Row-Level Security in solving real-world business reporting and data-access challenges. With the recommended enhancements, the solution can be further developed into a more comprehensive, secure, and decision-oriented business intelligence platform.
