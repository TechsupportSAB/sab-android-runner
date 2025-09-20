# Android Application Builder Image

This image is used to build the **Anathabhojanam** application in **GitHub (GH) Actions**.

## Purpose of Containerization

1. **Check locally how the build can be run on a server.**
2. **Build locally if there is no proper Java installed on the local machine.**
3. **More controlled building/build environment.**

## Command to create image locally.

```shell
docker build -t android-build-tool-34-jvm-17-builder .
```

## Run gradle command using container

```shell
docker run --rm \
  --volume "$(pwd):/app" \
  --workdir /app \
android-build-tool-34-jvm-17-builder \
  sh -c "./gradlew detekt"
```