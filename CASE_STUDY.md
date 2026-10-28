# Case Study — Brazilian E-Commerce | Sales & Customer Insights (R)

**Author:** Thiago Andrade | **Status:** educational portfolio project | **Dataset:** [Olist Brazilian E-Commerce (Kaggle)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce), historical orders (2016–2018).

## 1. Introduction / Business context
This project investigates how product sales, geography, delivery timeliness and customer evaluations are related within a historical e-commerce dataset. The modeled scope is **delivered orders that contain items**.

## 2. Problems / Questions
- How did product GMV change month to month?
- Which customer states account for the most product GMV?
- How do customer ratings vary between on-time and late deliveries?
- How many customers in the observed sample placed multiple delivered orders?

## 3. Data and methodology
The Quarto report documents joining orders, items, customers and review data and producing tables for monthly sales, states, delivery satisfaction, repeat customers and data quality. Its approach aggregates order items first and retains one review per order. Tools documented: **R, readr, dplyr, lubridate, ggplot2, knitr and Quarto**.

**Metric definitions:** GMV = sum of item `price` (excluding shipping); delivery timeliness compares delivery date with estimated delivery date when dates are known; observed repeat purchases are not cohort retention.

## 4. Proposed solutions and alternatives
| Option | Potential value | Limitations |
| --- | --- | --- |
| Operations: inspect late deliveries by state and month | Directs investigation to higher-risk segments | Additional logistics data is needed to explain causes |
| Customer experience: investigate late deliveries with low ratings | Connects experience indicators | Association does **not** prove lateness caused poor ratings |
| Commercial: study high-GMV regions and acquisition cohorts | Guides segmentation hypotheses | Historical windows are incomplete and not current |

These are proposed investigations, **not business improvements already delivered**.

## 5. Conclusions
The published Quarto source sets out an analysis framework linking commercial performance, on-time delivery and satisfaction. Without a controlled comparison or supplementary data, the study cannot identify causal effects or current market trends. The code and source must be checked before claiming quantitative results.

## 6. Next steps
1. **BI/analytics:** make the pipeline and output tables easy to reproduce, document source versions and validate one row per order.
2. **Operations:** investigate regions/months with late deliveries and collect operational context.
3. **Customer experience:** review qualitative reasons for low-rated orders and validate alternative explanations.
4. **Management:** prioritize a pilot and define measurable follow-up indicators.

**Artifacts:** [Quarto source](./relatorio.qmd) · [Monthly GMV figure](./01_gmv_mensal.png) · [States figure](./02_gmv_estados.png) · [Delivery-rating figure](./03_avaliacao_entregas.png) · [Rendered report source](./index.html).

> **Reproduction note:** at the time this case study was written, the repository includes the Quarto source and exported figures, but the input CSVs, output tables and referenced R analysis script are not all present in the public root. Therefore a fully reproducible run has not been verified.
