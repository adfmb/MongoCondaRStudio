MongoCondaRStudio
================
Cluster with Mongo, Conda &amp; RStudio images from Dockerfiles and including the clone of the repository [Quality of Life Analysis by dragon-analytics](https://github.com/dragon-analytics/quality-of-life-analysis)

Get the files
===========
- Clone this [**repo**](https://github.com/adfmb/MongoCondaRStudio.git)

# Steps
- Go to the folder MongoCondaRStudio/
- docker-compose build
- docker-compose up

### For Jupyter
- Go to [**Jupyter**](http://localhost:8888/) and write the given *token*

### For RStudio
- Visit **http://localhost:8098/admin.php** and create new user / pasword (*admin / supersecret*).
- Go to [**RStudio**](http://localhost:8099) and log in with credentials from the previuos step


## References
- [MongoConda *by juandados*](https://github.com/juandados/MongoConda/tree/0299548ce045d6b52f50d4e07997ee585040add6)
- [rstudio-docker *by fikipollo*](https://github.com/fikipollo/rstudio-docker)
