## Prometheus pushgateway extension for weewx

This weewx extension enables you to send your weather data to a [Prometheus](http://prometheus.io) [pushgateway](https://github.com/prometheus/pushgateway). Additional information regarding Prometheus and its use can be found on the associated web site.

## Requirements

This extension requires the use of the `requests` package.

```
pip install requests
```

## Installation

This extension can be easily installed using the weewx extensions installer.

1. Download the extension from github:
	```
	wget https://github.com/Bert-R/weewx-prometheus/archive/v1.2.0.tar.gz
	```

2. Install using the weewx extension utility
	```
	wee_extension --install v1.2.0.tar.gz
	```

3. Update **weewx.conf** to appropriately tag weather data for submission into the Prometheus pushgateway and subsequent scraping from Prometheus.  Note that **job** and **instance** names may be subject to relabeling depending on your Prometheus environment.
	```
    [StdRESTful]
      [[PromPush]]
         job = PROMETHEUS_JOB_NAME
         instance = PROMETHEUS_INSTANCE_NAME
         host = PUSH_GW_HOST
         port = PUSH_GW_PORT
	```
    `wee_extension` will add a boilerplate `[[PromPush]]` section to your config.  You need to edit it.
	

4. Restart weewx
    ```
    sudo /etc/init.d/weewx stop
    sudo /etc/init.d/weewx start
    ```

## Administravia
**Original author:** Tom Mitchell \<[tom@tom.org](mailto:tom@tom.org)\>
**license:** Apache License, Version 2.0. See LICENSE.  
**Original source:** [https://github.com/tomdotorg/weewx-prometheus](https://github.com/tomdotorg/weewx-prometheus)  
