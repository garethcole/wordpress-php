# wordpress-php

A replacement php image for https://github.com/Wodby/docker4wordpress that modifies the necessary config to support remote debugging with XDEBUG in Sublime Text 3

###Loopback address
Before starting a debugging session it is necessary to open a look back address, because remote xdebugging will not currently work on docker using xdebug.remote_connect_back = 1 (which should allow xdebug to connect back to what ever is calling it).

```sudo ifconfig lo0 alias 10.254.254.254```


###Sublime project settings
```
{
  "folders":
  [
		{
			"path": "/private/var/www/projectname"
		}
	],
    "settings": {
        "xdebug": {
            "path_mapping": {
                    "/var/www/html/public/wordpress/" : "/private/var/www/projectname/public/wordpress/"
            },
             "url": "http://localhost:8000",
            "port": 9999
        }
    }
}
```
