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
- [ ] think about long term URL structure and post structure. Dates in urls? Date grouping in blog folder? 
- [ ] Need to figure out a plan for media assets (especially large audio files) Don't want them in the built image, but... is the Automatic SSL gonna get messed up if I want to serve some items from cloud storage as well? 
- [ ] find something to reformat html, & sass on save
- [x] add solarized
- [x] pick a body font
- [x] create just blog section
- [ ] create main sections and a hello post for each
- [ ] precommit check to prevent `__tera_context` in templates
- [x] validate posts showing in atom feed
- [ ] make a template for each section type
- [ ] setup Berlely Mono for coding font
- [ ] figure out sections & taxonomies
- [x] setup a DockerFile to make a Caddy container
- [F] push local docker image to Cloud Run
- [x] configure SSL termination on Cloud Run
- [x] Cloud Build and deploy (multi-stage Docker)
- [x] setup GitHub build hook

