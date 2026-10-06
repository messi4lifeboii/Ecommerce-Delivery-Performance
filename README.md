# E-commerce Delivery Performance Analytics

## Power BI Business Analyst Portfolio Project

This project presents an end-to-end business analysis of e-commerce delivery performance using Power BI. It examines where delivery delays occur, how late deliveries are associated with customer experience, and which sellers, product categories, and locations should be prioritised for operational improvement.

The project covers the complete Business Analyst lifecycle, from defining the business problem and gathering requirements to preparing data, designing KPIs, building the dashboard, testing the solution, and presenting recommendations.

## Business problem

An e-commerce marketplace needs a consistent view of delivery performance. Management knows that some orders arrive late, but existing reporting does not clearly show:

- Where late deliveries are concentrated
- Which high-volume sellers require intervention
- Which product categories contribute the most late orders
- How delivery performance is associated with customer review scores
- Which KPIs should be monitored during an improvement initiative

## Business question

Which sellers, product categories, locations, and fulfilment stages contribute most to late deliveries, and where should management intervene first to protect customer satisfaction?

## Project objectives

- Measure on-time delivery performance using a documented and repeatable definition.
- Identify the geographic, seller, and product-category concentration of late orders.
- Compare customer review outcomes for on-time and late deliveries.
- Prioritise high-impact improvement opportunities using both order volume and delivery performance.
- Provide an interactive Power BI dashboard for management and operational teams.
- Translate analytical findings into clear, evidence-supported recommendations.

## Key findings

| Finding | Result |
|---|---:|
| Total orders | 99,441 |
| Eligible delivered orders | 96,470 |
| On-time delivery rate | 93.23% |
| Late orders | 6,534 |
| Average days late | 10.62 days |
| Average review score for on-time orders | 4.29 |
| Average review score for late orders | 2.27 |
| One-star review rate for on-time orders | 6.58% |
| One-star review rate for late orders | 53.69% |

Late deliveries were associated with a 2.02-point lower average review score and an approximately eight-times higher one-star review rate. This is an observed association and should not be interpreted as proof that delivery delay alone caused the lower ratings.

The geographic analysis also showed two different operational problems:

- Sao Paulo contributed the highest number of late orders because of its large order volume.
- Rio de Janeiro, Bahia, and Ceara showed more severe proportional delivery-performance issues.

This distinction is important because high-volume areas and high-rate areas require different intervention strategies.

## Dashboard pages

### 1. Executive Overview

Provides a management summary of total orders, on-time delivery rate, late orders, average days late, average review score, monthly performance, state-level performance, and delivery-status distribution.

### 2. Delivery Diagnostics

Explores delay severity, monthly late-delivery trends, state-level performance, and fulfilment timing to help users identify where delivery problems are occurring.

### 3. Customer Impact

Compares customer review outcomes across delivery-status and delay groups. It shows how poor delivery performance is associated with lower ratings and a higher concentration of one-star reviews.

### 4. Seller & Product Analysis

Identifies sellers and product categories requiring attention. Seller comparisons use a minimum-volume threshold to prevent very small sellers from being incorrectly presented as the worst performers.

### 5. Recommendations

Summarises the main findings, proposed operational actions, pilot success measures, and important analytical limitations.

## Data model

The Power BI model uses a star-style structure with two fact tables and supporting dimensions.

### Fact tables

- `fact_orders`: one row per order, including purchase dates, delivery dates, delivery status, delay measures, customer information, and review outcomes.
- `fact_order_items`: one row per order item, including product, seller, price, and freight value.

### Dimension tables

- `dim_products`
- `dim_sellers`
- `dim_customers`
- `dim_geography_zip`

The primary relationship between the two fact tables is:

`fact_orders[order_id]` 1 to many `fact_order_items[order_id]`

Product and seller dimensions filter the order-item fact table using `product_id` and `seller_id`.

## Core KPIs

- Total Orders
- Eligible Delivered Orders
- On-time Delivery Rate
- Late Delivery Rate
- Late Orders
- Average Days Late
- Average Total Delivery Days
- Average Processing Days
- Average Carrier Days
- Average Review Score
- One-star Review Rate
- Freight Value
- Total Item Value

