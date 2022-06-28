# Yealink Phone Book Manager
## Manage and Server Yealink's Remote Phone Books

Simple Rails app to manage and serve XML phone books for Yealink VoIP phones.

### Using Docker

You can run this app with a simple Docker container (with a SQLite3 DB and Puma as the webserver).

#### Building the Image Yourself

Build the image by using (tagging incrementally, along with `latest`)

```
docker build -t YOUR_PERSONALIZED_NAME/yealink:1.1 -t YOUR_PERSONALIZED_NAME/yealink:latest .
```



#### Running the Container

1. start container, will get error about database
2. After running container, copy `yealink-rpb/db/schema.rb` to local folder's db
  - (ex: `$PWD: ~/phonebook/db` would be `cp yealink-rpb/db/schema.rb ~/phonebook/db`)
3. run container again 


##### docker cli
```
docker run -v ./db/:/yealink/db/ --name yealink-rpb --network YOUR_REVERSE_PROXY_NETWORK -p 8081:80 jonswc/yealink:latest 
```

##### docker-compose.yml

```yaml
version: '3.3'
services:
  yealink:
    container_name: yealink-rpb
    ports:
      - '8081:80'
    volumes:
      - './db/:/yealink/db/'
    image: 'jonswc/yealink:latest'
    networks:
      - YOUR_REVERSE_PROXY_NETWORK

networks:
  YOUR_REVERSE_PROXY_NETWORK:
    external: true
    name: YOUR_REVERSE_PROXY_NETWORK
```

