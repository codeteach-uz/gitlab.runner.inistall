# gitlab.runner.inistall
## Install runner
### 1. Simply download one of the binaries for your system:
```shell
sudo curl -L --output /usr/local/bin/gitlab-runner "https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-linux-amd64"
```
### 2. Give it permissions to execute:
```shell
sudo chmod +x /usr/local/bin/gitlab-runner
```
### 3. Create a GitLab CI user:
```shell
sudo useradd --comment 'GitLab Runner' --create-home gitlab-runner --shell /bin/bash
```
### 4. Install and run as service:
```js
sudo gitlab-runner install --user=gitlab-runner --working-directory=/home/gitlab-runner
sudo gitlab-runner start
```
### 5. Register executor
```shell
sudo gitlab-runner register -n \
  --url https://gitlab.com/ \
  --registration-token $TOKEN \
  --executor docker \
  --description "crm-backend-runner" \
  --docker-image "alpine:latest" \
  --docker-privileged \
  --docker-volumes "/certs/client"
  --run-untagged="true" \
  --locked="false" \
  --access-level="not_protected"`
```  
  
### Verify executor
sudo gitlab-runner verify
