# til.cafe
Source for https://til.cafe

## handy commands

```
zola build
```

```
zola serve
```

docker stuff
```
docker build -t til.cafe:tag .
docker run -p 8080:8080 til.cafe:tag
```

```
gcloud run deploy til-cafe --allow-unauthenticated --max-instances=3 --region=us-west1 --project=til-cafe --source .
```


# TODOs
- [x] add solarized
- [x] pick a body font
- [x] create just blog section
- [ ] create main sections and a hello post for each
- [x] validate posts showing in atom feed
- [ ] make a template for each section type
- [ ] setup Berlely Mono for coding font
- [ ] figure out sections & taxonomies
- [ ] setup a DockerFile to make a Caddy container
- [ ] push local docker image to Cloud Run
- [ ] configure SSL termination on Cloud Run
- [ ] setup Cloud Build and deploy (multi-stage Docker)
- [ ] setup GitHub build hook

