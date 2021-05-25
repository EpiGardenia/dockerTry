# Step 1
## Add dockerfile
Image support for each language is available in dockerhub
Check Tag for available images

## Add docker-compose.yaml
1. Choose a compose file version
2. Add service for each language, connect to github account

## Build 
### run docker-compose build <language>
This will download the coresponding image for the language
for example: docker-compose build python

### run docker-compose build
This will build everything defined in docker-compose.yaml



# Credit
[video](https://www.youtube.com/watch?v=wyjNpxLRmLg)