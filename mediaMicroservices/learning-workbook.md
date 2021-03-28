# Enabling Log Aggregation and Queries


## What I've done

- [x] Set up a basic Elasticsearch + Fluentd + Kibana stack to aggregate logs abd integrated it with media microservices. Found documentation here :
    - https://docs.fluentd.org/v/0.12/container-deployment/docker-compose
    - https://github.com/fluent/fluentd-docs-gitbook/issues/75
  though a lot of it was incomplete and buggy. FLuentD log aggregation was badly documented here -- I've found that in docker-compose scenarios, its best just to
  use something like `fluentd-address: :24224` instead of specifying the host (it gets tricky, esp with docker-compose v2 vs v3).

- [x] These can now be queried using Kibana Query Language. This is not relational, and based on ElasticSearch unlike Microsoft's KUSTO.


## TODO: 
- [] Now, it might be useful to generate or identify some meaningful scenarios across this benchmark. I wonder if I can learn a lot about microservices by building a motivating scenario where logs need to be correlated
   across various 'tables' (or tags in this case). 
   -    It's a good chance to learn how Kibana/Elasticsearch deals with JOINs.
       - https://stackoverflow.com/questions/22611049/join-query-in-elasticsearch
       - https://www.elastic.co/guide/en/elasticsearch/reference/current/joining-queries.html


## Concretely Generating Workloads

Had to do some work in getting this up and running -- am still seeing errors in generated workloads, but this is probably a feature of this benchmark.

```
python3 scripts/write_movie_info.py -c ./datasets/tmdb/casts.json -m ./datasets/tmdb/movies.json && scripts/register_users.sh && scripts/register_movies.sh
```
