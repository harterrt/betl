# BETL

BETL (say: beetle) makes it easy to define Basic ETL jobs for Firefox Telemetry data.

This project is **not yet ready** for public consumption.

For many jobs, we only want to do the following:
* **filter** to a subset of telemetry pings
* **flatten** the JSON ping to a flat table
* **format** or perform simple transformations over the field

BETL allows you to define these ETL jobs in a declarative format,
removing most of the complexity incurred while transforming pings.

BETL is written in python, so it's easy to get started.
We also provide a simple Jupyter notebook,
which allows you to schedule your job in [ATMO](https://analysis.telemetry.mozilla.org)
while keeping your code in a version controlled python library.

## Upcoming improvements:

* Testing Support to increase reliability
* [Airflow scheduling](https://http://workflow.telemetry.mozilla.org./) to provide better logging
