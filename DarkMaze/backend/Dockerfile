FROM python:3.11-slim
WORKDIR /app

COPY ./requirements.txt /app/requirements.txt
RUN pip install --no-cache-dir -r /app/requirements.txt

RUN useradd -m -u 1000 nonrootuser
RUN chown -R nonrootuser:nonrootuser /app

COPY --chown=nonrootuser:nonrootuser ./src /app
USER nonrootuser

CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]