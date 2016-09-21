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

or, if you've got a newer rsync installed...
(rsync version 3.1.0 introduced the --chown --usermap and --groupmap options)

```
rsync -azvog --chown=www-data:www-data _site/* root@${WEBSRV}:/usr/share/nginx/www/
```

### New, for S3!

```
cd ~/src/jschmidt3786/kc9wsj.us/_site/ ; \
s3put --debug 1 --region us-west-2 --bucket wwwkc9wsjus --grant public-read --prefix $(pwd)/ *
```

