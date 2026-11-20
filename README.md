# ISPConfig3 - Nginx Reverse Proxy

This plugin allows you to run Nginx in front of Apache2 as a reverse proxy on servers managed through the ISPConfig3 Control Panel.

This is fork of https://github.com/Rackster/ispconfig3-nginx-reverse-proxy

# Added features

- local customization in nginx config
- added letsencrypt support

## How it works

In general, it just creates the Nginx vhost files for your sites.

Afterwards, all requests to port 80 or 443 (default http(s) ports) are fetched by Nginx rather than Apache2 and passed to the Apache2 backend - with Nginx's built-in *proxy_pass* feature.

## How to install

### CentOS

1. Change your listen address for httpd server in /etc/httpd/conf/httpd.conf

	```
	Listen 127.0.0.1:82
	```

2. Copy nginx extra config files

	```
	cp etc/nginx/conf.d/proxy.conf /etc/nginx/conf.d/
	cp etc/nginx/conf.d/upstreams.conf /etc/nginx/conf.d/
	```

3. Copy ispconfig host config files

	```
	cp usr/local/ispconfig/server/conf-custom/nginx_reverse_proxy_plugin.vhost.conf.master /usr/local/ispconfig/server/conf-custom/
	cp usr/local/ispconfig/server/conf-custom/vhost.conf.master /usr/local/ispconfig/server/conf-custom/
	```

4. Copy ispconfig plugin file

	```
	cp usr/local/ispconfig/server/plugins-available/nginx_reverse_proxy_plugin.inc.php /usr/local/ispconfig/server/plugins-available/
	```

5. Enable plugin via symlink

	```
	ln -s /usr/local/ispconfig/server/plugins-available/nginx_reverse_proxy_plugin.inc.php /usr/local/ispconfig/server/plugins-enabled/nginx_reverse_proxy_plugin.inc.php
	```

## Contribution

Feel free to be an active part of the project, either by testing and creating issues or forking and sending pull requests.

## Disclaimer

I am in no way responsible for any damage caused to your system by using the plugin.
Usage at you own risk!

