# D-mart
  
A Simple Shopping website created using Django as the backend and celry as the distributed task queue and the RabbitMq as the Message broker. I have tried to build up a paypal integration as well.

### Quick setup 

Firstly you will need [RabbitMq](https://www.rabbitmq.com/download.html) and [flower](http://flower.readthedocs.io/en/latest/install.html) installed.

The Database choice is left for the users to decide. Choose one of your choice and start experimenting.

Also install rabbit using the command :-
    
    $ sudo apt install rabbit 

Configure your rabbitmqctl username and password as : 
    
    ~$ rabbitmqctl add_user myusername mypassword
    ~$ rabbitmqctl add_vhost myvhost
    ~$ rabbitmqctl set_user_tags myusername myusername_tag
    ~$ rabbitmqctl set_permissions -p myvhost myvhost ".*" ".*" ".*"

Check if any instance is running by command :
    
    ~# rabbitmqctl status
If any instance is found running then stop it using:

    ~# rabbitmqctl stop
and restart using : 
     
     ~# rabbitmq-server


accordingly change the credentials in the settings.py file as... 

     '''
     
     BROKER_URL = "amqp://myusernmae:mypassword@localhost:5672/myvhost/"
     
     '''
start celery and flower(to view running tasks) by the command:
     
     ~$ celery -A myshop celery.py flower
     
finally start the django server by:
     
     -$ python manage.py runserver



