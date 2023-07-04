# Scoby Analytics Privacy Proxy for Google Tag Manager Server-side

[Scoby](https://www.scoby.io) is a dedicated analytics tool designed with a strong emphasis on privacy, allowing you to gather important metrics without the use of cookies. This ensures that your visitors' privacy is respected and no consent is required under GDPR, ePrivacy, or Schrems II.

Start your free trial today [here](https://app.scoby.io/register)

#### A Special Offer
Scoby is available for free for non-profit projects.
[Apply for your free account now](mailto:hello@scoby.io?subject=giving%20back)

## Overview

Scoby Analytics Privacy Proxy for [Google Tag Manager Server-side](https://tagmanager.google.com) serves as a privacy-conscious, server-side tag for gauging your website usage. It acts as a proxy, anonymizing any personally identifiable information (PII) before it's sent to Scoby Analytics.

## Configuration

### API Key

Retrieve the API Key from your Scoby Analytics [Workspace Settings](https://app.scoby.io).

### Secret Salt

An obscure, unique alphanumeric value used to anonymize all PII before it's sent to Scoby Analytics. Generate a [random string of 20 characters or more](https://codebeautify.org/generate-random-string) or a cryptographically secure salt value using

````shell
openssl rand -base64 32
````

### Endpoint

This refers to the path in your Google Tag Manager Server-Side Container that the Scoby Analytics Privacy Proxy listens to. The default path is `/count`.

## Usage

To measure your website usage using the Scoby Analytics Privacy Proxy, simply call a JavaScript Tag. Ensure that your organization hosts the SGTM Container to guarantee that only anonymized data is transferred to Scoby Analytics.

Scoby Analytics Privacy Proxy exposes one endpoint requiring two parameters: the currently visited URL and the referring URL. All parameters, except known (UTM) campaign measurement parameters, will be stripped from both URLs.

By default, the Scoby Analytics Privacy Proxy listens to the `/count` endpoint in your SGTM Container. This value can be altered using the "Endpoint" configuration parameter. If your SGTM instance is `https://your-instance.appspot.com`, your Scoby Analytics Privacy Proxy will be listening on `https://your-instance.appspot.com/count`.

Each call to your endpoint needs the `url` and `ref` parameters. The `url` parameter should contain the currently visited URL and `ref` parameter should contain the referring URL. The Scoby Analytics Privacy Proxy will handle the removal of any potential PII from both URLs before sending the page view to Scoby Analytics.

Below is an example of calling the Scoby Analytics Privacy Proxy using an `<img>` tag in a browser.

```javascript
new Image().src = `https://[YOUR_SGTM_INSTANCE_HOSTNAME]/count?url=${encodeURIComponent(document.location)}&ref=${encodeURIComponent(document.referrer)}&_${new Date().getTime()}`
```