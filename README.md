# packer-aws-repo

Create a nginx AWS box ubuntu lts, using Apple Mac M1 Pro

# How to use this repo 

- First, install the HashiCorp tap, a repository of all our Homebrew packages.
```
brew tap hashicorp/tap
```

- Now, install Packer with hashicorp/tap/packer.
```
brew install hashicorp/tap/packer
```

- To update to the latest, run
```
brew upgrade hashicorp/tap/packer
```

- Veryify instalation 

```
packer
```
 
 - Create new directory named `packer_tutorial`. This directory will contain your Packer template.
```
  mkdir packer_tutorial
```

- Navigate into the directory.
```
  cd packer_tutorial
```
  
- Download/git clone this repo into the alredy created above folder, as the repo contains aws-ubuntu.pkr.hcl packer template file

```
git clone git@github.com:georgitsvetkov/packer-repo-aws.git
```
  
- Authenticate to AWS, using doormat

```
Navigate to https://doormat.hashicorp.services/ and select the key icon, copy the key ids and paste them into the CLI:
```

```
export AWS_ACCESS_KEY_ID=<key-id>
export AWS_SECRET_ACCESS_KEY=<key-id>
export AWS_SESSION_TOKEN=<key-id>
```

- Test that auth to AWS is being successfull by listing the S3 buckets in your account:
```
aws s3 ls
```

- Initialize Packer configuration

```
packer init .
```

- Format and validate your Packer template

```
packer fmt
```
```
packer validate
```

- Build Packer image

```
packer build aws-ubuntu.pkr.hcl
```

- Visit the [AWS AMI page](https://eu-west-1.console.aws.amazon.com/ec2/v2/home?region=eu-west-1#ImageDetails:imageId=ami-0e25fd084241a0d7f) to verify that Packer successfully built your AMI.

> `Disclaimer:` Please note that the above is being tested using Apple Mac M1 Pro, running macOS Monterey

