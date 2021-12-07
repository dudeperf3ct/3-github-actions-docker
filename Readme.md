#### Github Actions with Docker

[![GH Docker Compose with locust load testing](https://github.com/dudeperf3ct/3-github-actions-docker/actions/workflows/main.yml/badge.svg?branch=main&event=push)](https://github.com/dudeperf3ct/3-github-actions-docker/actions/workflows/main.yml)

In the exercise, we will implement the following.

1. Containerize a GitHub project by integrating a Dockerfile and automatically registering new containers to a Container Registry.

2. Create a simple load test for your application using a load test framework such as locust or loader io and automatically run this test when you push changes to a staging branch.

One of the reason job can fail is mismatch between ip provided by flask and the one passed to locust.

Check if 

in github actions build log

```bash
web_1     |  * Running on http://172.18.0.2:8000/ (Press CTRL+C to quit)
```
and in `docker-compose.yml`

```bash
command: -f /app/locustfile.py --host=http://172.18.0.2:8000/ --headless -u 1000 -r 100 -t 10s
```
are same.
