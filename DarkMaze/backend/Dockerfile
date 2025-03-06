# TODO: Install the backend dependency package into the app folder inside the container.

FROM python:3.11-slim

RUN useradd --create-home appuser

WORKDIR /app

COPY requirements.txt /app/

RUN pip install --no-cache-dir -r requirements.txt

COPY src/ /app/

RUN chown -R appuser /app

USER appuser

EXPOSE 8000

CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]
