FROM python:3.10.1

ENV PYTHONUNBUFFERED 1
ENV DJANGO_SETTINGS_MODULE=stocks_products.settings
ENV DATABASE_URL=sqlite:///db.sqlite3

WORKDIR /app/

COPY . .

RUN pip install --no-cache-dir -r requirements.txt

RUN python manage.py migrate
RUN python manage.py collectstatic --noinput

EXPOSE 8000

CMD ["gunicorn", "-b", "0.0.0.0:8000", "stocks_products.wsgi:application"]