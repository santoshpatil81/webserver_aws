# webserver_aws

## File Structure

```
.
├── ...
├── webserver_aws                 # Root folder
├── .github/workflows             # Github actions workflow directory
    ├── deploy_oidc_iam.yml       # Workflow to deploy OIDC, IAM roles
    ├── deploy_webserver.yml      # Workflow to deploy core networking and setup webserver
├── oidc_IAM                      # Folder containing OIDC,IAM changes
    ├── setup.yml                 # .yml file including OIDC,IAM changes
├── core_networking_webserver     # Folder containing core networking and setup webserver
    ├── setup.yml                 # .yml file including core networking and setup webserver
```

### .github/workflows

#### deploy_oidc_iam.yml

This workflow deploys changes to configure AWS to trust GitHub's OIDC as a federated identity (actual changes included in `oidc_IAM/setup.yml`), so that we could use the github action `aws-actions/configure-aws-credentials`. By utilizing OIDC we configure AWS to trust GitHub as a federated identity provider, and then use ID tokens in Github Actions workflows to authenticate to AWS and access resources. We also create IAM roles for github workflows and allow workflows to assume those roles.

The workflow can only be triggered by users included in the `Dev-Deployers` group.

This workflow also validated the CloudFormation template using `cfn-lint` before actually deploying it.

You can access the workflow here - `https://github.com/santoshpatil81/webserver_aws/actions/workflows/deploy_oidc_iam.yml`

#### deploy_webserver.yml

This workflow deploys changes to setup core networking and creates webserver that copies a file from an S3 bucket and renders it. The actual changes are included in `core_networking_webserver/setup.yml`

#### oidc_IAM/setup.yml

This .yml file includes changes to configure AWS to trust GitHub's OIDC as a federated identity, so that we could use the github action `aws-actions/configure-aws-credentials`. By utilizing OIDC we configure AWS to trust GitHub as a federated identity provider, and then use ID tokens in Github Actions workflows to authenticate to AWS and access resources. We also create IAM roles for github workflows and allow workflows to assume those roles.

The workflow can only be triggered by users included in the `Dev-Deployers` group.

This workflow also validated the CloudFormation template using `cfn-lint` before actually deploying it.

You can access the workflow here - `https://github.com/santoshpatil81/webserver_aws/actions/workflows/deploy_webserver.yml`

#### core_networking_webserver/setup.yml

This .yml includes changes to setup core networking and creates webserver that copies a file from an S3 bucket and renders it.
