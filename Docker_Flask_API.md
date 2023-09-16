# Flask API

Assuming: nginx and flask installed

Install docker:

`sudo apt-get install docker.io`

Create a directory `mkdir flask`

In there copy the `data.csv` file to the `flask/`

Create the Dockerfile:

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

Follow the app and nginx installation: https://github.com/kode2go/flask_fast_api/blob/main/README.md

Build the app: `sudo docker build -t flask-app .`

Then run docker locally: `sudo docker run --network=host flask-app`




