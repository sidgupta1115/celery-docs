# Celey: Asynchronous backend tasks for Flask

As a part of a team developing a SaaS E-commerce/Travel Recommender System, I developed the backend infrastructure for data pipelines to function asynchronously. These documents show the setup of this framework that are specfic to our project but should be useful to anyone trying to understand the framework for setting up asynchronous tasks with Flask.

This repositiory has a notebook that shows the setup of Celery with the Flask web framework. The notebook shows know how to configure celery with rabbitmq as a messaging queue to perform asynchronous tasks from Flask, configure Supervisor to monitor Celery as a backend daemon, and troubleshoot bugs. 

This document references example files that use pseudocode and will not function as is. I have also attached the actual project files to be used as reference

This document does not go into the full configuration of Flask but I will provided resources as necessary
Configuring Flask on EC2 Ubuntu 14.04 Server: https://www.datasciencebytes.com/bytes/2015/02/24/running-a-flask-app-on-aws-ec2/


## The 4 Components to the  Celery framework:
1. **Flask**: client application. This is where Celery is triggered to run an asychronous task. **simple_flask_example.py** shows a basic implementation of flask with the pseudocode to build a model
2. **Message Queue**: rabbitmq broker. This is the environment where celery "workers" perform the task. It can be configured such that rabbitmq runs the tasks on a separate server but in our example we run rabbitmq from the same ec2 environment
3. **Celery**: framework for asynchronous tasks. Celery need to be configuered to run with Flask. The file **celery_config.py** holds the configuration information
4. **Supervisor**: Process monitor/controller. This how we run Celery as a daemon backend process and monitior/troubleshoot Celery's performance or bugs.
