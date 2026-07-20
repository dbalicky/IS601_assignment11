# Setup

## Use python 3.10
```bash
pyenv local 3.10
```

## Initialize and set repo
```bash
git init

git remote add origin main
```

## Create and activate venv
```bash
python3 -m venv venv

source ativate/bin/venv
```

## Install dependencies from requirements.txt
```bash
pip install -r requirements.txt
```

## Commit and push to repo
```bash
git add <updated file or dir>

git commit -m '<message about commit>'

git push origin main

# or to use git push on future pushes
git push --set-upstream origin main 
```

# Docker setup

**Setup docker repo**

## Check if docker is working
```bash
docker compose ps
```

## Check if any projects are active
```bash
docker compose ls
```

**If active, erase any previous image data**
```bash
docker compose down -v
```

## Build new image
```bash
docker compose up --build

# or to run in background
docker compose up --build -d
```

## Tag image to docker repo

**Use *docker compose ps* to check local Image name**

```bash
docker tag <local image name> <docker repo image>

# local image name : assignment11-web:latest
# docker repo image name: dbal7/is601_assignment11:latest
```

## Push image to docker
```bash
docker push <docker repo image>
```

## Shutdown and remove running image after completion
```bash
docker compose -v
```

# Issues

### Github action test failed, assertion error

keep repushing
