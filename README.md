docker-glassfish-showcase
=========================

Docker image to run the Primefaces showcase on a Glassfish 4.1 application server.

Usage
-----

To create the image `glassfish-showcase`, execute the following command on the docker-glassfish folder:

	docker build -t koert/glassfish-showcase .

To run the image and bind to port :

	docker run -d -p 8080:8080 koert/glassfish-showcase
	
You can access the showcase application with: http://localhost:8080/showcase

More options:
	docker run -d -p 4848:4848 -p 8080:8080 -p 9009:9009 \
	  -v ~/tmp/glassfish/logs:/opt/glassfish4/glassfish/domains/domain1/logs \
	  -e DEBUG="true" -e GLASSFISH_PASS="mypass" koert/glassfish-showcase

Ports: 
- 4848: Glassfish administration console
- 8080: HTTP listener
- 8181: HTTPS listener
- 9009: JPDA debug

Mount points:
- /opt/glassfish4/glassfish/domains/domain1/logs: log files

Environment:
- DEBUG: true/false for debugging on port 9009
- GLASSFISH_PASS: admin password for console on port 4848

To run manually:
docker run --rm -it -p 8080:8080 -p 4848:4848 koert/glassfish-showcase /bin/bash
# /opt/app/bin/start-glassfish.sh


