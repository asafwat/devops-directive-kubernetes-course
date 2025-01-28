```bash
mkdir go-workspace
export GOPATH=$PWD/go-workspace
go mod download
go run main.go
```

## without using task
export IMAGE_REPO="safwat3112/demo-api-golang"
export IMAGE_TAG="1.0"
KO_DOCKER_REPO=$IMAGE_REPO \
          ko build \
          --bare \
          --tags=$IMAGE_TAG \
          --platform=all