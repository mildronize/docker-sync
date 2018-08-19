# docker-sync
Maximized the applications run time speed without bottleneck leveraging unison (for windows)

## prerequisites:
- [unison](https://www.cis.upenn.edu/~bcpierce/unison/)
- docker-compose
- [docker-toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/)

## How to setup
1. setup docker-compose.yml 
    - replace `debian` with your image
2. add this line to your service (container)
    ```
    volumes_from:
      - unison
    ```
3. setup your target path on your container (where is the file will go) default: I use `/src`
    ```
    environment:
      - UNISON_WORKING_DIR=/src
    volumes:
      - /src
    ```
2. setup script in `package.json`

## How to use
This is for powershell user.

```
npm install
docker-machine env | Invoke-Expression
npm run docker-init   # for first time run or init your script
npm run docker-dev    # for syncing files to docker
```

## TODO
- [ ] make it easier to use

## Thanks
- [docker-unison](https://github.com/leighmcculloch/docker-unison)

Inspire from [docker-sync](https://github.com/EugenMayer/docker-sync)

I made it because [docker-sync](https://github.com/EugenMayer/docker-sync) is hard to use for me.