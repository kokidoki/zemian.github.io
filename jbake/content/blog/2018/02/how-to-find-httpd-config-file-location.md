title=How to find httpd config file location
date=2018-02-28
type=post
tags=httpd
status=published
~~~~~~

    Zemians-MacBook-Air:~ zemian$ httpd -t -D DUMP_INCLUDES
    Included configuration files:
      (*) /private/etc/apache2/httpd.conf
        (498) /private/etc/apache2/extra/httpd-mpm.conf
        (504) /private/etc/apache2/extra/httpd-autoindex.conf
        (544) /private/etc/apache2/other/php7.conf
