# Elasticsearch-Logstash-Kibana (ELK)

Download the necessary binaries:
* https://www.elastic.co/downloads/elasticsearch
* https://www.elastic.co/downloads/logstash
* https://www.elastic.co/downloads/kibana

### Start the elasticsearch server
* Open a terminal (command prompt in Windows)
* Change directory (cd) into the elasticsearch folder
* Issue the following command:

```
bin/elasticsearch
```

Once the server is up, visit http://localhost:9200 to verify.

### Start the kibana server
* Open a terminal (command prompt in Windows)
* Change directory (cd) into the kibana folder
* Issue the following command:

```
bin/kibana
```

Once the server is up, visit http://localhost:5601 to verify.


### Start the logstash server
* Open a terminal (command prompt in Windows)
* Change directory (cd) into the logstash folder
* Issue the following command:

```
bin/logstash -f logstash-sample.conf
```

Where the `logstash-sample.conf` (or any other filename) has the following content:

```
input {
  file {
    path => "/Users/vinodkumar/Desktop/spring-boot-sandbox/product-service/logs/slf4j.log"
    type => "syslog"
  }

  file {
    path => "/Users/vinodkumar/Desktop/spring-boot-sandbox/category-service/logs/slf4j.log"
    type => "syslog"
  }
}

output {
    elasticsearch {
        hosts => ["localhost:9200"]
        index => "myapp-%{+YYYY.MM.dd}"
    }
}
```
