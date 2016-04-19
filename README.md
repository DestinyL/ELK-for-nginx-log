# ELK-for-nginx-log
ELK (elasticsearch, logstash, kibana) Log analysis solution for nginx server log

# How to roll it up?

1. First install [Logstash](https://www.elastic.co/downloads/logstash), [Elasticsearch](https://www.elastic.co/downloads/elasticsearch), [Kibana](https://www.elastic.co/downloads/kibana).
2. Just run Kibana and Elasticsearch. They don't need any configuration so it's easy!
  - E.g. in mac, after installing them by `brew`, just type `$ elasticsearch` and `$ kibana` in shell to run them up
3. Setup Logstash:
  - Copy `logstash.conf` in this repo to your computer
  - Run logstash with that config file: `$ logstash -f logstash.conf`
  - If you want to run logstash by `service` cmd instead, just copy `logstash.conf` to its config folder (e.g. `/etc/logstash/config.d`)

# Note!

###### - When setting up logstash, check its privilege of nginx log file!

By default (on ubuntu 14), using service to run logstash will run as user `logstash`, but nginx log files are under user `www-data` and forbid other user's access. And logstash will tell you nothing wrong even it's forbidden by file privilege...

Solution can be:

- Use `chmod` to modify nginx log file privilege. E.g. `chmod 664 access.log`
- Modify `/etc/default/logstash` => `LS_USER` field to change logstash user, e.g. `root`

# [More detail on my blog here.](http://blog.yunfei.me/blog/ELK-stack.html)
