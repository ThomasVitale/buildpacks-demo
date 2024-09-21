# Buildpacks Demo

Demo for showing an issue with the Spring Boot plugin when running multi-arch buildpacks.
The examples are using Gradle, but it would be the same result with Maven.

## Multi-Arch Java Buildpacks

When using the pack CLI, the build works on both AMD64 and ARM64 architectures.

```shell
pack build demo \
  --builder docker.io/paketobuildpacks/builder-jammy-buildpackless-tiny \
  --buildpack gcr.io/paketo-buildpacks/java \
  --env BP_JVM_VERSION=22
```

When using the Spring Boot plugin, the build only works on ARM64 architectures.

```shell
./gradlew bootBuildImage
```

## Multi-Arch Java Native Buildpacks

When using the pack CLI, the build works on both AMD64 and ARM64 architectures.

```shell
pack build demo-native \
  --builder docker.io/paketobuildpacks/builder-jammy-buildpackless-tiny \
  --buildpack gcr.io/paketo-buildpacks/java-native-image \
  --env BP_JVM_VERSION=22 \
  --env BP_NATIVE_IMAGE=true
```

When using the Spring Boot plugin, the build works on both AMD64 and ARM64 architectures.

```shell
./gradlew bootBuildImage
```
