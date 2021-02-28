# gcloud-sync
A simple utility that will automatically create a backup of a Magento database, media directory and configuration from a host to Google Cloud Storage. 

## Local Setup
Download `gcloud`, `gsutil` via [Google Cloud SDK](https://cloud.google.com/storage/docs/quickstart-gsutil).

Login using a Google Account:
```
$ gcloud auth login `ACCOUNT`
```

Create a [Google Cloud Project](https://cloud.google.com/resource-manager/docs/creating-managing-projects):
```
$ gcloud projects create [PROJECT_NAME]
```

Create a [Google Cloud Storage Bucket](https://cloud.google.com/storage/docs/creating-buckets#storage-create-bucket-gsutil):
```
$ gsutil mb -c nearline -p [PROJECT_NAME] gs://[BUCKET_NAME]
```

Print temporary Google Account `[OAUTH2_TOKEN]`:
```
$ gcloud auth print-access-token
```

Add bash alias `gcs` to your `~/.bashrc` or `~/.zshrc`, just replace `[BUCKET_NAME]`:
```
alias gcs='echo "curl --silent https://raw.githubusercontent.com/X2Y-Development/gcloud-sync/master/gcloud-sync --output gcloud-sync && php gcloud-sync -t=$(gcloud auth print-access-token) -b=[BUCKET_NAME] -c -d -a -m -v && rm -f gcloud-sync"'
```

## Host Setup
SSH into a host, navigate to Magento web root directory and download the utility: 
```
$ curl https://raw.githubusercontent.com/X2Y-Development/gcloud-sync/master/gcloud-sync --output gcloud-sync
```

## Usage
``` 
$ php gcloud-sync 
```

```
Usage:
    -t      Google Account OAuth2 token
    -b      Google Cloud Storage bucket name
    -c      Sync Magento configuration files
    -a      Sync Magento media assets
    -d      Sync Magento database
    -m      Sync modules from app/code
    
Example:
    php gcloud-sync -c -a -d -t=[OAUTH2_TOKEN] -b=[BUCKET_NAME] 

X2Y Development <dev@x2y.io>
```
