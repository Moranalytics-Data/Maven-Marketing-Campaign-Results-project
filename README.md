## **Maven Marketing Campaign Results project**

### 📄 **Overview**

This project employs a prepared dataset from Maven Analytics that includes various demographics for a group of international customers, along with details of their purchasing habits and their responses to a series of recent “Maven Marketing” campaigns.

The project prompts recommend that any analysis should include a profile of the customer base, an evaluation of best-selling products, a comparison among the various sales channels, a ranking of campaign successes, and a specific focus on factors related to the number of web purchases.

### 🧰 **Tools used**

Microsoft Excel (PowerQuery, PivotTables, Slicers)

### 📂 **Dataset**

Marketing campaign data of 2,240 customers

### 🧹 **Data Preparation**

Being a prepared dataset seemingly targeted at less experienced analysts, the data did not require extensive cleaning.

-	Approximately 1% of the records lacked **Income** information; this percentage was deemed adequately low to omit these customers from financial calculations.
One income figure of $666,666 was dismissed, both for its status as an outlier and for the near-certainty that it was an unserious entry.
-	Similarly, frivolous entries into the **Marital Status** category such as “Absurd” and “YOLO” were discounted.
-	The dataset included family data fields for both **Kids** and **Teens**, raising the question of whether the latter was intended as a subset of the former. An evaluation of the data concluded that these were indeed intended as separate categories. (There were instances, for example, in which the teens figure exceeded the kids figure, indicating that the latter was not meant to reflect an overall total of children.)
-	The **Education** variable required some interpretation. Reflective of the customers’ international makeup, the categories—particularly “2n Cycle” and “Basic”—employed some terminology not typically used in the United States.
Based on an assumption that the report was intended for presentation in the U.S.—and based on online research into the definition of these terms—a helper column was created to clarify the response terminology as necessary:

| Original | Reclassified |
|---|---|
| Basic	| High School |
| Graduation |	Bachelor’s |
| Master |	Master’s |
| 2n Cycle |	Master’s |
| PhD |	PhD |

### 🔍 **Analysis Process**
-	The dashboard’s **customer profile** charts were based on traditional PivotTables.
-	Because the dataset’s orientation of **product purchase information** did not lend itself to easy conversion into a bar chart, various methods were applied. Initially, PowerQuery was used to unpivot the columns in question in order to generate the necessary totals in a desired orientation, but the results could not then be connected to the country-based slicer already established for the customer-demographic tables.
    - Ultimately, a **helper table** was built with a series of GETPIVOTDATA formulas in order to create a reoriented table better suited to adapt into the necessary bar chart — but that would still remain responsive to the country slicer.
-	A similar approach would be applied to the columns that tracked customers’ acceptance of **Maven Marketing’s various campaigns**, such that the required calculations could be oriented for adaptation into a bar chart.**

    - (Subsequent research would reveal other, more simple approaches to creating such a helper table, including the use of basic INDEX formulas, as well as dynamic array formulas employing dot notation.)
-	Regarding **web purchases**, initial investigations — using Excel’s “Correlation” Data Analysis tool — suggested possible connections with wine purchases in particular (which would seem to make some intuitive sense). However, an Excel “Regression” analysis found a heteroskedastic relationship between those variables that would seem to indicate that there was not, in fact, a significant relationship between web purchases and wine purchases.
-	More convincing, however, was — somewhat surprisingly — a statistical **relationship between web purchases and in-store purchases**, indicating that the former did not preclude the latter, as might be speculated.

### 📊 **Dashboard Design**
The dashboard endeavors to walk the user through a basic series of questions:
-	**Who is our (Maven Marketing’s) customer?**  _Customer demographics (column charts)._
-	**What are they buying?**  _Most-purchased items (bar chart)._
-	**How are they buying it?**  _Sales channels by percentage (pie chart)._
-	**How are we reaching them?**  _Highest campaign responses (bar chart)._
-	**Which customers are buying things online?**  _Most significant correlations with web purchases (column & pie charts)._
All charts are connected by slicer to allow the user to select from among the countries within the Maven Marketing campaign area.
### 🎯 **Key Insights & Recommendations**
-	An **average customer** is likely in their 40s or 50s, married and with a single child. They are not characterized by a specific income range—their annual income is almost as likely to be in the $30,000s as it is in the $60,000s (and all ranges in between). They will almost assuredly have had some higher education, most likely with a bachelor’s degree.
-	Overall, and in every individual country, wine is the **top seller**, followed by meat and then gold.•	In-store purchases are by far the most successful sales channel; catalog purchases and purchases made through promotions are roughly comparable as the least successful.
-	After decent response to **Maven Marketing’s first campaign**, customer interest dropped off sharply. It bounced back to consistent levels thereafter, but has seen a particularly sharp uptick with Maven’s most recent campaign, which was by far its most successful.
-	Surprisingly, it does not appear that customers who make purchases online are doing so exclusively: There appears to be a correlation between **online and in-store purchases**. If increased online engagement is a desired outcome, more in-store marketing for the website should be considered, perhaps touting online-exclusive offers that could supplement the in-store experience.
- Data also suggests that **customers in relationships**, both married and otherwise, are a significantly larger portion of the base than those not in relationships. Perhaps outreach more specifically targeted to the single/divorced/widowed demographic(s) could be considered.
### 💡 **Reflection/Learning Outcomes**
- This project offered further proof of **PowerQuery’s abilities** to simply perform certain actions that would be far more complex (and far less elegant) when done in Excel, itself.
- In the process of assembling this dashboard, I learned more about **how slicers perform** — and (through trial and error) how they will only connect to PivotTables that share the same pivot cache.
- I also gained additional insight into the pros and cons of **basing charts on PivotTables, versus regular Excel tables**. This led to further research into methods by which the respective functionalities of both options can be combined.
- (It’s a bit frivolous, but I also learned the downside of using a **dark dashboard background**—and how, as a result, charts with no fills can be even more temperamental about being selected and moved than regular charts are.)
