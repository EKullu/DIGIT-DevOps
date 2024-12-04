FROM ubuntu:latest

# Install curl and cron
RUN apt-get update && apt-get install -y curl cron

# Add the cron job to the container
RUN echo "*/10 * * * * curl -X GET https://stagingpiramal.tekdinext.com/application/v1/UpdateDisbursals -H 'Content-Type: application/json'" > /etc/cron.d/ping-api

# Apply cron job and start cron
RUN chmod 0644 /etc/cron.d/ping-api
RUN crontab /etc/cron.d/ping-api

# Start cron in the background
CMD ["cron", "-f"]
