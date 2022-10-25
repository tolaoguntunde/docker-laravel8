## Docker Lumen NginX sample


- Create docker Image

```bash
docker build -t myimage .
```


- this will build the image from the Dockerfile

```bash
docker run -d -p 9000:80 myimage
```

- Run the above code to to run the image 
