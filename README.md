# BETL

BETL (say: beetle) makes it easy to define Basic ETL jobs for Firefox Telemetry data.

For many jobs, we only want to do the following:
* **filter** to a subset of telemetry pings
* **flatten** the JSON ping to a flat table
* **format** or perform simple transformations over the field

BETL allows you to define these ETL jobs in a declarative format,
removing most of the complexity incurred while transforming pings.
