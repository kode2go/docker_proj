# docker_proj

## Scala
Scala Project: https://github.com/kode2go/scala_local/wiki/Scala-on-GCP-VM-Instance#dockerize

## Flask API

For data file: https://github.com/kode2go/flask_fast_api/blob/main/data.csv

`pip install flask`

`pip freeze > requirements.txt`

Create Docker file from:

```
# Use an official Python runtime as a parent image
FROM python:3.8-slim

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in requirements.txt
RUN pip install --trusted-host pypi.python.org -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV CSV_FILE=data.csv

# Run app.py when the container launches
CMD ["python", "app.py"]

```

Then:

`sudo docker build -t flask-app .`

`sudo docker images`

Local machine:

`sudo docker run --network=host flask-app`

## Fast API

