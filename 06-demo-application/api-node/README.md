```bash
nvm ls
nvm use node 19.4
npm install
npm run dev
```

## without using task
export IMAGE_REPO="safwat3112/demo-api-node"
export IMAGE_TAG="1.0"
docker buildx build \
        --platform linux/amd64,linux/arm64 \
        -t $IMAGE_REPO:$IMAGE_TAG \
        --push \
        .