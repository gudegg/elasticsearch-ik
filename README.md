# elasticsearch-ik for chinese
elasticsearch version:2.4.4

dockerhub :https://hub.docker.com/r/gude/elasticsearch-ik/

## Standalone:
`docker run -d --name elasticsearch -p 9200:9200 -p 9300:9300 gude/elasticsearch-ik`

## Cluster：
#### master
```
docker run \
  --name some-elasticsearch-master \
  -p 9200:9200 \
  -p 9300:9300 \
  -d \
  gude/elasticsearch-ik \
  --network.host=0.0.0.0
```
#### slave
```
docker run \
  --name some-elasticsearch-slave1 \
  --link some-elasticsearch-master \
  -p 9201:9200 \
  -p 9301:9300 \
  -d \
   gude/elasticsearch-ik \
  --network.host=0.0.0.0 \
  --discovery.zen.ping.unicast.hosts=some-elasticsearch-master
```
### cluster status
`curl http://localhost:9200/_cat/health?v`  or  `curl http://localhost:9200/_cluster/health`

[Tutorial](https://zhangguodong.me/2018/07/20/elasticsearch%E4%BD%BF%E7%94%A8docker%E9%9B%86%E7%BE%A4%E6%90%AD%E5%BB%BA/)
