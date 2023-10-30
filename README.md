# datasets-tables-bq-pulumi

This project shows how to create BigQuery Datasets with tables using Pulumi and elegant/scalable Json configuration.\
This use cas was previously created with Terraform and the goal is to rewrite it with Pulumi and the Python SDK.

The link to the article with the use case created with Terraform : 

https://medium.com/google-cloud/create-bigquery-datasets-and-tables-with-terraform-in-an-elegant-and-scalable-way-84eab21c1b96

![datasets_with_tables_one_module_terraform.png](images%2Fdatasets_with_tables_one_module_terraform.png)

## Build from local machine

### Set env vars in your Shell

```shell
export PROJECT_ID={{your_project_id}}
export LOCATION={{your_location}}
```

### Preview

```shell
gcloud builds submit \
    --project=$PROJECT_ID \
    --region=$LOCATION \
    --config pulumi-preview-infra.yaml \
    --verbosity="debug" .
```


### Update

```shell
gcloud builds submit \
    --project=$PROJECT_ID \
    --region=$LOCATION \
    --config pulumi-update-infra.yaml \
    --verbosity="debug" .
```

### Destroy

```shell
gcloud builds submit \
    --project=$PROJECT_ID \
    --region=$LOCATION \
    --config pulumi-destroy-infra.yaml \
    --verbosity="debug" .
```

## Build from the project hosted in a GITHUB repository

### Preview

```shell
gcloud beta builds triggers create manual \
  --project=$PROJECT_ID \
  --region=$LOCATION \
  --name="datasets-tables-pulumi-preview" \
  --repo="https://github.com/tosun-si/datasets-tables-bq-pulumi" \
  --repo-type="GITHUB" \
  --branch="main" \
  --build-config="pulumi-preview-infra.yaml" \
  --verbosity="debug"
```

### Update

```shell
gcloud beta builds triggers create manual \
  --project=$PROJECT_ID \
  --region=$LOCATION \
  --name="datasets-tables-pulumi-update" \
  --repo="https://github.com/tosun-si/datasets-tables-bq-pulumi" \
  --repo-type="GITHUB" \
  --branch="main" \
  --build-config="pulumi-update-infra.yaml" \
  --verbosity="debug"
```

### Destroy

```shell
gcloud beta builds triggers create manual \
  --project=$PROJECT_ID \
  --region=$LOCATION \
  --name="datasets-tables-pulumi-destroy" \
  --repo="https://github.com/tosun-si/datasets-tables-bq-pulumi" \
  --repo-type="GITHUB" \
  --branch="main" \
  --build-config="pulumi-destroy-infra.yaml" \
  --verbosity="debug"
```


