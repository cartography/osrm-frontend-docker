# Dockerfile for osrm-frontend
This container run [osrm-frontend](https://github.com/Project-OSRM/osrm-frontend) for [osrm-backend](https://github.com/Project-OSRM/osrm-backend) project.

# Quick Start
When you start the osrm-frontend you must specify the API host and port. How to do it is written below.

## Start OSRM API

Start OSRM API and generate route files. 
> Warning OSRM files can be generated for a long time, about 30-60 minutes.
    
    docker run -d -p 5000:5000 -v /data/osrm-mos:/osrm-data --name osrm-api mudimages/docker-osrm:latest osrm Mos "http://be.gis-lab.info/data/osm_dump/dump/latest/RU-MOS.osm.pbf"


## Start OSRM Frontend

    docker run -d --link osrm-api:api --name osrm-mos-front --restart=always -p 8080:80 winsent/osrm-frontend-docker

You must `--link` osrm-frontend container with osrm-api with `api` tag. Or use `API_PORT_5000_TCP_ADDR` and `API_PORT_5000_TCP_PORT` variables to set host and port of the api.

You can test it by visiting [http://container-ip:8080](http://container-ip:8080)




