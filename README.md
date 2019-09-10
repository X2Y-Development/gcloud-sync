# gcloud-sync
A simple utility that will automatically create a backup of a Magento database, media directory and configuration from a host to Google Cloud Storage. 

## Local Setup
Download `gcloud`, `gsutil` via [Google Cloud SDK](https://cloud.google.com/storage/docs/quickstart-gsutil).

Login using a Google Account:
```
$ gcloud auth login `ACCOUNT`
```
Set default project:
```
$ gcloud config set project x2y-development
```
or create a new one. [Documentation](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

Print Google Account authentication token:
```
$ gcloud auth print-access-token
```

## Host Setup
Log into a host, navigate to Magento web root directory and download the utility: 
```
$ curl https://raw.githubusercontent.com/X2Y-Development/gcloud-sync/master/gcloud-sync --output gcloud-sync
```

## Usage
```
$ php gcloud 
```

```
Usage:
    -t      Temporary oauth2 token.
    -c      Sync env.php or local.xml
    -a      Sync assets
    -d      Sync database
    
Example:
    php gcloud-sync -c -a -d -t=ya29.Glx-Byl-vhVow_4e1RW-tp8bp39uMjwRRz-45HrUz-r68vMGohU0qv6FE2vTXQb7ndvdMcvANyeBxSFteV3t2RSJgzG5dyvxz8iIfQfyNKqm9LN1syqwkLKULNhjG

X2Y Development <dev@x2y.io>
```
