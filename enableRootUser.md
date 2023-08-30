# How to enable root user and super user in container for devspaces

Create the `Dockerfile` with the content

```
FROM devspaces/udi-rhel8:latest
RUN dnf -y -q install sudo
RUN RUN echo "user:password" | chpasswd
RUN echo 'user ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
WORKDIR /projects
CMD tail -f /dev/null
```

then create the `authfile.json` with your credentialsrun the commands

```
docker build --authfile authfile.json -t mariodga:latest
```
...build output


```
docker push --authfile authfile.json mariodga:latest docker.io/danisilver/mariodga:latest
```

...push output

Once the container has been pushed, we can use it in a new devfile in a github repo.

The base container is `docker.io/danisilver/mariodga:latest`

```
schemaVersion: 2.2.0
metadata:
  name: nodejs-mongodb
  namespace: danielgallardo21-dev
attributes:
  controller.devfile.io/devworkspace-config:
    name: devworkspace-config
    namespace: crw
  controller.devfile.io/scc: container-build
  controller.devfile.io/storage-type: common
projects:
  - name: front-end
    git:
      remotes:
        origin: "https://github.com/shaunwa/fsa-meal-tracker-app.git"
      checkoutFrom:
        revision: main
  - name: back-end
    git:
      remotes:
        origin: "https://github.com/shaunwa/fsa-meal-tracker-server.git"
      checkoutFrom:
        revision: main
components:
  - name: nodejs
    container:
      image: docker.io/danisilver/mariodga:latest
      env:
      # The values below are used to set up the environment for running the application
        - name: SECRET
          value: 220fd770-c028-480d-8f95-f84353c7d55a 
        - name: NODE_ENV
          value: production
      endpoints:
        - exposure: public
          name: nodejs
          targetPort: 8080
      memoryLimit: 1G
      mountSources: true
      volumeMounts:
        - name: npm
          path: /home/user/.npm
  - name: npm
    volume:
      size: 1G
  - name: mongo
    container:
      image: registry.redhat.io/rhscl/mongodb-36-rhel7:1-50
      env:
        - name: MONGODB_USER
          value: user
        - name: MONGODB_PASSWORD
          value: password
        - name: MONGODB_DATABASE
          value: guestbook
        - name: MONGODB_ADMIN_PASSWORD
          value: password
      endpoints:
        - name: mongodb
          exposure: internal
          targetPort: 27017
      memoryLimit: 512Mi
      mountSources: false
      volumeMounts:
        - name: mongo-storage
          path: /var/lib/mongodb/data
  - name: mongo-storage
    volume:
      size: 1G
commands:
  - id: 1-run
    exec:
      label: "Run the application"
      component: nodejs
      workingDir: ${PROJECTS_ROOT}/nodejs-mongodb-sample
      commandLine: "npm install && node --inspect=9229 app.js"
      group:
        kind: run
```