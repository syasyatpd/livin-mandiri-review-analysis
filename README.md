# Livin' by Mandiri Review Analysis: Google Play Store Scraping and Rating-Based Sentiment Categorization
 
Data scraping project that collects user reviews of the Livin' by Mandiri app from Google Play Store, filters them by date range, and categorizes sentiment as positive, neutral, or negative. The final dataset contains 8,231 reviews from June 14 to August 17, 2025, complemented by a keyword analysis of the complaints found in negative reviews.
 
## Project Overview
 
| Item | Detail |
|---|---|
| **App** | Livin' by Mandiri (`id.bmri.livin`) |
| **Source** | Google Play Store (language: Indonesian, country: Indonesia) |
| **Review period** | June 14, 2025 – August 17, 2025 |
| **Reviews retrieved** | 274,441 |
| **Reviews after date filter** | **8,231** |
| **Average rating (analyzed reviews)** | 3.58 / 5.0 |
| **Output** | Excel workbook `livin_reviews_analysis.xlsx` (7 sheets) |
 
### App Snapshot at Scraping Time
 
| Metric | Value |
|---|---|
| Overall Play Store rating | 4.10 / 5.0 |
| Total reviews | 292,096 |
| Total downloads | 10,000,000+ |
| App version | 3.1.0 |
 
## Objectives
 
- Collect user reviews of Livin' by Mandiri from Google Play Store.
- Filter reviews to a defined date range.
- Categorize reviews into positive, neutral, and negative groups.
- Identify the most frequent complaint topics in negative reviews.
## Tools
 
| Category | Tools |
|---|---|
| **Language** | Python 3.12 |
| **Libraries** | google-play-scraper 1.2.7, pandas 2.2.2, openpyxl |
| **Environment** | Jupyter Notebook (`PENDAHULUAN.ipynb`) |
| **Output format** | Excel (`.xlsx`) |
 
## Workflow
 
| Stage | Activity |
|---|---|
| **1. App information** | Retrieved app metadata (title, rating, total reviews, downloads, version, last update) with `app()` |
| **2. Review scraping** | Retrieved reviews with `reviews_all()` using `lang='id'`, `country='id'`, and `Sort.NEWEST` (274,441 reviews in the run) |
| **3. Data processing** | Selected 6 columns, renamed them, converted dates, and applied the date filter (274,441 → 8,231 reviews) |
| **4. Categorization** | Assigned each review to a sentiment category based on its star rating, and added review length |
| **5. Keyword detection** | Flagged six complaint topics using keyword matching on review text |
| **6. Statistics and export** | Calculated summary statistics and exported seven sheets to Excel |
 
## Sentiment Categorization
 
| Category | Rule |
|---|---|
| **Negative** | Rating 1–2 ★ |
| **Neutral** | Rating 3 ★ |
| **Positive** | Rating 4–5 ★ |
 
Categories follow the star rating given by each user. The review text is not classified by a language model.
 
## Complaint Keyword Categories
 
Keyword matching is applied to the lowercase review text. A review can match more than one category.
 
| Category | Keywords |
|---|---|
| **Error** | `error`, `eror`, `gagal` |
| **Slow performance** | `lambat`, `lemot`, `lelet`, `lag` |
| **Login** | `login`, `log in`, `masuk` |
| **Crash** | `crash`, `force close`, `tutup sendiri`, `keluar sendiri` |
| **Maintenance** | `maintenance`, `perbaikan`, `gangguan` |
| **Customer service** | `cs`, `customer service`, `layanan`, `komplain` |
 
## Output Structure
 
| Sheet | Content |
|---|---|
| **Info_Aplikasi** | App metadata, scraping timestamp, and date filter |
| **Statistik_Umum** | Total reviews, average rating, and counts and shares per sentiment category |
| **Analisis_Kata_Kunci** | Keyword counts and shares within negative reviews |
| **Rating_per_Bulan** | Review count per month and sentiment category |
| **All_Reviews** | All 8,231 reviews with rating, date, text, thumbs-up count, app version, category, review length, and keyword flags |
| **Review_Negatif** | Negative reviews only, for deeper analysis |
| **Top_50_Reviews** | 50 reviews with the highest thumbs-up count |
 
## Key Findings
 
### Rating Distribution
 
| Category | Reviews | Share |
|---|---|---|
| **Positive (4–5 ★)** | 5,056 | 61.4% |
| **Neutral (3 ★)** | 494 | 6.0% |
| **Negative (1–2 ★)** | 2,681 | 32.6% |
 
### Complaint Topics in Negative Reviews (n = 2,681)
 
| Topic | Reviews | Share of negative reviews |
|---|---|---|
| **Login** | 625 | 23.3% |
| **Slow performance** | 357 | 13.3% |
| **Error** | 280 | 10.4% |
| **Maintenance** | 216 | 8.1% |
| **Customer service** | 177 | 6.6% |
| **Crash** | 48 | 1.8% |
 
### Other Observations
 
| Aspect | Finding |
|---|---|
| **Rating gap** | The average rating of reviews in this period (3.58) is lower than the app's overall Play Store rating (4.10). |
| **Top complaint** | Login is the most frequent topic, mentioned in 23.3% of negative reviews. Crash is the least frequent (1.8%). |
| **Most-liked negative reviews** | The most-liked negative review (3,845 thumbs-up, July 22, 2025) addresses transaction notification settings for incoming and outgoing funds. The next two (328 and 211 thumbs-up, late June 2025) describe being unable to log in and being unable to open the app after an update. |
 
## Recommendations
 
| Recommendation | Supporting data |
|---|---|
| Prioritize the login and access flow | Login is the top complaint topic: 625 of 2,681 negative reviews (23.3%) |
| Investigate performance and error handling | Slow performance (13.3%) and error (10.4%) rank second and third |
| Review the transaction notification settings | The most-liked negative review (3,845 thumbs-up) concerns this feature |
| Communicate maintenance and disruptions more clearly | 8.1% of negative reviews mention maintenance, repairs, or disruptions |
 
## Limitations and Next Steps
 
- Sentiment is based on star ratings only. A review with a high rating can still contain complaints, and the reverse is also possible.
- Keyword matching is substring-based without word boundaries. Short keywords such as `lag`, `cs`, and `masuk` can match unrelated words, so topic counts may be overstated.
- Topic percentages do not sum to 100% because one review can match several categories.
- Keyword analysis covers negative reviews only.
- Results reflect June 14 – August 17, 2025 and do not represent other periods.
- Next step: add text-based sentiment classification (NLP) to validate the rating-based categories, and refine keyword matching with word boundaries.
 
## Contact
 
**Syasya Tri Puspita Dewi**
Portfolio: [syasyatpd.github.io](https://syasyatpd.github.io)
 