Detailed definitions, populations, denominators, and caveats are available in the [KPI catalogue](05_Data_Model/KPI_Catalogue.md).

## Recommended actions

1. Begin with high-volume sellers that contribute the greatest number of late orders.
2. Review seller processing time, especially the period between order approval and carrier handover.
3. Separate geographic action plans into high-volume contribution and high late-rate workstreams.
4. Track customer review score and one-star review rate as guardrails alongside on-time delivery.
5. Run a controlled operational pilot before estimating financial or retention impact.
6. Investigate known data-quality issues before using the solution in a production environment.

## Tools and techniques

- Power BI Desktop
- Power Query
- DAX
- Python for profiling and data preparation
- SQL validation queries
- Star-schema data modelling
- KPI design and metric documentation
- Requirements gathering and traceability
- User acceptance testing
- Business storytelling and stakeholder recommendations

## Project workflow

| Milestone | Deliverable | Status |
|---|---|---|
| 1 | Project charter and stakeholder analysis | Complete |
| 2 | Business requirements, user stories, and acceptance criteria | Complete |
| 3 | Data assessment and quality report | Complete |
| 4 | Data preparation and reconciliation | Complete |
| 5 | Data model, relationships, KPIs, and DAX measures | Complete |
| 6 | Exploratory analysis and insight summary | Complete |
| 7 | Power BI dashboard | Complete |
| 8 | Testing and UAT documentation | Complete |
| 9 | Portfolio documentation and executive recommendation | Complete |

## Repository structure

```text
Ecommerce_Delivery_BA_Portfolio/
|-- 01_Project_Initiation/
|-- 02_Requirements/
|-- 03_Data_Assessment/
|-- 04_Data_Preparation/
|   `-- powerbi_data/
|-- 05_Data_Model/
|-- 06_Analysis/
|-- 07_PowerBI/
|-- 08_Testing/
|-- 09_Portfolio/
|-- Ecommerce_Delivery_Performance.pbix
|-- PROJECT_TIMELINE.md
`-- README.md
```

## How to open the dashboard

1. Clone or download this repository.
2. Install Power BI Desktop if it is not already installed.
3. Open `Ecommerce_Delivery_Performance.pbix`.
4. Use the report tabs and slicers to explore delivery performance by month, state, seller, product category, and delivery status.
5. If Power BI asks for updated file locations, point the queries to the CSV files inside `04_Data_Preparation/powerbi_data`.

## Supporting documentation

- [Project charter](01_Project_Initiation/Project_Charter.md)
- [Business requirements](02_Requirements/Business_Requirements.md)
- [Data quality report](03_Data_Assessment/Data_Quality_Report.md)
- [Transformation and reconciliation notes](04_Data_Preparation/Transformation_and_Reconciliation.md)
- [Power BI model specification](05_Data_Model/PowerBI_Model_Specification.md)
- [DAX measures](05_Data_Model/DAX_Measures.md)
- [Insight summary](06_Analysis/Insight_Summary.md)
- [Power BI build guide](07_PowerBI/PowerBI_Build_Guide.md)
- [UAT plan and results](08_Testing/UAT_Plan_and_Results.md)
- [Executive recommendation](09_Portfolio/Executive_Recommendation.md)
- [Interview story](09_Portfolio/Interview_Story.md)

## Analytical limitations

- The dataset is historical and represents one Brazilian e-commerce marketplace.
- The analysis identifies associations, not causal effects.
- The dataset does not contain complete logistics cost, profit, customer-support, or lifetime-value information.
- Repeat purchasing is affected by the finite observation period.
- Item-level product analysis should not be interpreted as unique-order analysis because one order can contain multiple items.

## What this project demonstrates

This portfolio project demonstrates the ability to:

- Translate a business problem into measurable analytical requirements
- Prepare and validate multi-table data
- Design a reliable Power BI data model
- Create documented DAX measures and KPIs
- Build clear executive and diagnostic dashboard views
- Balance performance rate with business volume when prioritising action
- Communicate limitations and avoid unsupported causal claims
- Turn analysis into practical business recommendations

## Project status

Completed and ready for portfolio presentation.
