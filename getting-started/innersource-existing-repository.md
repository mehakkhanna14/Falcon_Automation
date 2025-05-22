# Innersourcing an existing repository

## Create an innersource repository

Create a [new repository on Philips-Internal Github](https://github.com/organizations/philips-internal/repositories/new)
__Note: ensure that you create no files, and do not use a template to ensure that you can import an existing repo in the next step__

## Push from ADS to Github

```POWERSHELL
git clone https://tfsemea1.ta.philips.com/tfs/TPC_Region22/IGT/_git/<YOUR-REPO>
cd .\<YOUR-REPO>\
git remote add innersource https://github.com/philips-internal/<YOUR-REPO>.git
git branch -M main
git push -u innersource main
```

In case the innersource repository, will be replacing the ADS repository: inform your users and remove the existing repository from ADS.
__Note: the complete history is transferred given GIT's distributed nature__

## Make adaptations for basic innersource compliance

See [Innersource continuous compliance](https://github.com/philips-internal/continuous-compliance) for more background information

* Copy the [license](../LICENSE), [code of conduct](../CODE_OF_CONDUCT.md), [contributing guidelines](CONTRIBUTING.md) from this repository,
* Create a list of [maintainers](../MAINTAINERS.md), and provide `maintainer` access to these users,
* Ensure the repository has a proper [ReadMe](../README.md),
* Copy the [Philips Repository Indexing file](../.github/philips-repo.yml) to the same location in your repository
