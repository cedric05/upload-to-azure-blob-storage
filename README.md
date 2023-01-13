# upload-to-azure-blob-storage

```yaml
on: [push]

jobs:
  upload-to-azure-blob:
    runs-on: ubuntu-latest
    name: uploads to azure blob storage container
    steps:
      - uses: actions/checkout@v3
      - id: upload-blob
        uses: cedric05/upload-to-azure-blob-storage@v1
        with:
            source-file: a.out # source file to upload
            base-project-path: c++_projects/first-project # az backup directory
            target-file: hello-world # az target file name
            overwrite: 'true' #optional
            container-name: container-name # az storage container name
            storage-account-name: storage-account-name # az storage account name
            creds: ${{ secrets.AZURE_CREDENTIALS }} # az create rbac output
```

## Use with credential

This credentials feature is for sharing same credentials with [azure-login](https://github.com/marketplace/actions/azure-login).  
How to create Azure credentials?  
-> Please check [azure-login page](https://github.com/marketplace/actions/azure-login#configure-azure-credentials).

# Develop

install-azcopy-action is tested below.
- ubuntu-22.04
- ubuntu-20.04(ubuntu-latest)
- ubuntu-18.04

[GitHub - Supported runners](https://docs.github.com/en/free-pro-team@latest/actions/reference/specifications-for-github-hosted-runners#supported-runners-and-hardware-resources)
If you need to add another environment, please post a issue.