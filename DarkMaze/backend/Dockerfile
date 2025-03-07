# Use an official Python runtime as a parent image
FROM python:3.11-slim

# Set the working directory inside the container to /app
WORKDIR /app

# Copy the requirements.txt into the container at /app
COPY ./requirements.txt /app/requirements.txt

# Install any needed dependencies (including uvicorn)
RUN pip install --no-cache-dir -r requirements.txt

# Create a non-root user and switch to it
RUN useradd -m -u 1000 myuser
USER myuser

# Copy the entire backend application code into the container
# COPY --chown=myuser:myuser ./src/ /app/
# Expose port 8000 for the backend app
RUN chown -R myuser:myuser /backend
EXPOSE 8000

# Set the default command to run the FastAPI app with uvicorn
CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8000"]