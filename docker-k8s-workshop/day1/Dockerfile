# Use Python base image
FROM python:3.9-slim

# Set working directory
WORKDIR /app

# Copy source code
COPY app.py /app

# Install Flask
RUN pip install flask

# Expose port
EXPOSE 8080

# Command to run the app
CMD ["python", "app.py"]
