Tencent Cloud DNS (DNSPod) module for Caddy
===========================

This package contains a DNS provider module for [Caddy](https://github.com/caddyserver/caddy). It can be used to manage DNS records with Tencent Cloud (as is <https://www.tencentcloud.com> or <https://cloud.tencent.com>) accounts.

## Caddy module name

```
dns.providers.tencentcloud
```

## Config examples

To use this module for the ACME DNS challenge, [configure the ACME issuer in your Caddy JSON](https://caddyserver.com/docs/json/apps/tls/automation/policies/issuer/acme/) like so:

```json
{
  "module": "acme",
  "challenges": {
    "dns": {
      "provider": {
        "name": "tencentcloud",
        "secret_id":  "TENCENTCLOUD_SECRET_ID",
        "secret_key": "TENCENTCLOUD_SECRET_KEY"
      }
    }
  }
}
```

or with the Caddyfile:

```
# globally

acme_dns tencentcloud {
  secret_id {env.TENCENTCLOUD_SECRET_ID}
  SecretKey {env.TENCENTCLOUD_SECRET_KEY}
}
```

```
# one site

tls {
  dns tencentcloud {
    secret_id {env.TENCENTCLOUD_SECRET_ID}
    secret_key {env.TENCENTCLOUD_SECRET_KEY}
  }
}
```

You can replace `{env.TENCENTCLOUD_SECRET_ID}`,`{env.TENCENTCLOUD_SECRET_KEY}` with the actual auth token in the `""` if you prefer to put it directly in your config instead of an environment variable.

## Authenticating

See [the associated README in the libdns package](https://github.com/libdns/tencentcloud) for important information about credentials.
