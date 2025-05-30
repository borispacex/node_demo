```bash
docker build -t jenkins-ci:latest .
docker run -d -p 8080:8080 -p 5000:5000 --name jenkins-ci jenkins-ci:latest 
docker logs jenkins-ci
```
admin
admin
Boris Vargas
