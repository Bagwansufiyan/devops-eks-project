FROM python:3.12-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY app.py .

EXPOSE 5000
USER 1000
CMD ["opentelemetry-instrument", "--traces_exporter", "otlp", "--exporter_otlp_endpoint", "http://otel-collector-opentelemetry-collector.observability.svc.cluster.local:4317", "python", "app.py"]
