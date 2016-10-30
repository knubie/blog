# Using NGINX to run multiple web servers with Docker.

- `#nginx`
- `#docker`
- `#docker-gen`
- `#linux-containers`
- `#reverse-proxy`

---

It's pretty straight forward to run a web server in Docker. Just expose port 80, or whichever you prefer, and load up the host machine's IP address in a web browser.

```
$ docker run -d --name node-app -p 80:80 -v "$PWD":/usr/src/myapp node:0.10 node /usr/src/myapp/app.js
```

But if you're running multiple web apps with Docker you'll need a way to map the incoming requests to your server to the appropriate docker container. That's where Nginx's reverse proxy comes in.
First you'll need to find the IP adress of the container running the web server.

```
$ docker inspect node-app | grep IPAddress
```

Now we can just plug the IP address into our Nginx configuration, and either map it to a new hostname.

```
upstream node_app {
  server 172.17.0.1:80;
}

server {

  server_name my-node-app.com;

  location / {
    proxy_pass http://node_app;
  }
}
```
Or, alternatively we could drop the `server_name` directive, and route it to some alternate path on the parent context's hostname.

````
upstream node_app {
  server 172.17.0.1:80;
}

server {
  location /node-app/ {
    proxy_pass http://node_app;
  }
}
```

This technique works, however it can be cumbersome to manually update the Nginx configuration every time you stop/start a container with its new IP address. Thanks to [jwilder](https://github.com/jwilder), however, there's an incredibly useful tool called [docker-gen](https://github.com/jwilder/docker-gen) which can be used to automatically generate configuration files (in addition to any other kind of text file) every time a docker container is run. He's even got an [Nginx reverse-proxy demo](https://github.com/jwilder/nginx-proxy) demonstrating this exact use-case.

