#  Amazon Product Pricing & Ratings Dashboard (Power BI)

An interactive Power BI dashboard that explores one question: **do bigger discounts mean better- or worse-rated products on Amazon?**

![Dashboard Overview](images/overview.png)

##  Problem Statement

Online shoppers see huge discounts everywhere, but is a discount a sign of a good deal or a weak product? This project analyses Amazon product listings (price, discount, rating, review count) to find which categories, price bands and discount levels offer the best value.

##  Key Metrics (KPI Cards)

| Metric | What it shows |
|---|---|
| **Total Products** | Number of products in the current filter |
| **Avg Discount %** | Mean discount across products |
| **Weighted Avg Rating** | Rating weighted by number of reviews, so a 4.5 from 20,000 reviews counts more than a 5.0 from 3 |
| **Total Reviews** | Sum of rating counts |
| **Avg Savings (INR)** | Average of actual price minus discounted price |
| **HRHD % of Catalog** | Share of products flagged High Rating + High Discount (genuine good deals) |

##  Key Insights

> Replace these with your real numbers from the dashboard.

- Average discount is **[XX%]** while the weighted average rating is **[X.X]**, so heavy discounting does not mean low quality.
- **[Category]** has the highest review volume; **[Category]** offers the deepest discounts.
- **[XX%]** of the catalog is flagged **HRHD** (High Rating, High Discount).
- **[Price band]** has the best balance of rating and discount.

##  Features

- Slicers for **Main Category, Price Band, Discount Band and Rating Band**
- Combo chart: Total Products vs Avg Discount % by price band
- Scatter plot: discount % vs rating, sized by rating count
- Bar charts: most-reviewed categories, sub-categories and products
- Drill-down matrix by category and sub-category
- Detail table with the **HRHD flag** per product
- Two report pages: **Overview** and a **detailed category / product page**

## 🛠️ Tools & Skills

- **Power BI Desktop**
- **Power Query**: data cleaning (price symbols, percentages, data types, nulls)
- **DAX**: custom measures (Weighted Avg Rating, Avg Savings, HRHD %)
- Data modelling, band segmentation, dashboard design

##  Repository Structure

```
├── DSE_assignment_vivid.pbix   # Power BI project file
├── README.md
├── images/
│   ├── overview.png            # Dashboard screenshots
│   └── page2.png
└── data/                       # (optional) source dataset / link
```

##  How to Open

1. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free, Windows only).
2. Download or clone this repo.
3. Open `DSE_assignment_vivid.pbix`.
4. If prompted, refresh the data or point the data source to the file in `data/`.

##  Dataset

Amazon products dataset with: `product_name`, `main_category`, `sub_category`, `actual_price`, `discounted_price`, `discount_percentage`, `rating`, `rating_count`.
Source: *[https://www.kaggle.com/datasets/shanjaikumar111/amazon-sales]*


##  Author

**[Your Name]**
[LinkedIn](https://linkedin.com/in/linkedin.com/in/shanjai-kumar-380933315) · [Email](mailto:shanjaikumarshanjaikumar@gmail.com)

⭐ If you found this useful, feel free to star the repo!
