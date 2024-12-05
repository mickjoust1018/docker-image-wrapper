# docker-image-wrapper
1. 这个库用于拉取 k8s 在国内无法拉取的部分镜像库。
2. 用于备份正在使用的docker镜像。


## 2024-12-05：新增
- sonarqube:9.9.8-community
- grafana/loki:3.1.2 = latest
- grafana/grafana:11.3.2 = latest
## 2024-12-04：新增
- grafana:8.5.3
- sonarqube:9.3.0-community
- sonarqube:9.9.0-community
- jenkins:2.431-jdk11
- influxdb:1.8
- elasticsearch:7.12.0
- mongo:4.2
- graylog:4.3.6
- postgres:17.2 = latest

## 可用组件
- coredns
- kube-prometheus
  - kube-state-metrics
  - prometheus-adapter
  - prometheus
- nfs-subdir-external-provisioner

