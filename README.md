```bash
anlinh@Mac ex02 % open -a Docker
anlinh@Mac ex02 % docker version
Client:
 Version:           29.7.2
 API version:       1.55
 Go version:        go1.26.5
 Git commit:        a7dcaa6
 Built:             Wed Aug  5 18:27:50 2026
 OS/Arch:           darwin/arm64
 Context:           desktop-linux

Server: Docker Desktop 4.90.0 (238679)
 Engine:
  Version:          29.7.2
  API version:      1.55 (minimum version 1.40)
  Go version:       go1.26.5
  Git commit:       6a43e3d
  Built:            Wed Aug  5 18:28:35 2026
  OS/Arch:          linux/arm64
  Experimental:     false
 containerd:
  Version:          v2.3.3
  GitCommit:        aad11006b869517fcd3009450b6f82da282e1a9b
 runc:
  Version:          1.4.3
  GitCommit:        v1.4.3-0-gbb14dabe
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
anlinh@Mac ex02 % docker build -t hw-backend:v1 .
[+] Building 13.5s (10/10) FINISHED                            docker:desktop-linux
 => [internal] load build definition from Dockerfile                           0.0s
 => => transferring dockerfile: 195B                                           0.0s
 => [internal] load metadata for docker.io/library/node:18-alpine              4.4s
 => [internal] load .dockerignore                                              0.0s
 => => transferring context: 2B                                                0.0s
 => [1/5] FROM docker.io/library/node:18-alpine@sha256:8d6421d663b4c28fd3ebc4  5.9s
 => => resolve docker.io/library/node:18-alpine@sha256:8d6421d663b4c28fd3ebc4  0.0s
 => => sha256:8bfa36aa66ce614f6da68a16fb71f875da8d623310f0cb8 1.26MB / 1.26MB  0.9s
 => => sha256:02bb84e9f3412827f177bc6c020812249b32a8425d2c1858e9d 443B / 443B  0.3s
 => => sha256:d84c815451acbca96b6e6bdb479929222bec57121dfe1 39.66MB / 39.66MB  5.3s
 => => extracting sha256:d84c815451acbca96b6e6bdb479929222bec57121dfe10cc5b12  0.5s
 => => extracting sha256:8bfa36aa66ce614f6da68a16fb71f875da8d623310f0cb80ae1e  0.0s
 => => extracting sha256:02bb84e9f3412827f177bc6c020812249b32a8425d2c1858e9d7  0.0s
 => [internal] load build context                                              0.0s
 => => transferring context: 604B                                              0.0s
 => [2/5] WORKDIR /app                                                         0.1s
 => [3/5] COPY package.json ./                                                 0.0s
 => [4/5] RUN npm install --omit=dev                                           2.7s
 => [5/5] COPY server.js ./                                                    0.0s
 => exporting to image                                                         0.4s
 => => exporting layers                                                        0.1s
 => => exporting manifest sha256:eda5f2a143b6e7613782ce8a26ca035bd206fb1bb890  0.0s
 => => exporting config sha256:48ce3b609abf1fceaac08b7fab2f0494f47f9a74b5317f  0.0s
 => => exporting attestation manifest sha256:70e176bf7f0a023f666d79db988e6f7d  0.0s
 => => exporting manifest list sha256:84a619a4ab73bbe56c06a1c14ae62ba179ed5ed  0.0s
 => => naming to docker.io/library/hw-backend:v1                               0.0s
 => => unpacking to docker.io/library/hw-backend:v1                            0.2s

View build details: docker-desktop://dashboard/build/desktop-linux/desktop-linux/jqi226vjjja342dki61zuzwsh
anlinh@Mac ex02 % docker run -d --name app-single-stage -p 8080:3000 hw-backend:v1
1174b5820347cc1e75ac646e8fb4b6e1e466b594816713b91e1364b2c7290bd2
anlinh@Mac ex02 % docker ps --filter name=app-single-stage
docker logs app-single-stage
curl -i http://localhost:8080/
CONTAINER ID   IMAGE           COMMAND                  CREATED         STATUS         PORTS                                         NAMES
1174b5820347   hw-backend:v1   "docker-entrypoint.s…"   4 seconds ago   Up 3 seconds   0.0.0.0:8080->3000/tcp, [::]:8080->3000/tcp   app-single-stage
Server listening on port 3000
HTTP/1.1 200 OK
X-Powered-By: Express
Content-Type: application/json; charset=utf-8
Content-Length: 100
ETag: W/"64-X6dmrnSif/iQ8a4MU/3aYV44T1k"
Date: Mon, 12 Oct 2026 16:03:14 GMT
Connection: keep-alive
Keep-Alive: timeout=5

{"status":"success","message":"Hello from Docker Single-stage!","student":"Dang Khanh An - PTIT070"}%
```
