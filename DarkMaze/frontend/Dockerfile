# TODO: Install the frontend dependency package into the app folder inside the container.

# Use Python 3.11 as the base image
FROM python:3.11

# Set the working directory inside the container
WORKDIR /app

# Copy the frontend requirements file into the container
COPY ./requirements.txt /app/requirements.txt

# Install the frontend dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the frontend code into the container
COPY . /app

# Expose port 8088
EXPOSE 8088

# Run the FastAPI app using uvicorn
CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8088", "--reload"]
