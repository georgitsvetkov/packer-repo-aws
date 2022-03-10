# packer-aws-repo

Create a nginx AWS box ubuntu lts - README.md with instructions (gh repo)

# How to use this repo 

- First, install the HashiCorp tap, a repository of all our Homebrew packages.
`
brew tap hashicorp/tap
`

- Now, install Packer with hashicorp/tap/packer.
`
brew install hashicorp/tap/packer
`

- To update to the latest, run
`
brew upgrade hashicorp/tap/packer
`

- Veryify instalation 

````````````
$ packer
Usage: packer [--version] [--help] <command> [<args>]

Available commands are:
    build           build image(s) from template
    console         creates a console for testing variable interpolation
    fix             fixes templates from old versions of packer
    fmt             Rewrites HCL2 config files to canonical format
    hcl2_upgrade    transform a JSON template into an HCL2 configuration
    init            Install missing plugins or upgrade plugins
    inspect         see components of a template
    validate        check that a template is valid
    version         Prints the Packer version
````````````  
 
 - Create new directory named `packer_tutorial`. This directory will contain your Packer template.
  `
  mkdir packer_tutorial
  `

- Navigate into the directory.
  `
  cd packer_tutorial
  `
  
- Download/git clone this repo into the alredy created above folder, as the repo contains aws-ubuntu.pkr.hcl packer template file

`
git clone git@github.com:georgitsvetkov/packer-repo-aws.git
`
  
- Authenticate to AWS, using doormat

`
Navigate to https://doormat.hashicorp.services/ and select the key icon, copy the key ids and paste them into the CLI:
`

```
export AWS_ACCESS_KEY_ID=<key-id>
export AWS_SECRET_ACCESS_KEY=<key-id>
export AWS_SESSION_TOKEN=<key-id>
```

- Test that auth to AWS is being successfull by listing the S3 buckets in your account:
`
aws s3 ls
`

- Initialize Packer configuration

`
packer init .
`

- Format and validate your Packer template

`
packer fmt
`
`
packer validate
`

- Build Packer image

`
packer build aws-ubuntu.pkr.hcl
`

- Visit the [AWS AMI page](https://eu-west-1.console.aws.amazon.com/ec2/v2/home?region=eu-west-1#ImageDetails:imageId=ami-0e25fd084241a0d7f) to verify that Packer successfully built your AMI.
