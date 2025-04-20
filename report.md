image-name                   latest         0e90a673ed0e   8 minutes ago   2.18GB
dockersamples/101-tutorial   latest         4caa81cff7ef   5 years ago     46.2MB

the biggest one is the one we build earlier

# Initial Image

IMAGE          CREATED          CREATED BY                                      SIZE      COMMENT
0e90a673ed0e   16 minutes ago   CMD ["yarn" "dev"]                              0B        buildkit.dockerfile.v0
<missing>      16 minutes ago   EXPOSE map[8080/tcp:{}]                         0B        buildkit.dockerfile.v0
<missing>      16 minutes ago   RUN /bin/sh -c yarn build # buildkit            3.28MB    buildkit.dockerfile.v0
<missing>      16 minutes ago   COPY . . # buildkit                             1.25MB    buildkit.dockerfile.v0
<missing>      16 minutes ago   RUN /bin/sh -c yarn install # buildkit          418MB     buildkit.dockerfile.v0
<missing>      16 minutes ago   COPY yarn.lock ./ # buildkit                    81.9kB    buildkit.dockerfile.v0
<missing>      16 minutes ago   COPY package.json ./ # buildkit                 12.3kB    buildkit.dockerfile.v0
<missing>      16 minutes ago   WORKDIR /app                                    8.19kB    buildkit.dockerfile.v0
<missing>      4 weeks ago      CMD ["node"]                                    0B        buildkit.dockerfile.v0
<missing>      4 weeks ago      ENTRYPOINT ["docker-entrypoint.sh"]             0B        buildkit.dockerfile.v0
<missing>      4 weeks ago      COPY docker-entrypoint.sh /usr/local/bin/ # …   20.5kB    buildkit.dockerfile.v0
<missing>      4 weeks ago      RUN /bin/sh -c set -ex   && export GNUPGHOME…   5.41MB    buildkit.dockerfile.v0
<missing>      4 weeks ago      ENV YARN_VERSION=1.22.22                        0B        buildkit.dockerfile.v0
<missing>      4 weeks ago      RUN /bin/sh -c ARCH= && dpkgArch="$(dpkg --p…   168MB     buildkit.dockerfile.v0
<missing>      4 weeks ago      ENV NODE_VERSION=18.20.7                        0B        buildkit.dockerfile.v0
<missing>      4 weeks ago      RUN /bin/sh -c groupadd --gid 1000 node   &&…   69.6kB    buildkit.dockerfile.v0
<missing>      14 months ago    RUN /bin/sh -c set -ex;  apt-get update;  ap…   591MB     buildkit.dockerfile.v0
<missing>      14 months ago    RUN /bin/sh -c set -eux;  apt-get update;  a…   200MB     buildkit.dockerfile.v0
<missing>      22 months ago    RUN /bin/sh -c set -eux;  apt-get update;  a…   52.3MB    buildkit.dockerfile.v0
<missing>      22 months ago    # debian.sh --arch 'arm64' out/ 'bookworm' '…   155MB     debuerreotype 0.15

# Workshop

