# About

This  `docker-compose` file allows you to spin up

-  RStudio server on port `8787` using `rstudio/rstudio`  
-  Jupyter data science notebook, with `Julia`, `R`, and `python 2/3` on port `8888`  
-  Neo4j database running on port `7474` with authentication disabled and APOC and postgresql/Redshift JDBC plugins

In addition to the tools above, the images map a few directories to the host computer in the form of `host path:container`.

To run this setup, simply

```
docker-compose up
```

where the `docker-compose.yaml` file is within the local directory.

This can certainly be extended in a number of ways, and at some point I will add other databases.

## Python  


First we need to install py2neo with `bolt` to leverage bolt connections

```
!pip install neo4j-driver==1.0.2
```

which should be run inside the cell in a notebook.

Now, connect

```
from neo4j.v1 import GraphDatabase, basic_auth
driver = GraphDatabase.driver("bolt://localhost")
session = driver.session()
```

for more info, go here:  http://neo4j.com/docs/developer-manual/current/#driver-manual-index  

## R



```
library(RNeo4j)
graph = startGraph("http://neo4j:7474/db/data/")
> graph
< Graph >
$version
[1] "3.0.3"
```
