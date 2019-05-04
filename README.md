# metrics

## docker 를 통한 influx / grafana 설정 
```shell
# influx & grafana 가 함께 속할 네트워크 설정
$ docker network create project-metrics

$ cd .docker
$ docker-compose up -d
```

### influx
```shell
$ docker exec -it {influx container id} /bin/bash
$ influx
$ create database test
$ use test
```

### grafana
```shell
$ docker exec -it {grafana container id} /bin/bash

# influx db 와 통신이 되는지 확인
$ curl -G 'http://influxdb:8086/ping'
```

grafana 웹UI에서 데이터소스 추가시 
- URL: http://influxdb:8086
- Database: test
