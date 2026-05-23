FROM python:3.12-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY . .

ENV PYTHONUNBUFFERED=1

EXPOSE 8000

CMD ["sh", "-c", "python manage.py collectstatic --noinput && python manage.py migrate && python manage.py loaddata data.json || true && DJANGO_SUPERUSER_PASSWORD=admin123 python manage.py createsuperuser --username superadmin --email superadmin@example.com --noinput || true && gunicorn drf_project.wsgi:application --bind 0.0.0.0:8000"]