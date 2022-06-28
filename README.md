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

```
docker run -v ./db/:/yealink/db/ --name yealink-rpb --network YOUR_REVERSE_PROXY_NETWORK -p 8081:80 jonswc/yealink:latest 
```

After running container, copy `yealink-rpb/db/schema.rb` to local folder's db (ex: `$PWD: ~/phonebook/db` would be `cp yealink-rpb/db/schema.rb ~/phonebook/db`)
