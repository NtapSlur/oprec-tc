# Set python version using linux alpine
FROM python:3.8-alpine3.18

WORKDIR /opt/peramal

ENV PYTHONUNBUFFERED=1 \
    DJANGO_SETTINGS_MODULE=pyweb.settings \
    WEB_CONCURRENCY=2

# Make a new user compfest16 in a group cf16
RUN addgroup -S cf16 && adduser -S compfest16 -G cf16

# Copy everything from directory
COPY . .

# Give user compfest16 access to the working directory
RUN chown -R compfest16:cf16 .

# Change user to compfest16
USER compfest16

RUN pip install -r requirements.txt

EXPOSE 1234

CMD ["python", "manage.py", "runserver", "0.0.0.0:1234"]

