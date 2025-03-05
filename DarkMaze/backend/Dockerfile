# TODO: Install the backend dependency package into the app folder inside the container.
# Use an official Python runtime as a parent image
FROM python:3.11

# Set the working directory inside the container to /app
WORKDIR /app

# Copy the requirements.txt into the container at /app
COPY ./requirements.txt /app/requirements.txt

# Install any needed dependencies (including uvicorn)
RUN pip install --no-cache-dir -r requirements.txt

# Copy the entire backend application code into the container
COPY . /app

# Expose port 8000 for the backend app
EXPOSE 8000

ENV PATH="/usr/local/bin:$PATH"

# Set the default command to run the FastAPI app with uvicorn
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]