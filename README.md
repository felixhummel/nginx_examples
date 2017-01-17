# Nginx Example Configs

This defines a [default_server](http://nginx.org/en/docs/http/server_names.html)
that serves [Let's Encrypt](https://letsencrypt.org/)'s `/.well-known` on `:80`
and redirects `:80` to `:443` otherwise.

New services listen on `:443`. See `conf.d/foo.example.org.conf` for an example.

If a service should listen on both `:80` and `:443` then it must include
`listen_ssl.conf` for certificate renewal to work. See
`conf.d/ip.example.org.conf`.

Certificates are expected at `/etc/letsencrypt/live/<server_name>/`. You may
use [Felix' certbot container](https://hub.docker.com/r/felix/certbot/) or
the official [Certbot](https://certbot.eff.org/) client.

SSL config params are stored in `ssl.conf`.

A few sane proxy defaults live in `proxy.conf`.

Note: Nginx variables [should not be used for templating](http://nginx.org/en/docs/faq/variables_in_config.html).
Use [Salt](https://docs.saltstack.com/en/latest/) or another configuration
management tool of your choice.
