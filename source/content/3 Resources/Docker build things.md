---
created: 20230913-1242
tags:
  - Resources/docker
---

What will you discover today?

How to build and test normal docker without a compose file. I'm getting too used to compose and should be more flexible with base docker.

### Build
`docker buildx build .` I started trying the simple simple docker build (with buildx for good measure, the one that compose uses)


`docker buildx build -t <image_name>:<image_tag> .` Now with a name so it's not a horrible hash

`docker buildx build  --target <stage_name> -t <image_name>:<image_tag> .` with target I can stop build in a certain stage of the dockerfile

### Run

`docker run -it <image_name>:<image_tag> <some_command>` I can not use the command and it will run the default CMD line written in the Dockerfile

~~~ bash
--rm removes the container once it stops
-p <local_port>:<container_port> exposes a port from the container
-v <local_folder/named_volume>:<container_folder> creates a bind mount or a volume
~~~


---
## Related Ideas:
* [[fleeting]]
* [[]]
