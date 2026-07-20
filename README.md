# Docker repo
https://hub.docker.com/repository/docker/dbal7/is601_assignment11/general


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

## Also set up personal access tokens with docker and github

**Update tags in yml file to match docker repo**

# Issues

### Github action test failed, assertion error

keep repushing

### Github action security errors

**Update h11, urlib3, and fastapi versions**

FROM
```bash
h11==0.14.0
urllib3==2.2.3
fastapi==0.115.4
httpcore==1.0.6
```

TO
```bash
h11==0.16.0
urllib3==2.7.0
fastapi==0.139.0
httpcore==1.0.9
```

**Install updated dependecy version**
```bash
pip install --upgrade -r requirements.txt
```

## Postgres error during github action test

**Close down image**
```bash
docker compose down
```

**Update**
```bash
image: postgres:17
```

### Still getting an error during test: Error 500

**Test by running main.py and see server error log**
```bash
python main.py 2>&1 | tee server_error.log
```

**Use tail to see exactly what is causing this error**
```bash
tail -n 40 server_error.log
```

**Change line 61 in main.py from**
```bash
return templates.TemplateResponse("index.html", {"request": request})
```

**To**
```bash
return templates.TemplateResponse(
    request=request,
    name="index.html"
)
```