# GitOps Documentation
- This documentation is for Argocd configuration  

## Requirement  
- [Install Helm](https://helm.sh/docs/intro/install/)  
- Container image  
- DNS  
- Certificate  
- Configuration for containers  

---

## Basic Usage  
- For `Web Application` and `API Server`  
  - Configuration `sample-web/values.yaml` , only change values.  
    - namespace  
      - Description: Application located where you what  
    - app.name  
      - Description: Application naming  
    - app.port  
      - Description: container port  
    - app.targetPort  
      - Description: container port forwards  
    - app.resources.limits (all values)  
      - Description: container cpu and memory limits  
    - app.resources.requests (all values)  
      - Description: contaienr cpu and memory request  
    - volumeMounts (all values)  
      - Description: contianer mountpoints  
    - volumes (all values)  
      - Description: container volume defined  
    - configReload  
      - Description: if you want to reload configuration and container restart please enable , change this value `false` to `true`  
    - ingress.enabled  
      - Description: if your application need gave each other endpoint please enabled , change this value `false` to `true`  
    - ingress.hostname  
      - Description: your application domain name  
    - ingress.crt
      - Description: your application certificate , please encrypted with base64  
    - ingress.key
      - Description: your application certificate key , please encrypted with base64  
  - Container configuration  
    - Please put your configuration file into `conf/`  
    - In this sample we used `json` and `yaml`  
- `Cronjob` configuration  
  - cronjob.enabled
    - Descritpion: if you want to used cronjob please enabled , change this value `false` to `true`  

---

## Test before deploy to ArgoCD
- We can use the helm command for a final check before deployment.
- Go to your Chart folder.  
  - example: `sample-web`.  
  ```shell=
  ## example cmd
  helm template ${release} . -f values.yaml > .\out\${file_name}.yaml

  ## currently cmd
  helm template test . -f values.yaml > .\out\sample-output.yaml
  ```
- There have a sample in `sample-web/out/sample-output.yaml` .  