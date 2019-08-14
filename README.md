
# This is a Helm starter for go projects

Starter packs are described in the [helm documentation](https://docs.helm.sh/developing_charts/#chart-starter-packs). 
They're handy in order to initialize a new project for deployment onto Kubernetes. 

# Installation

This starter is automatically installed by the helm [pipeline plugin](https://github.com/myspotontheweb/helm-pipeline-plugin)

```
sudo apt-get install -y make git gettext-base
helm plugin install https://github.com/myspotontheweb/helm-pipeline-plugin.git
```

# Usage

```
helm pipeline NAME=my-project NAMESPACE=myteam PORT=9001 ORG=myspotontheweb STARTER=go
```

## Recreating files

You can regenerate the files by first deleting them

```
$ helm pipeline clean
rm -rf chart
rm -f Dockerfile
rm -f .travis.yml

$ helm pipeline NAME=my-project NAMESPACE=myteam PORT=9001 ORG=myspotontheweb STARTER=go
Creating myproject
cat chart/.ci/Dockerfile | envsubst '$NAME $FILTERED_NAME $NAMESPACE $PORT' > Dockerfile
cat chart/.ci/.travis.yml | envsubst '$NAME $FILTERED_NAME $NAMESPACE $PORT' > .travis.yml
```

## Remove caching

Helm chart starter packs are stored under the helm client homedir: *~/.helm/starters*

```
$ helm pipeline clean-starter STARTER=go
rm -rf /home/mark/.helm/starters/go
```
