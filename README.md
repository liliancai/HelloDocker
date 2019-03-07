Docker get started project.

Followed https://docs.docker.com/get-started/part2/

sudo docker run -d -p 4000:80 liliancai/get-started:part2

After installed Nginx on server

```
/etc/nginx/nginx.conf 
Insert in http{}:
server{
       listen 80;
        location / {
                 proxy_pass http://0.0.0.0:4000;
        }
}
```

Also disable the default pagea:#not recommand way

```
#include /etc/nginx/sites-enabled/*;

sudo systemctl restart nginx
```
Then http://i.p.v.4 suposed to see what shows on http://0.0.0.0:4000

----------------------------------------------------------------------
### To stop container running as daemon
```
docker ps & docker stop <container ID>
```
### To build a image and remove it
```
docker build --tag=helloflask . & docker rmi --force helloflask:latest
```

### To push a builded image
i.g.
```
docker ps & docker commit f85f85be0898ecf & docker tag helloflask liliancai/helloflask:v2 & docker push liliancai/helloflask:v2 


& docker run -p 80:5000 liliancai/helloflask:v2
```
