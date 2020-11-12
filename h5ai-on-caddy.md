# h5ai with Caddy 2

From [here](https://github.com/caddyserver/caddy/issues/819#issuecomment-725867359)

```
handle {
    php_fastcgi unix//run/php/php7.4-fpm.sock
    file_server {
        browse
    }
    @no_index {
        not file {
            try_files {path}.html {path} {path}/index.html
        }
    }
    rewrite @no_index /_h5ai/public/index.php
}
```
