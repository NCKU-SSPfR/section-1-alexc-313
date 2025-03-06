# Use an official Python runtime as a parent image
FROM python:3.11-slim

# Set a non-root user for security
RUN useradd --create-home appuser

# Set the working directory inside the container
WORKDIR /app

# Copy only requirements first to leverage Docker caching
COPY requirements.txt /app/

# Install dependencies securely
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code after dependencies are installed
COPY src/ /app/

# Ensure the non-root user owns the directory
RUN chown -R appuser:appuser /app

# Switch to non-root user (after copying source to avoid permission errors)
USER appuser

# Expose port 8000
EXPOSE 8000

# Run the FastAPI app using uvicorn (adjust path if `main.py` is in `src/`)
CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]
