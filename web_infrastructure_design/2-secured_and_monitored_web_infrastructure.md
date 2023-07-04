# 2. Secured and monitored web infrastructure

## Table of contents

  * [Secured and monitored wen infrastructure](#secured-and-monitored-web-infrastructure)
      * [Specifics about this infrastructure](#specifics-about-this-infrastructure)
      * [Issues about this infrastructure](#issues-about-this-infrastructure)
  * [Bibliography](#bibliography)
  * [Tools](#tools)

## Secured and monitored web infrastructure

The following is three server web infrastructure that hosts the website `www.foobar.com`, it must be secured, serve encrypted traffic, and be monitored

<div align="center">
  <a href="https://holbertonschool.uy/">
    <img src="2-secured_and_monitored_web_infrastructure.jpg" alt="secured_web_infrastructure">
  </a>
</div>

### Specifics about this infrastructure

- For every additional element, why you are adding it
- What are firewalls for
- Why is the traffic served over HTTPS
- What monitoring is used for
- How the monitoring tool is collecting data
- Explain what to do if you want to monitor your web server QPS

### Issues about this infrastructure


- Why terminating SSL at the load balancer level is an issue
- Why having only one MySQL server capable of accepting writes is an issue
- Why having servers with all the same components (database, web server and application server) might be a problem

## Bibliography:

- https://cyberhoot.com/cybrary/secure-socket-layer-ssl/
- https://www.netreo.com/blog/network-and-infrastructure-monitoring-is-every-tool-the-same/
- https://levelup.gitconnected.com/system-design-interview-basics-difference-between-api-gateway-and-load-balancer-60260b568121
- https://oa-angel26.medium.com/web-infrastructure-design-4634a2e1b27c

## Tools:
- https://app.diagrams.net/
