# til.cafe
Source for https://til.cafe

## handy commands

```
zola build
```

```
zola serve
or
zola serve -i 0.0.0.0 -u max.cat-bass.ts.net
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
- [x] create "about" page
- [x] figure out sections & taxonomies
- [x] update header to link to sections
- [ ] think about long term URL structure and post structure. Dates in urls? Date grouping in blog folder? 
- [ ] Need to figure out a plan for media assets (especially large audio files) Don't want them in the built image, but... is the Automatic SSL gonna get messed up if I want to serve some items from cloud storage as well? 
- [ ] find something to reformat html, & sass on save
- [x] add solarized
- [x] pick a body font
- [x] create just blog section
- [ ] consider - how much to keep in issues, Simon style
- [ ] consider - what license for content?
- [ ] precommit check to prevent `__tera_context` in templates
- [x] validate posts showing in atom feed
- [ ] add per page and overall site last updated date? 
- [ ] setup Berlely Mono for coding font
- [x] setup a DockerFile to make a Caddy container
- [x] configure SSL termination on Cloud Run
- [x] Cloud Build and deploy (multi-stage Docker)
- [x] setup GitHub build hook
- [ ] audio: prototype a WAV-metadata -> compressed audio + sqlite + web app flow. Audio files on GCS, generated sqlite & mini web app in the container. 

