# Logging

## Enable logging

You need to go into the nginx config file and enable logging. An example log will be shown below. You need to add the log format to the http { } lines.

!!!default_file_conf

    /etc/nginx/nginx.conf

Example:

```bash
http {
    log_format main '$remote_addr - $remote_user [$time_local] "$request" '
                    '$status $body_bytes_sent "$http_referer" '
                    '"$http_user_agent" "$http_x_forwarded_for"';
}
```

Now in the configuration file with your site you need to add a line:

```bash
access_log /path/nameLog.log main;
```