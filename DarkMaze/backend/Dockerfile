# Use an official Python runtime as a parent image
FROM python:3.11-slim

# Create a non-root user for security
RUN useradd --create-home appuser

# Set the working directory inside the container
WORKDIR /app

# Copy only necessary files to the container (avoid unnecessary files)
COPY requirements.txt /app/

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy only the relevant source code files
COPY src/ /app/

# Ensure the non-root user owns the directory
RUN chown -R appuser:appuser /app

# Switch to the non-root user
USER appuser

# Expose the FastAPI port
EXPOSE 8000

# Set the correct module path for Uvicorn
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
