FROM ubuntu:latest 
#Tell to use the ubuntu's latest version as the Base Image

WORKDIR /app

# Copy current folder contents (including app.py) into /app
COPY . /app

#Intall the necessary packages  Python3 and pip in the container
RUN apt-get update && apt-get install -y python3 python3-pip


# Set environment variables
ENV NAME World

# Run a command to start the application (Runtime step )
CMD ["python3", "app.py"]
