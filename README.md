

Drone is a Continuous Delivery system built on container technology. Drone uses a simple YAML configuration file, a superset of docker-compose, to define and execute Pipelines inside Docker containers.

Sample Pipeline Configuration:

name: default

kind: pipeline
type: docker

steps:
- name: backend
  image: golang
  commands:
    - go get
    - go build
    - go test

- name: frontend
  image: node:6
  commands:
    - npm install
    - npm test

- name: publish
  image: plugins/docker
  settings:
    repo: octocat/hello-world
    tags: [ 1, 1.1, latest ]
    registry: index.docker.io

- name: notify
  image: plugins/slack
  settings:
    channel: developers
    username: drone

Documentation and Other Links:

    Setup Documentation docs.drone.io/installation
    Usage Documentation docs.drone.io/getting-started
    Plugin Index plugins.drone.io
    Getting Help discourse.drone.io
    Build the Enterprise Edition BUILDING
    Build the Community Edition BUILDING_OSS

Please note the official Docker images run the Drone Enterprise distribution. If you would like to run the Community Edition you can build from source by following the instructions in BUILDING_OSS.

