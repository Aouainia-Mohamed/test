# service repository svc-dataclips-m

A service that takes care of data extract generation, and uploads them to AWS S3
It should allow creating new extracts from different data sources (Postgres, Elasticsearch)
And be able to create and upload very large extracts (streaming of csv)
