[logo]: https://miro.medium.com/max/256/0*AqO_2lNemh_Fl9Gm.png"

Drone is a Continuous Delivery system built on container technology. Drone uses a simple YAML configuration file, a superset of docker-compose, to define and execute Pipelines inside Docker containers.

<img src=https://github.com/drone/brand/blob/master/screenshots/screenshot_build_success.png/>

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
    
   * [Setup Documentation](https://docs.drone.io/installation)
   * [Usage Documentation](https://docs.drone.io/getting-started)
   * [Plugin Index](https://plugins.drone.io)
   * [Getting Help](https://discourse.drone.io)
   * [Build the Enterprise Edition](https://github.com/drone/drone/blob/master/BUILDING)
   * [Build the Community Edition](https://github.com/drone/drone/blob/master/BUILDING_OSS)
