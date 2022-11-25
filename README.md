# dokku-letsencrypt-auto-enable-allow-list

This plugin for Dokku automatically enables Let's encrypt HTTPS for newly created cloned apps and review apps. It only activates if the `DOKKU_LETSENCRYPT_AUTO_ENABLE` environment variable in the app is set to `1` and the app's Let's encrypt certificate no has not yet been deployed.

## Installation

```shell
dokku plugin:install https://github.com/gleniat/dokku-letsencrypt-auto-enable-allow-list.git letsencrypt-auto-enable-allow-list
```

Make sure you have [dokku-letsencrypt](https://github.com/dokku/dokku-letsencrypt) plugin installed and working correctly (i.e., you have set `DOKKU_LETSENCRYPT_EMAIL` per app or globally).

## Usage

1. add `DOKKU_LETSENCRYPT_AUTO_ENABLE` environment variable to your app and set it to 1
```
dokku config:set <yourapp> DOKKU_LETSENCRYPT_AUTO_ENABLE=1
```

2. clone the app with `dokku apps:clone <yourapp> <yourapp>-test` or make a review app with Dokku GitHub action. Let's Encrypt certificate will be obtained automatically.

If your base app in the step 1 doesn't have Let's Encrypt enabled, it will be enabled during a subsequent build or after manual rebuild with `dokku ps:rebuild <yourapp>` command.

## Other variants

1. Activate Let's Encrypt for all new apps, except the apps with `DOKKU_LETSENCRYPT_AUTO_ENABLE` set to `0`. Try https://github.com/gleniat/dokku-letsencrypt-auto-enable

## Requirements

- dokku 0.4.x
