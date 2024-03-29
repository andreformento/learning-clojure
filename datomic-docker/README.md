# Datomic with docker

Get credentials [here](https://my.datomic.com/account)

- Build:
  ```shell
  export DATOMIC_USER=your@email.com
  export DATOMIC_PASSWORD=your.pass
  export DATOMIC_VERSION=1.0.6527

  docker build --build-arg DATOMIC_USER=$DATOMIC_USER \
              --build-arg DATOMIC_PASSWORD=$DATOMIC_PASSWORD \
              --build-arg DATOMIC_VERSION=$DATOMIC_VERSION \
              -t andreformento/datomic:$DATOMIC_VERSION .
  ```

- Push
  ```shell
  docker push andreformento/datomic:$DATOMIC_VERSION
  ```

- just run
  ```shell
  export DATOMIC_VERSION=1.0.6527
  export DATOMIC_LICENSE_KEY=your-license
  docker run --rm -it \
             -p 4334:4334 \
             -e DATOMIC_LICENSE_KEY=$DATOMIC_LICENSE_KEY \
             --name datomic \
             andreformento/datomic:$DATOMIC_VERSION
  ```

- console
  ```shell
  export DATOMIC_VERSION=1.0.6527
  docker run --rm -it \
             -p 8080:8080 \
             --name datomic-console \
             --entrypoint=/datomic-pro/bin/console \
             andreformento/datomic:$DATOMIC_VERSION \
             -p 8080 dev datomic:dev://datomic:4334/my-db
  ```
