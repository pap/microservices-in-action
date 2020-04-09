A microservice chassis for Python services
==========================================

This project aims to abstract common concerns such as logging, error reporting,
metrics collection, circuit breaking, service registration etc.

## Run `demo.py` using docker

### Build the docker image

Open a terminal window and run the following command:

`docker build -t chapter7:chassis .`

You will see an output similar to this:

```bash
Sending build context to Docker daemon  17.41kB
Step 1/6 : FROM python:3.8-buster
 ---> d47898c6f4b0
Step 2/6 : COPY . /app
 ---> 2df60832e917
Step 3/6 : WORKDIR /app
 ---> Running in 7793e77d9ac5
Step 4/6 : RUN pip install -r requirements.txt
 ---> Running in f6c783b44d27

(...)

Step 5/6 : EXPOSE 8000
 ---> Running in 4afb69ad72c6
Removing intermediate container 4afb69ad72c6
 ---> 5e51fc57e4fb
Step 6/6 : CMD [ "nameko", "run", "--config", "config.yml", "demo" ]
 ---> Running in 07af20935b2f
Removing intermediate container 07af20935b2f
 ---> 252f01156b43
Successfully built 252f01156b43
Successfully tagged chapter7:chassis
```

A docker image `chapter7:chassis` should now be available to you.

### Run the example application

To run using the docker image you have created execute the following command on a terminal window:

 `docker run --rm -p 8000:8000 chapter7:chassis`

This sample application, running on top of `nameko` will expose the `demo_chassis_service` and `health_check_service` services.

#### demo_chassis_service

Provides 3 endpoints:

* health (GET)
* external (GET)
* error (GET)

#### health_check_service

Will start a timer, with a 10 second interval, invoking the health endpoint provided by `demo_chassis_service`
