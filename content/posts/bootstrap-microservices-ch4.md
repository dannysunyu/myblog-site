+++
title = 'Bootstrap Microservices Ch4'
date = 2025-07-09T17:21:01+07:00
draft = false
+++

Testing an internal microservice from the outside is normally
only possible in development. Once we move this microservice to production, its
REST API is only available within the Kubernetes cluster. In this case, we’ll make it private because we don’t want the outside world having direct access to our video storage.
This is a security feature of microservices! We can control which microservices are
exposed to the outside world, and we can use that to restrict access to parts of the
application that should not be directly accessible by outsiders. 
