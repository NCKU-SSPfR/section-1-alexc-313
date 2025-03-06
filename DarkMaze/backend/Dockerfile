# Use an official Python runtime as a parent image
FROM python:3.11-slim

# Set a non-root user for security
RUN useradd --create-home appuser

# Set the working directory inside the container
WORKDIR /app

# Ensure the non-root user owns the directory
RUN chown -R appuser /app

# Copy only requirements first to leverage Docker caching
COPY requirements.txt /app/

# Install dependencies securely
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the frontend code after dependencies are installed
COPY src/ /app/

# Switch to non-root user
USER appuser

# Expose port 8000
EXPOSE 8000

# Run the FastAPI app using uvicorn
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]
