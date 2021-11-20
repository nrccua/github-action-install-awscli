Enables the use of the `aws` command line in your Github action. See [Managing access keys for IAM users](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html) on generating an access key/secret key pair.

# Usage

<!-- start usage -->
```yaml
- uses: nrccua/github-action-install-awscli
  with:
    # AWS Access Key
    # Required: True
    aws_key_id: ''

    # AWS Secret Access Key
    # Required: True
    aws_secret_access_key: ''

    # The AWS Region to use
    # Default: us-east-1
    # Required: False
    aws_region: ''
```
<!-- end usage -->

# Example
```yaml
name: Deploy To S3

on:
  push:
    branches:
      - master

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
      with:
        persist-credentials: false
    - run: my_build.sh
    - name: Install AWS CLI
      uses: nrccua/github-action-install-awscli@master
      with:
        aws_key_id: ${{ secrets.AWS_ACCESS_KEY_ID }}
        aws_secret_access_key: ${{ secrets.AWS_SECRET_KEY_ID }}
        aws_region: ${{ secrets.AWS_REGION }}
    - name: Copy files to S3
      shell: bash
      env:
        aws_s3_bucket: ${{ secrets.AWS_S3_BUCKET }}
      run: |
        # Copy up build to s3
        aws s3 cp --acl public-read --recursive ./my_build_directoy s3://$aws_s3_bucket/
```
