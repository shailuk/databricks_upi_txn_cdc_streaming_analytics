# Databricks UPI transaction CDC (Change Data Capture) Streaming Analytics <br/>

## Tech Stack
* Databricks
* PySpark Structured Streaming
* Delta Lake (Change Data Feed)
* Unity Catalog

---

## Pipeline Architecture

* CDC-Enabled Raw Table:** `raw_upi_transactions_v1` with Delta CDF, comprehensive schema (device, location, demographics, fees)
* Real-Time CDC Processing:** Read change feed (insert/update/delete), CDC-aware aggregations using multiplier logic (+1/-1)
* Merchant Aggregations (Hourly):** Transactions, success/failure/refund counts, amounts, net value, fees, commissions, unique customers
* Idempotent Upserts:** Delta MERGE on composite keys (merchant_id, date, hour) for safe, repeatable writes

---

## Operations, Testing & BI

* Mock CDC Generator:** Continuous INSERT/UPDATE/DELETE cycles with realistic distributions for robust pipeline testing
* Ops & Monitoring:** Checkpointed streams, batch logging, recoverability, and clearly documented run order
* Ready for BI:** Low-latency curated tables for merchant performance dashboards and operational KPIs
