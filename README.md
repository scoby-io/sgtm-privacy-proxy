# Scoby Analytics Tag for Google Tag Manager Server-side

[scoby](https://www.scoby.io) is an ethical analytics tool that helps you protect your visitors' privacy without sacrificing meaningful metrics. The data is sourced directly from your web server, no cookies are used and no GDPR, ePrivacy and Schrems II consent is required.

Start your free trial today [https://app.scoby.io/register](https://app.scoby.io/register)

#### Did you know?
scoby is free for non-profit projects.
[Claim your free account now](mailto:hello@scoby.io?subject=giving%20back)

## Overview

The Scoby Analytics Tag for [Google Tag Manager Server-side][gtm-ss] is a server-side tag for anonymously measuring your website usage in Scoby Analytics.

## Configuration

### API Key

The API Key from your Scoby Analytics [Workspace Settings](https://app.scoby.io).

### Secret Salt

A random and secret alphanumeric value that is used to anonymize all PII before it is transmitted to Scoby Analytics servers. You can generate use a [random string of 20 characters or more](https://codebeautify.org/generate-random-string) or generate a cryptographically secure salt value using 

````shell
openssl rand -base64 32
````

### Endpoint

The path in your Google Tagamanger Server-Side Container that the Scoby Analytics Template listens to. By default this is `/count`.

## Usage

To measure your website usage using the Scoby Analytics Tag you can just call a simple Javascript Tag. It is important though that you (your company) hosts the SGTM Container. This way you ensure that only anonymized data is transferred to Scoby Analytics. 

```javascript
new Image().src = `https://[YOUR_SGTM_INSTANCE_HOSTNAME]/count?url=${encodeURIComponent(document.location)}&ref=${encodeURIComponent(document.referrer)}`
```