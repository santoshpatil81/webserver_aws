# webserver_aws

## Setup OIDC

This file configures AWS to trust GitHub's OIDC as a federated identity, so that we could use the github action `aws-actions/configure-aws-credentials` that uses tokens to authenticate to AWS and access resources.
