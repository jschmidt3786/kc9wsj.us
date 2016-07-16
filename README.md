## static blog/point-of-presence site for Jeff KC9WSJ

that's about it.


here's how to deploy:

```bash
#!/bin/bash -ex
WEBSRV="_ipaddr"
BASEDIR=$(pwd) # probably...

rsync -az --progress _site/* root@${WEBSRV}:/usr/share/nginx/www/
ssh root@${WEBSRV} 'chown -R www-data: /usr/share/nginx/www'
```
