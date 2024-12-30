# Builder
FROM --platform=linux/amd64 docker.apple.com/base-images/ubi9/node20-builder:latest AS build
COPY gen/srv ./
RUN npm ci --omit=dev --maxsockets 1


FROM --platform=linux/amd64 docker.apple.com/base-images/ubi9-minimal/node20-runtime:latest
COPY --chown=$NON_ROOT_USER:$NON_ROOT_USER --from=build . .
# Manually updated command
CMD ["npm", "run" ,"start-kyma"]
