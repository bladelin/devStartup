FROM ubuntu:16.04

RUN apt-get update && \
    apt-get install -y redis-server && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

#RUN sed -i 's/^\(bind .*\)$/# \1/' /etc/redis/redis.conf && \
#  sed -i 's/^\(daemonize .*\)$/# \1/' /etc/redis/redis.conf && \
#  sed -i 's/^\(logfile .*\)$/# \1/' /etc/redis/redis.conf

COPY redis.conf /etc/redis/redis.conf

# Define default command.
CMD ["redis-server", "/etc/redis/redis.conf"]


EXPOSE 6379
