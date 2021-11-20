Enables the use of the aws command line in your Github action

# Usage

<!-- start usage -->
```yaml
- uses: nrccua/github-action-install-awscli
  with:
    # AWS Access Key See [Managing access keys for IAM users](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html) on generating an access key/secret key pair.
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
