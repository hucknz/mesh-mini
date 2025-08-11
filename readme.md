# Mesh-Mini

Mesh-Mini is a fork of the npm package MeshCommander created by [BrytonSalisbury](https://github.com/BrytonSalisbury/mesh-mini), due to the ending of support of the MeshCommander application found here - https://www.meshcommander.com/meshcommander.

The code has been modified to be bundled and injected into a copy of node.exe and is accessed via your localhost in a browser. Docker images are also provided below. This solution is **much** more performant than the original MeshCommander due to running in a modern browser.

**Note:** This repo only builds a new version of the docker container when the base image is uploaded. Refer to https://github.com/BrytonSalisbury/mesh-mini for the original source and package downloads. 

## Docker

A Docker image can be pulled and then run with the following commands:

`docker pull hucknz/mesh-mini`

`docker run -p 3000:3000 hucknz/mesh-mini`

### Docker compose example
```
  meshcommander:
    container_name: meshcommander
    image: hucknz/mesh-mini
    ports:
      - 3000:3000
    restart: unless-stopped
```

### Notes

The Docker image is running the 'server' version of Mesh-Mini which can store a central computer list inside the container. The container can be passed an environment variable, _COMPUTER_PATH_, which controls where the computer list is stored, i.e `COMPUTER_PATH=/config/computers.json`

This can be used in conjunction with a mounted volume so a computer list can be provided and maintained from local storage.

If the environment variable isn't provided, when a computer list is pushed to the server it will be stored in _/usr/src/app/computers.json_

https://hub.docker.com/r/hucknz/mesh-mini
