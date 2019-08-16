
# This is a Helm chart starter pack

Starter packs are described in the [helm documentation](https://docs.helm.sh/developing_charts/#chart-starter-packs). 
They're handy in order to initialize a new project for deployment onto Kubernetes. 

# Installation

This starter is automatically installed by the helm [starter plugin](https://github.com/myspotontheweb/helm-starter-plugin)

```
sudo apt-get install -y make git gettext-base
helm plugin install https://github.com/myspotontheweb/helm-starter-plugin.git
```

# Usage

```
helm starter NAME=my-project NAMESPACE=myteam PORT=9001 ORG=myspotontheweb STARTER=default
```

## Recreating files

You can regenerate the files by first deleting them

```
$ helm starter clean
rm -rf chart
rm -f Dockerfile
rm -f .travis.yml

$ helm starter NAME=my-project NAMESPACE=myteam PORT=9001 ORG=myspotontheweb STARTER=default
Creating myproject
cat chart/.ci/Dockerfile | envsubst '$NAME $FILTERED_NAME $NAMESPACE $PORT' > Dockerfile
cat chart/.ci/.travis.yml | envsubst '$NAME $FILTERED_NAME $NAMESPACE $PORT' > .travis.yml
```

## Remove caching

Helm chart starter packs are stored under the helm client homedir: *~/.helm/starters*

```
$ helm starter clean-starter STARTER=default
rm -rf /home/mark/.helm/starters/default
```
