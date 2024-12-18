# Volatility Docker image

[Volatility](https://github.com/volatilityfoundation/volatility) is a famous DFIR memory analysis framework.

This Docker image aims to make its installation and use very smooth, on any system.

## Usage

Create a shell script called vol26 with the below contents:

```
#!/bin/bash

docker run --rm --user=$(id -u):$(id -g) -v "$(pwd)/images":/dumps:ro,Z -ti phocean/volatility $@

```

Then, you can simply use it as follows:

```
➤  ./vol26 -f /dumps/memory_dump.vmem imageinfo
```



