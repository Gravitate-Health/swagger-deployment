Swagger kubernetes deployment
=================================================

Table of contents
-----------------
- [Swagger deployment](#swagger-deployment)
  - [Table of contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Installation](#installation)
    - [Requirements](#requirements)
    - [Kubernetes deployment](#kubernetes-deployment)
    - [Adding new swagger pages](#adding-new-swagger-pages)
  - [Usage](#usage)
  - [Known issues and limitations](#known-issues-and-limitations)
  - [Getting help](#getting-help)
  - [Contributing](#contributing)
  - [License](#license)
  - [Authors and history](#authors-and-history)

Introduction
------------

Swagger deploymnet for the project API documnetation.

Installation
------------
### Requirements

kubectl and access to a kubernetes cluster is required.


### Kubernetes deployment

For the Kubernetes deployment first of all, the istio setup must be running

```bash
git clone <link-to-repo>
cd swagger-GH
```
To set up the swagger with the keycloak api we need to apply the configmap

```bash
kubectl apply -f YAMLs/001_keycloak-api-configmap.yaml
```

Then apply the swagger deployment with the nuimber of replicas needed

```bash
kubectl apply -f YAMLs/002_swagger-deployment.yaml
```

To set up the service and the virtual service for Istio

```bash
kubectl apply -f YAMLs/003_swagger-service.yaml
kubectl apply -f YAMLs/004_swagger-vs.yaml
```

### Adding new swagger pages

In order to add or modify new swagger pages the [YAMLs/002_swagger-deployment.yaml]() must be modify in the following section

```yaml
...

- name: API_URLS
          value: >-
            [
            ... ,
            {url:'<url to the yaml>',name:'Example swagger name'}
            ]
...
```



Usage
-----
There an endpoint avaible on \<base-url>/swagger-fosps where you can access the different swaggers pages avaible.


Known issues and limitations
----------------------------

Nothing noticed yet.

Getting help
------------
In case you find a problem or you need extra help, please use the issues tab to report the issue.

Contributing
------------
To contribute, fork this repository and send a pull request with the changes squashed.

License
------------

This project is distributed under the terms of the [Apache License, Version 2.0 (AL2)](https://www.apache.org/licenses/LICENSE-2.0). The license applies to this file and other files in the [GitHub repository](https://github.com/Gravitate-Health/swagger-fosps) hosting this file.
```
Copyright 2022 Universidad Politécnica de Madrid

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

Authors and history
---------------------------
- Alejo Esteban ([@10alejospain](https://github.com/10alejospain))
