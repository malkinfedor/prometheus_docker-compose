# prometheus_docker-compose
Deploy prometheus with docker-compose for testing purpose

### Install Docker-compose on CentOS 7
```shell
yum install epel-release python-pip -y && \
pip install docker-compose && \
yum upgrade python* -y
```

### Change the next file before start (docker-compose up)

change ip address in the next file to the local ip address (just run `ip a`)
_prometheus.yml_

```yml
alerting:
  alertmanagers:
  - static_configs:
    - targets:
       - __10.0.0.4__:9093

  - job_name: 'node'
    static_configs:
    - targets: ['__10.0.0.4__:9100']

```

_alertmanager.yml_

```yml
receivers:
- name: email-me
  email_configs:
  - to: __your_email@gmail.com__
    from: kerios4fedor@gmail.com
    smarthost: smtp.gmail.com:587
```
