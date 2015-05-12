# Docker Exec Image: Java

A Dockerfile describing an container capable of executing Java source files.

# Build

```sh
git clone https://github.com/docker-exec/java.git
docker build -t dexec/lang-java .
```

# Usage

In a directory containing a script e.g. foo.java, run:

```sh
docker run -t --rm \
    -v $(pwd -P)/foo.java:/tmp/dexec/build/foo.java \
    dexec/lang-java foo.java
```

## Passing arguments to the script

Arguments can be passed to the script using any of the following forms:

```
-a argument
--arg argument
--arg=argument
```

Each argument passed must be prefixed in this way, e.g.

```sh
docker run -t --rm \
    -v $(pwd -P)/foo.java:/tmp/dexec/build/foo.java \
    dexec/lang-java foo.java \
    --arg='hello world' \
    --arg=foo \
    --arg=bar
```

## Passing arguments to the compiler

Arguments can be passed to the compiler using any of the following forms:

```
-b argument
--build-arg argument
--build-arg=argument
```

Each argument passed must be prefixed in this way, e.g.

```sh
docker run -t --rm \
    -v $(pwd -P)/foo.java:/tmp/dexec/build/foo.java \
    dexec/lang-java foo.java \
    --build-arg=-some-compiler-option \
    --build-arg=some-compiler-option-value
```
