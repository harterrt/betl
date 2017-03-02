# BETL

BETL (say: beetle) makes it easy to define Basic ETL jobs for Firefox Telemetry data.

This project in in early alpha.

For many jobs, we only want to do the following:
* **filter** to a subset of telemetry pings
* **flatten** the JSON ping to a flat table
* **format** or perform simple transformations over the field

BETL allows you to define these ETL jobs in a declarative format,
removing most of the complexity incurred while transforming pings.

Starting with a collection of Pings, we can define a transformation:
```
transformed_dataframe = convert_pings(
        sqlContext,
        collection_of_pings,
        DataFrameConfig(
            [
                ("new_column_name", "ping_field", transformation, pyspark.sql.FieldType()),
                ("channel", "meta/normalizedChannel", None, StringType()),
                ("is_release", "meta/normalizedChannel", lambda x: x == "release", BooleanType()),
                ...
            ],
            lambda ping: ping['payload/test'] == '@testpilot-addon'
        )
)
```

Take a look at [this simple example](https://github.com/harterrt/betl-example/blob/master/main.py#L14),
or this [more complex ETL Job](https://github.com/harterrt/cliqz_ping_pipeline/blob/master/main.py#L54)

BETL is written in python, so it's easy to get started.
We also provide a [simple Jupyter notebook](notebooks/load_and_execute.ipynb),
which allows you to schedule your job in [ATMO](https://analysis.telemetry.mozilla.org)
while keeping your code in a version controlled python library.

## Upcoming improvements:

* Testing Support to increase reliability
* [Airflow scheduling](https://http://workflow.telemetry.mozilla.org./) to provide better logging
