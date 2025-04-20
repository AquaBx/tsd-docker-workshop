# Use the official Python image as a base
FROM python:3.8-slim-buster

# Set the working directory in the container
WORKDIR /app

# Copy the files into the container
COPY . .

# Install required packages
RUN pip install --no-cache-dir -r requirements.txt

# Set an environment variable
ENV NAME World

# Open port 80
EXPOSE 80

# Run the application
CMD ["python", "app.py"]
