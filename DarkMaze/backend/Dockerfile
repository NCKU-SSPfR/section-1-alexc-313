# TODO: Install the backend dependency package into the app folder inside the container.

# Use an official Python runtime as a parent image
FROM python:3.11-slim

# Create a non-root user for security
RUN useradd --create-home appuser

# Set the working directory inside the container to /app
WORKDIR /app

# Ensure the non-root user owns the directory
RUN chown -R appuser /app

# Copy only the dependency file first to leverage Docker caching
COPY requirements.txt /app/

# Install any needed dependencies (including uvicorn)
RUN pip install --no-cache-dir -r requirements.txt

# Copy the entire backend application code into the container
COPY src/ /app/

# Switch to the non-root user
USER appuser

# Expose port 8000 for the backend app
EXPOSE 8000

# Set environment variables
ENV PATH="/usr/local/bin:$PATH"

# Set the default command to run the FastAPI app with uvicorn
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]