IMAGE          CREATED          CREATED BY                                      SIZE      COMMENT
c4c76c196770   2 minutes ago    CMD ["yarn" "dev"]                              0B        buildkit.dockerfile.v0
<missing>      2 minutes ago    EXPOSE map[8080/tcp:{}]                         0B        buildkit.dockerfile.v0
<missing>      2 minutes ago    COPY . . # buildkit                             1.25MB    buildkit.dockerfile.v0
<missing>      16 minutes ago   RUN /bin/sh -c yarn install # buildkit          418MB     buildkit.dockerfile.v0
<missing>      17 minutes ago   COPY yarn.lock ./ # buildkit                    81.9kB    buildkit.dockerfile.v0
<missing>      17 minutes ago   COPY package.json ./ # buildkit                 12.3kB    buildkit.dockerfile.v0
<missing>      17 minutes ago   WORKDIR /app                                    8.19kB    buildkit.dockerfile.v0
<missing>      4 weeks ago      CMD ["node"]                                    0B        buildkit.dockerfile.v0
<missing>      4 weeks ago      ENTRYPOINT ["docker-entrypoint.sh"]             0B        buildkit.dockerfile.v0
<missing>      4 weeks ago      COPY docker-entrypoint.sh /usr/local/bin/ # …   20.5kB    buildkit.dockerfile.v0
<missing>      4 weeks ago      RUN /bin/sh -c set -ex   && export GNUPGHOME…   5.41MB    buildkit.dockerfile.v0
<missing>      4 weeks ago      ENV YARN_VERSION=1.22.22                        0B        buildkit.dockerfile.v0
<missing>      4 weeks ago      RUN /bin/sh -c ARCH= && dpkgArch="$(dpkg --p…   168MB     buildkit.dockerfile.v0
<missing>      4 weeks ago      ENV NODE_VERSION=18.20.7                        0B        buildkit.dockerfile.v0
<missing>      4 weeks ago      RUN /bin/sh -c groupadd --gid 1000 node   &&…   69.6kB    buildkit.dockerfile.v0
<missing>      14 months ago    RUN /bin/sh -c set -ex;  apt-get update;  ap…   591MB     buildkit.dockerfile.v0
<missing>      14 months ago    RUN /bin/sh -c set -eux;  apt-get update;  a…   200MB     buildkit.dockerfile.v0
<missing>      22 months ago    RUN /bin/sh -c set -eux;  apt-get update;  a…   52.3MB    buildkit.dockerfile.v0
<missing>      22 months ago    # debian.sh --arch 'arm64' out/ 'bookworm' '…   155MB     debuerreotype 0.15

## Image diff in size

docker-workshop              small          c4c76c196770   3 minutes ago    2.17GB
image-name2                  latest         49561b06f2bd   8 minutes ago    2.18GB

## list of containers

tomchauvel@MacBook-Air-de-Tom tsd-docker-workshop % docker ps -a
CONTAINER ID   IMAGE                          COMMAND                  CREATED          STATUS                   PORTS                    NAMES
8b777d9fc781   docker-workshop:small          "docker-entrypoint.s…"   7 minutes ago    Up 7 minutes             0.0.0.0:8080->8080/tcp   friendly_swartz
7f2832acc57b   docker-workshop:small          "docker-entrypoint.s…"   8 minutes ago    Created                                           sharp_nightingale
6cc53875e06d   image-name2                    "docker-entrypoint.s…"   12 minutes ago   Created                                           charming_allen
748efeb7a842   dockersamples/101-tutorial     "nginx -g 'daemon of…"   16 minutes ago   Up 16 minutes            0.0.0.0:81->80/tcp       objective_banzai
9c05538cb156   dockersamples/101-tutorial     "nginx -g 'daemon of…"   16 minutes ago   Created                                           blissful_hofstadter
9b7d56d5aea0   bkimminich/juice-shop          "/nodejs/bin/node /j…"   2 hours ago      Up 2 hours               0.0.0.0:80->3000/tcp     crazy_bartik
e6b19a2498bf   bkimminich/juice-shop:latest   "/nodejs/bin/node /j…"   2 weeks ago      Exited (0) 2 hours ago 

## echo hello

tomchauvel@MacBook-Air-de-Tom tsd-docker-workshop % docker exec 8b777d9fc781 echo "hello"
hello
tomchauvel@MacBook-Air-de-Tom tsd-docker-workshop % docker exec e6b19a2498bf echo "hello"
Error response from daemon: container e6b19a2498bfbfc568729350a1b975ba7dc740d3143fd2fe45cf043434b3ac84 is not running
tomchauvel@MacBook-Air-de-Tom tsd-docker-workshop % 


## touch file

tomchauvel@MacBook-Air-de-Tom tsd-docker-workshop % docker run -it docker-workshop:small /bin/sh
# ls
Dockerfile  LICENSE  README.md  cheetsheet.md  first-steps.md  intro.md  next-steps.md  node_modules  package.json  presentation.md  report.md  yarn.lock
# touch coucou.txt
# 
tomchauvel@MacBook-Air-de-Tom tsd-docker-workshop % docker run -it docker-workshop:small /bin/sh
# ls
Dockerfile  LICENSE  README.md  cheetsheet.md  first-steps.md  intro.md  next-steps.md  node_modules  package.json  presentation.md  report.md  yarn.lock
# 

##

docker run -it  buildtree /bin/sh




### Part 2

volume mounting update instantly the code

docker run --rm \
-p 8080:8080 -dt \
--volume $(pwd):/app \
-w /app \
--name workshop \
node:18 \
sh -c "yarn install && yarn dev"

