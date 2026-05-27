# Phronencial Frontend
``` yaml
deploy_staging:
  tags:
    - production
  environment:
    name: production
    url: https://newfront.phronencial.com
  script:
    - cd $PROJECT_FOLDER && git pull origin main && npm install && npm run build && exit
  only:
    - main
```

#  Novathena app
``` yaml
workflow:
stages:          # List of stages for jobs, and their order of execution
  - build
  - deploy

build-staging:       # This job runs in the build stage, which runs first.
  stage: build
  rules:
    - if: $CI_COMMIT_BRANCH == "Staging"
  tags:
    - staging
  script:
    - echo "Building the Webapp"
    - cp dockerfiles/Dockerfile.prod Dockerfile
    - docker build --target build -t $DOCKER_IMAGE_NAME .
    - echo "Building completed."

deploy-staging:      # This job runs in the deploy stage.
  stage: deploy
  rules:
    - if: $CI_COMMIT_BRANCH == "Staging"
  tags:
    - staging
  script:
    - echo "Stopping Webapp container..."
    - docker rm --force $DOCKER_IMAGE_NAME || exit_code=$?
    - echo "Running built Webapp container..."
    - docker run --mount type=volume,source=$VOLUME_NAME,target=$VOLUME_TARGET --name $DOCKER_IMAGE_NAME $DOCKER_IMAGE_NAME npm run build:staging
    - docker ps -ls #print the state of the last created container

# PRODUCTION

build-production:       # This job runs in the build stage, which runs first.
  stage: build
  rules:
    - if: $CI_COMMIT_BRANCH == "Production"
  tags:
    - staging
  script:
    - echo "Building the Webapp"
    - cp dockerfiles/Dockerfile.prod Dockerfile
    - docker build --target build -t $PROD_DOCKER_IMAGE_NAME .
    - echo "Building completed."

deploy-production:      # This job runs in the deploy stage.
  stage: deploy
  rules:
    - if: $CI_COMMIT_BRANCH == "Production"
  tags:
    - staging
  script:
    - echo "Stopping Webapp container..."
    - docker rm --force $PROD_DOCKER_IMAGE_NAME || exit_code=$?
    - echo "Running built Webapp container..."
    - docker run --mount type=volume,source=$PROD_VOLUME_NAME,target=$VOLUME_TARGET --name $PROD_DOCKER_IMAGE_NAME $PROD_DOCKER_IMAGE_NAME npm run build:prod
    - docker ps -ls #print the state of the last created container
```

#  Novathena api
``` yaml
workflow:
stages:          # List of stages for jobs, and their order of execution
  - build
  - deploy

build-staging:       # This job runs in the build stage, which runs first.
  stage: build
  rules:
    - if: $CI_COMMIT_BRANCH == "Staging"
  tags:
    - staging
  script:
    - echo "Building for Staging"
    - printf $ENV >> .env
    - cp dockerfiles/Dockerfile.prod Dockerfile
    - docker build --no-cache --rm --target production -t $DOCKER_IMAGE_NAME .
    - echo "Building completed."

deploy-staging:      # This job runs in the deploy stage.
  stage: deploy
  rules:
    - if: $CI_COMMIT_BRANCH == "Staging"
  tags:
    - staging
  environment: staging
  script:
    - echo "Deploying application..."
    - echo "Stopping API container..."
    - docker rm --force $DOCKER_IMAGE_NAME || exit_code=$?
    - docker run -it -d -p $EXPOSED_SOCKET_PORT:443 -p $DOCKER_EXPOSED_PORT:3000 --mount source=$RESTARTER_VOLUME,target=$RESTARTER_FOLDER --mount type=bind,source=$ASSETS,target=/assets --net $DOCKER_BACKEND_NETWORK --restart always --name $DOCKER_IMAGE_NAME $DOCKER_IMAGE_NAME
    - docker network connect $OLD_NETWORK $DOCKER_IMAGE_NAME
    - echo "Application successfully deployed."

# PRODUCTION

build-production:       # This job runs in the build stage, which runs first.
  stage: build
  rules:
    - if: $CI_COMMIT_BRANCH == "Production"
  tags:
    - production
  script:
    - echo "Building for Staging"
    - printf $PROD_ENV >> .env
    - cp dockerfiles/Dockerfile.prod Dockerfile
    - docker build --no-cache --rm --target production -t $PROD_DOCKER_IMAGE_NAME .
    - echo "Building completed."

deploy-production:      # This job runs in the deploy stage.
  stage: deploy
  rules:
    - if: $CI_COMMIT_BRANCH == "Production"
  tags:
    - production
  environment: production
  script:
    - echo "Deploying application..."
    - echo "Stopping API container..."
    - docker rm --force $PROD_DOCKER_IMAGE_NAME || exit_code=$?
    - docker run -it -d -p $PROD_EXPOSED_SOCKET_PORT:443 -p $PROD_DOCKER_EXPOSED_PORT:3000 --mount source=$RESTARTER_VOLUME,target=$RESTARTER_FOLDER --mount type=bind,source=$ASSETS_PROD,target=/assets --net $DOCKER_BACKEND_NETWORK --restart always --name $PROD_DOCKER_IMAGE_NAME $PROD_DOCKER_IMAGE_NAME
    - docker network connect $OLD_NETWORK $PROD_DOCKER_IMAGE_NAME
    - echo "Application successfully deployed."
```

#  Novathena webapp
``` yaml
workflow:
stages:          # List of stages for jobs, and their order of execution
  - build
  - deploy

build-staging:       # This job runs in the build stage, which runs first.
  stage: build
  rules:
    - if: $CI_COMMIT_BRANCH == "Staging"
  tags:
    - staging
  script:
    - echo "Building the Backoffice"
    - cp dockerfiles/Dockerfile.prod Dockerfile
    - docker build --target build -t $DOCKER_IMAGE_NAME .
    - echo "Building completed."

deploy-staging:      # This job runs in the deploy stage.
  stage: deploy
  rules:
    - if: $CI_COMMIT_BRANCH == "Staging"
  tags:
    - staging
  script:
    - echo "Stopping Backoffice container..."
    - docker rm --force $DOCKER_IMAGE_NAME || exit_code=$?
    - echo "Running built Backoffice container..."
    - docker run --mount type=volume,source=$VOLUME_NAME,target=$VOLUME_TARGET --name $DOCKER_IMAGE_NAME $DOCKER_IMAGE_NAME npm run build:staging
    - docker ps -ls #print the state of the last created container

# PRODUCTION

build-production:       # This job runs in the build stage, which runs first.
  stage: build
  rules:
    - if: $CI_COMMIT_BRANCH == "Production"
  tags:
    - staging
  script:
    - echo "Building the Backoffice"
    - cp dockerfiles/Dockerfile.prod Dockerfile
    - docker build --target build -t $PROD_DOCKER_IMAGE_NAME .
    - echo "Building completed."

deploy-production:      # This job runs in the deploy stage.
  stage: deploy
  rules:
    - if: $CI_COMMIT_BRANCH == "Production"
  tags:
    - staging
  script:
    - echo "Stopping Backoffice container..."
    - docker rm --force $PROD_DOCKER_IMAGE_NAME || exit_code=$?
    - echo "Starting built Backoffice container..."
    - docker run --mount type=volume,source=$PROD_VOLUME_NAME,target=$VOLUME_TARGET --name $PROD_DOCKER_IMAGE_NAME $PROD_DOCKER_IMAGE_NAME npm run build:prod
    - docker ps -ls #print the state of the last created container
```