# Web infrastructure design

The following infrastructure designs were discussed and analized:

0. [Simple web stack](/web_infrastructure_design/0-simple_web_stack.md)

A lot of websites are powered by simple web infrastructure, a lot of time it is composed of a single server with a [LAMP stack](https://en.wikipedia.org/wiki/LAMP_%28software_bundle%29).

Design a one server web infrastructure that hosts the website that is reachable via `www.foobar.com`. Start your explanation by having a user wanting to access your website.

__Requirements:__

* You must use:
    * 1 server
    * 1 web server (Nginx)
    * 1 application server
    * 1 application files (your code base)
    * 1 database (MySQL)
    * 1 domain name `foobar.com` configured with a `www` record that points to your server IP `8.8.8.8`

1. [Distributed web infrastructure](/web_infrastructure_design/1-distributed_web_infrastructure.md)

Design a three server web infrastructure that hosts the website www.foobar.com.

__Requirements:__

* You must add:
    * 2 servers
    * 1 web server (Nginx)
    * 1 application server
    * 1 load-balancer (HAproxy)
    * 1 set of application files (your code base)
    * 1 database (MySQL)

2. [Secured and monitored web infrastructure](/web_infrastructure_design/2-secured_and_monitored_web_infrastructure.md)

On a whiteboard, design a three server web infrastructure that hosts the website www.foobar.com, it must be secured, serve encrypted traffic, and be monitored.

__Requirements:__

* You must add:
    * 3 firewalls
    * 1 SSL certificate to serve www.foobar.com over HTTPS
    * 3 monitoring clients (data collector for Sumologic or other monitoring services)

3. [Scale up](/web_infrastructure_design/3-scale_up.md)

Read: [Application server vs web server](https://www.nginx.com/resources/glossary/application-server-vs-web-server/)

* You must add:
    * 1 server
    * 1 load-balancer (HAproxy) configured as cluster with the other one
    * Split components (web server, application server, database) with their own server

## Author

* __Cristian Encalada__ - *Holberton Student* 
    - Github: [Cristian Encalada](https://github.com/cristian-encalada/)