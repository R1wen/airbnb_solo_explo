# Airbnb NYC 2019: Exploratory Data Analysis

An exploratory analysis of the New York City Airbnb listings dataset (2019), done with Python, pandas, matplotlib and seaborn.

The goal is to understand how the market is structured before any modeling: how prices are distributed, how long guests must stay, how often listings are available, and where the listings are concentrated in the city.

## Dataset

**`AB_NYC_2019.csv`**: 48,895 listings and 16 columns.

| Column | Description |
|---|---|
| `id`, `name` | Listing identifier and title |
| `host_id`, `host_name` | Host identifier and name |
| `neighbourhood_group` | Borough (Manhattan, Brooklyn, Queens, Bronx, Staten Island) |
| `neighbourhood` | Neighbourhood |
| `latitude`, `longitude` | Coordinates |
| `room_type` | Entire home/apt, private room or shared room |
| `price` | Price per night ($) |
| `minimum_nights` | Minimum stay required |
| `number_of_reviews`, `last_review`, `reviews_per_month` | Review activity |
| `calculated_host_listings_count` | Number of listings per host |
| `availability_365` | Days available over the year |

## Analysis steps

1. **Loading and overview**: structure of the data, types, missing values.
2. **Price analysis**: descriptive statistics, outlier detection with a boxplot, distribution after filtering.
3. **Nights and availability**: distribution of minimum stays and of yearly availability.
4. **Location**: distribution of listings across boroughs and the 10 neighbourhoods with the most listings.

## Key observations

### Data quality
- Missing values are limited to 4 columns: `name` (16), `host_name` (21), and `last_review` / `reviews_per_month` (10,052 each, about 21% of listings).
- The two review columns are missing for the same rows, which most likely correspond to listings that never received a review.
- 11 listings have a price of $0 and were removed as invalid entries.

### Prices
- The median price is **$106 per night**, while the mean is **$152.76**. The gap shows a strongly right-skewed distribution.
- The maximum price is **$10,000**, far from the 75th percentile ($175). These extreme listings distort the mean.
- Limiting the analysis to listings at or below $500 (about 2% of the data removed, 1,044 listings) brings the mean down to **$131.56** and the standard deviation from $240 to $88.
- Most listings are concentrated between about **$68 and $172 per night** (25th to 75th percentile).

### Minimum nights
- Most listings accept short stays: the median minimum stay is **2 nights** and 75% of listings require 5 nights or fewer.
- A small group (505 listings) requires more than 40 nights, which points to long-term rentals and pulls the raw distribution to the right. They were excluded for the distribution plot.

### Availability
- Availability is very polarized. About **36% of listings (17,533)** have 0 available days over the year, so they are either fully booked or inactive.
- Across all listings the median availability is only **45 days**.
- Among listings with at least one available day, the median rises to **168 days** and the mean to about 176 days. The spread is wide (25% below 55 days, 25% above 305 days).

### Location
- The market is highly concentrated: **Manhattan (21,661) and Brooklyn (20,104) hold about 85% of all listings**.
- Queens follows with 5,666 listings (about 12%), then the Bronx (1,091) and Staten Island (373), which together represent about 3%.
- The neighbourhoods with the most listings are **Williamsburg and Bedford-Stuyvesant**, both close to 4,000 listings, ahead of Harlem, Bushwick, Upper West Side, Hell's Kitchen, East Village, Upper East Side, Crown Heights and Midtown.
- Brooklyn neighbourhoods take the first two places, and 4 of the top 10 neighbourhoods are in Brooklyn.

## Tech stack

- Python 3
- pandas, NumPy
- matplotlib, seaborn
- Jupyter Notebook

## Getting started

```bash
git clone https://github.com/R1wen/airbnb_solo_explo.git
cd airbnb_solo_explo
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook airbnb_solo_explo.ipynb
```

The dataset `AB_NYC_2019.csv` is already included in the repository.

## Project structure

```
.
├── AB_NYC_2019.csv           # Dataset
└── airbnb_solo_explo.ipynb   # Main analysis notebook
```

## Author

Built by [R1wen](https://github.com/R1wen).
