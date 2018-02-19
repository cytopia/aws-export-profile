# aws-export-profile

`aws-export-profile` is a bash script that will output AWS export statements of your chosen aws boto profile.

Wrap the command in `$(aws-export-profile)` to actually export your boto environment variables.


## Available exports

| Variable               | Description |
|------------------------|-------------|
| `AWS_ACCESS_KEY`       | Access key  |
| `AWS_ACCESS_KEY_ID`    | Alternative name for `AWS_ACCESS_KEY`|
| `AWS_SECRET_KEY`       | Secret key  |
| `AWS_SECRET_ACCESS_KEY`| Alternative name for `AWS_SECRET_KEY`|
| `AWS_SESSION_TOKEN`    | Session token |
| `AWS_SECURITY_TOKEN`   | Secret token |
| `AWS_REGION`           | Region|


## Examples

This tool simply output the exports to stdout. In order to auto-source them, wrap the command in `$(...)`.

#### Boto profile `testing`

```bash
$ aws-export-profile testing

export AWS_ACCESS_KEY_ID="XXXXXXXXXXXXXXXXXXXX"
export AWS_ACCESS_KEY="XXXXXXXXXXXXXXXXXXXX"
export AWS_SECRET_ACCESS_KEY="A1Bc/XXXXXXXXXXXXXXXXXXXXXXXXXXX"
export AWS_SECRET_KEY="A1Bc/XXXXXXXXXXXXXXXXXXXXXXXXXXX"
export AWS_REGION="eu-central-1"
```

#### Boto profile `testing` with custom paths

```bash
$ aws-export-profile deploy /jenkins/aws/credentials /jenkins/aws/config

export AWS_ACCESS_KEY_ID="XXXXXXXXXXXXXXXXXXXX"
export AWS_ACCESS_KEY="XXXXXXXXXXXXXXXXXXXX"
export AWS_SECRET_ACCESS_KEY="A1Bc/XXXXXXXXXXXXXXXXXXXXXXXXXXX"
export AWS_SECRET_KEY="A1Bc/XXXXXXXXXXXXXXXXXXXXXXXXXXX"
export AWS_REGION="eu-central-1"
```

#### Boto profile `production` with more exports
```bash
$ aws-export-profile production

export AWS_ACCESS_KEY_ID="XXXXXXXXXXXXXXXXXXXX"
export AWS_ACCESS_KEY="XXXXXXXXXXXXXXXXXXXX"
export AWS_SECRET_ACCESS_KEY="A1Bc/XXXXXXXXXXXXXXXXXXXXXXXXXXX"
export AWS_SESSION_TOKEN="XXXXXXXXXXXXXXXXx/XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX/XXXXXXXXXXXXXXXXXXXXXXXX/XXXXXXXXXXXXXXXXXXX/XXXXXXXXXXXX="
export AWS_SECRET_KEY="A1Bc/XXXXXXXXXXXXXXXXXXXXXXXXXXX"
export AWS_REGION="eu-central-1"
```


## Usage

```bash
Usage: aws-export-profile [profile] [credentials] [config]

This bash helper will output AWS export statements of your chosen aws boto profile.
Wrap this script in $(aws-export-profile) to export those environment variables.

Optional arguments:
    [profile]      Boto profile name to export. Default is 'default'
    [credentials]  Path to your aws credentials file.
                   Default is ~/.aws/credentials
    [config]       Path to your aws config file.
                   If no config file is found, AWS_REGION export will not be available.
                   Default is ~/.aws/config

Available exports:
    AWS_ACCESS_KEY_ID
    AWS_ACCESS_KEY
    AWS_SECRET_ACCESS_KEY
    AWS_SECRET_KEY
    AWS_SESSION_TOKEN
    AWS_SECURITY_TOKEN
    AWS_REGION

Examples to show output:
    aws-export-profile testing
    aws-export-profile production /jenkins/aws/credentials /jenkins/aws/config

Examples to export:
    $(aws-export-profile testing)
    $(aws-export-profile production /jenkins/aws/credentials /jenkins/aws/config)
```

## License

**[MIT License](LICENSE.md)**

Copyright (c) 2018 [cytopia](https://github.com/cytopia)
