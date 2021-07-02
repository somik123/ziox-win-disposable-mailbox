# ziox-win-disposable-mailbox
Disposable Emails based on catchall service

Just upload to your public_html directory and ensure php-imap is enabled.

config.php is located in "backend-libs" directory.

Required nginx configuration for the webserver for secure operations:
```
	location ~ "/backend-libs" {
		deny all;
		return 403;
	}
	location ~ "/(index\.php|json\-api\.php)(/|$)"{
		include snippets/fastcgi-php.conf;
		# With php-fpm (or other unix sockets):
		# fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
		# With php-cgi (or other tcp sockets):
		fastcgi_pass 127.0.0.1:9000;
	}
	location ~ \.php(/|$) {
		deny all;
		return 403;
	}

```

