# AWS Translate Application

A web page to translate text into supported languages and use polly for audio outpout

## Prerequisites

Get an AWS account and some IAM User eligible to use AWS Translate and AWS Polly.
Set its access key and secret in the HTML page (NOT recommended):
```
AWS.config.credentials = new AWS.Credentials("access key", "secret key");
```

or use a proper security mechanism describe here:
https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-credentials-browser.html

As this does not work with AWS Cognito identities we need to use a Web Federated Identity for security:
https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/loading-browser-credentials-federated-id.html

## Run

```
docker run -it --rm -d -p 8080:80 --name web -v $(pwd)/translate.html:/usr/share/nginx/html/index.html nginx
```

## Build Custom Image

```
docker build -t translate .
```

```
docker run -it --rm -d -p 8080:80 --name web translate
```
