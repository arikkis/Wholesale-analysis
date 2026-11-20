# Why don't wholesale customers come back?
**Customer retention and lifetime value analysis for a gift-candle brand (B2B, 1,140 shops, 2021–2026)**

> Real business project for Candlehand, a gift-candle manufacturer, rebuilt on **synthetic data** to protect the
> company's confidentiality: all names are invented and all amounts changed by up to ±5%. The results closely
> reproduce the real analysis but are not the company's actual figures.

---

## At a glance

| | |
|---|---|
| **Business problem** | Most wholesale shops order once and never return. Which shops come back, when, and what is a new customer worth? |
| **Data** | ERP exports (AWS QuickSight / Odoo): 28,500 invoice lines; after cleaning 2,330 invoices from 1,140 shops in 53 countries |
| **Methods** | Data cleaning · descriptive analysis · logistic regression with confidence intervals and a sensitivity analysis · Kaplan–Meier survival curves · customer lifetime value |
| **Outcome** | Answers to the company's five questions, testable recommendations, and **errors found in the company's reporting pipeline**, which helped the company correct it |

## Key findings

**1. Re-ordering has fallen.** 30% of new shops place a second order within 243 days (the period in which 80% of
all re-orders happen). The rate dropped from 26–35% for shops that started in 2022–2023 to 18–22% in 2024–2025.
At the same time, fewer new shops acquired: 295 in 2022, about 110–150 a year since.


**2. A small group carries the business.** 12% of shops (4+ orders) bring about half of all invoice value,
while two-thirds of shops order only once. This loyal group shrank sharply after 2022: shops with 4+ orders a
year fell from 35 to 5–10, and their loss explains about two-thirds of the fall in yearly sales.

**3. Timing matters more than the first order.** No feature of the first order (channel, value, units, product
mix, country) reliably predicts whether a shop will return. What the data does show clearly is *when* shops
return: half of all re-orders happen within about 3 months, and after a year almost no shop comes back.

**4. A hidden country effect.** At first, larger first orders seemed to predict loyalty. A sensitivity analysis
showed that the effect comes almost entirely from **Italy**: Italian shops with a small first order rarely
returned (11% vs 32–50% for larger orders), while in other countries order size made little difference. Without
Italian shops, the effect disappears.

**5. Channel matters for value.** A direct customer is worth about **3×** as much as one acquired through a
wholesale platform (≈1,940 € vs 460 € of invoice value over three years). Direct shops keep ordering over the
years, while most platform shops stop after their first order.

## Recommendations to the business

- **Prioritise direct buyers.** They bring about three times more value and tend to re-order more often, so they
  deserve more of the sales team's follow-up time than platform shops.
- **Follow up on a fixed schedule.** Contact every new shop **2–3 months** after its first order (when re-orders
  peak), again at about **6 months**, and a last time before **8 months**. Italian shops return more slowly, so
  allow them a longer period before treating them as lost.
- **Test.** Shops whose first order covered several product categories re-ordered more often (34%
  vs 23%), and shipping costs may affect re-ordering. Both are worth testing (e.g. a mixed starter assortment;
  comparing shops just below and above the free-shipping threshold) before changing the sales policy.
- **Watch the promising markets and clarify Italy.** Lithuania and Belgium show above-average re-ordering, while
  Italy, the second-largest market, has placed no orders in 2026 – worth checking with the business.

## Skills demonstrated

- **Messy real-world data:** reconciling two inconsistent ERP exports, identifying shops behind marketplace
  orders, filling missing countries with a documented, auditable process.
- **Data-quality investigation:** found that invoice amounts mixed VAT, shipping and platform commission; this
  was reported to the person responsible for the AWS data pipeline and helped correct it.
- **Statistics with honest uncertainty:** confidence intervals, joint tests, multicollinearity checks, a
  sensitivity analysis (with/without Italy), and survival analysis for censored data.
- **Business communication:** a short report with conclusions and testable recommendations for non-technical
  readers.
- **Reproducibility and privacy:** one configurable notebook (*Restart & Run All*, built-in data checks) and a
  synthetic dataset that keeps the analysis intact while protecting customers' and the company's data.

## What's in this repository

| File | What it is |
|---|---|
| [`Candlehand_wholesale_report.docx`](Candlehand_wholesale_report.docx) | **The report** (10-minute read): findings, figures, recommendations, limitations |
| [`candlehand_final_report_synthetic.ipynb`](candlehand_final_report_synthetic.ipynb) | **The full analysis**, from raw data to every figure and number in the report |
| `data_synthetic.csv`, `Total_synthetic.xlsx` | Synthetic sales and ERP exports (input data) |
| `shop_country_lookup_synthetic.xlsx` | Documented country lookup for shops without a country |
| `unknown_country_shops_synthetic.xlsx` | Shops still without a country (written by the notebook) |
| `figures_synthetic/` | All figures, saved by the notebook |


## Limitations

Synthetic data (close to, not identical with, the real results) · invoice value is not revenue · shop identity
rests on names · findings are associations, not causes.

---

**Author:** Arkadij Kisielius
