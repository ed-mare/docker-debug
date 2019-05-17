# Build...
# docker build -t 'redis-client' ./
#
# Run...
# docker run --rm -it --privileged --network host redis-client
#
# https://redislabs.com/lp/redis-ruby/
# https://redis.io/topics/rediscli
# https://github.com/redis/redis-rb/blob/448322f0faff320eacec82682314edefb1b12036/lib/redis/distributed.rb
#
# Use the redis-cli
#
# redis-cli -h foo.bar.cache.amazonaws.com -p 6379
#
# Or use Ruby redis client. Use if connecting w/TLS.
#
# irb 
# require ‘redis’ 
#
# NOTE: monitor is not implemented yet (5/2019)
#
# redis = Redis.new(url: "rediss://:mypassword@myredis.instance.com:6379")
# 
# redis.ping # => “PONG”
# redis.set 'foo', 50
# redis.get 'foo'
# redis.exists 'foo'
# redis.expire 'foo', 50
# redis.del(‘foo’)
# redis.ttl 'foo'
# redis.keys 
# redis.keys 'fo*' # pattern match 
#
# Slow queries
# redis.slowlog('get', 25)
#
# INFO
# redis.info 
# redis.info["connected_clients"] 
# redis.info["connected_slaves"]
# redis.info["used_memory_human"] 
# redis.info(:commandstats)
#
# Flush all data
# redis.flushall

FROM ruby:2.6.2

ENV HOME /home/scripts
RUN mkdir -p $HOME
WORKDIR $HOME
COPY . $HOME
RUN apt-get update &&  apt-get -y install redis-tools && apt-get install -y stunnel4
RUN gem install redis
CMD ["/bin/bash"]
