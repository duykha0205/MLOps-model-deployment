# Dockerfile

# Use a base image with necessary dependencies for your model
FROM python:3.9-slim

# Set working directory in the container
WORKDIR /app

# Copy the trained model script and dataset files
COPY my_trained_model.py datasets/my_dataset.csv ./

# Install any required dependencies (e.g., scikit-learn)
RUN pip install scikit-learn pandas joblib

# Command to run your model script
CMD ["python", "my_trained_model.py"]