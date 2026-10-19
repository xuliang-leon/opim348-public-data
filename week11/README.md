# Week 11 classroom data

Download the files directly for Colab:

| Dataset | Raw CSV URL |
| --- | --- |
| Public TLC completed trips | [tlc_uber_zone161_2023-01-06_to_08.csv](https://raw.githubusercontent.com/xuliang-leon/opim348-public-data/main/week11/tlc_uber_zone161_2023-01-06_to_08.csv) |
| Synthetic Uber RDD classroom data | [uber_surge_rdd_classroom_synthetic.csv](https://raw.githubusercontent.com/xuliang-leon/opim348-public-data/main/week11/uber_surge_rdd_classroom_synthetic.csv) |
| Synthetic hotel booking history | [hotel_booking_history_2023_2025.csv](https://raw.githubusercontent.com/xuliang-leon/opim348-public-data/main/week11/hotel_booking_history_2023_2025.csv) |

## Public TLC completed-trip sample

`tlc_uber_zone161_2023-01-06_to_08.csv` contains 12,357 **real completed trips** from the [NYC TLC 2023 High Volume FHV dataset](https://data.cityofnewyork.us/Transportation/2023-High-Volume-FHV-Trip-Data/u253-aew4/about_data). It selects Uber (`HV0003`), pickup zone 161, and pickup times from 2023-01-06 00:00 through 2023-01-08 23:59. The file retains five reported fields: company license, pickup time, pickup zone, trip miles, and base passenger fare. The [preparation script](https://github.com/xuliang-leon/opim348-course-site/blob/develop/scripts/prepare_week11_tlc_sample.py) is in the course materials repository.

For the teaching plot, retain trips with 1–20 miles, base fare $3–$150, and base fare per mile $1–$30. Aggregate by pickup hour. This leaves 10,555 trips and 72 zone-hour observations. The price proxy is **mean base passenger fare per mile**, not a posted offer price. Completed rides are not requests or conversion; the positive price–rides association is descriptive and cannot identify a causal demand curve. The [TLC data dictionary](https://www.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_hvfhs.pdf) defines the fields and license number.

## Synthetic classroom RDD data

`uber_surge_rdd_classroom_synthetic.csv` contains **400 invented aggregates**, each representing 1,000 app sessions near a hypothetical 1.25 underlying-surge threshold. A 1.2× multiplier appears below 1.25 and 1.3× above it. The purchase-rate data were generated with a smooth underlying-demand trend and a price response of approximately −0.5 elasticity. They are **not Uber session data** and cannot replicate the [Cohen et al. (2016) study](https://www.nber.org/papers/w22627). The [generator](https://github.com/xuliang-leon/opim348-course-site/blob/develop/scripts/prepare_week11_rdd_classroom.py) is in the course materials repository.

The slide chart marks the classroom model's purchase rates of **0.600 just below** and **0.575 just above** the cutoff. Its red lines show that reference model; the plotted dots are noisy synthetic observations.

## Synthetic hotel booking history for EMSR-b

`hotel_booking_history_2023_2025.csv` is a **fully simulated** history for a 172-room hotel. It contains one row for every booking date from 120 days before each stay through the stay date, for all 1,096 stay dates in 2023–2025 (132,616 rows). The [generator](https://github.com/xuliang-leon/opim348-course-site/blob/develop/scripts/generate_week11_hotel_data.py) and [beginner notebook](https://github.com/xuliang-leon/opim348-course-site/blob/develop/notebooks/week11/hotel-emsrb-booking-limits.ipynb) are in the course materials repository.

The four fare products, ordered from highest to lowest price, are **no restriction** (base S$250), **7-day advance purchase** (S$220), **30-day advance purchase** (S$180), and **90-day advance purchase** (S$140). Each advance-purchase fare accepts requests only when the stay is at least that many days away. Actual simulated rates vary modestly by year, peak season, and event night. Demand varies by day of week, June/December season, a simulated event indicator, fare, and random variation. Simulated bookings can be cancelled, and confirmed rooms never exceed 172.

| Column group | Meaning |
| --- | --- |
| `stay_date`, `booking_date`, `days_before_stay` | The room-night being sold, the booking snapshot date, and the booking lead time. |
| `rate_*` | Offered nightly rate in Singapore dollars for each fare product on this stay date. |
| `requests_*` | Daily customer requests for that product, including requests rejected after sellout. |
| `confirmed_*` | Daily newly accepted room bookings. |
| `cancellations_*` | Daily cancelled bookings. |
| `on_books_*` | Booked rooms for that fare after that day's new bookings and cancellations. |
| `total_on_books`, `rooms_available` | Total confirmed rooms and remaining capacity after that day's activity. |
| `peak_season`, `special_event` | Simulated demand and rate context, not actual Singapore event records. |

The suffixes are `flex`, `ap7`, `ap30`, and `ap90`. The notebook sums **requests** over booking dates to approximate uncensored fare-class demand; actual hotel systems may not observe requests when a product is closed or sold out. The generator records those requests specifically for the classroom exercise. Historical prices are manager-set, so the notebook does not interpret a price–demand correlation as a causal elasticity. EMSR-b is used as an initial booking-limit policy that an analyst would monitor and revise.
