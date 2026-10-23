FROM python:3.11-slim

EXPOSE 80
COPY index.html /app/index.html

CMD ["python3", "-m", "http.server", "80", "--directory", "/app"]