## Docker Laravel8 Docker sample

- this repo contains a Dockerfile for deploying a Laravel8 application

- Create docker Image

```bash
docker build -t myimage .
```


- this will build the image from the Dockerfile

```bash
docker run -d -p 9000:80 myimage
```

- Run the above code to to run the image 
