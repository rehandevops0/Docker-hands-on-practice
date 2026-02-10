# Use official lightweight Python image
FROM python:3.9-slim

# Set working directory inside the container
# All commands will run from /app
WORKDIR /app

# Copy app.py from local machine to container's /app directory
COPY app.py .

# Install Flask inside the container
# This is required to run the Flask application
RUN pip install flask

# Command that runs when the container starts
# This starts the Flask backend server
CMD ["python", "app.py"]

