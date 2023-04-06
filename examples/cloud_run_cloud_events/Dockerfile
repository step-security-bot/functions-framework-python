# Use the official Python image.
# https://hub.docker.com/_/python
FROM python:3.7-slim@sha256:fbb1606214af72cab47a4caf66ac0b94a343613b2a833c022a6de1acfbe84499

# Copy local code to the container image.
ENV APP_HOME /app
ENV PYTHONUNBUFFERED TRUE

WORKDIR $APP_HOME
COPY . .

# Install production dependencies.
RUN pip install gunicorn cloudevents functions-framework
RUN pip install -r requirements.txt
RUN chmod +x send_cloudevent.py

# Run the web service on container startup.
CMD ["functions-framework", "--target=hello", "--signature-type=cloudevent"]
