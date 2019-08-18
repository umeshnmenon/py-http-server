# py-hhtp-server

Py HTTP Server is a minimalistic light weight http server that can be used for micro service based solutions in Python.

### Design

The design supports both single threaded and multi-threaded server. The `server` and `threaded_server` are the main 
classes that start the application server. The `router` class routes the requests and 
`request_handler` handles all the requests and calls specific request handling classes. The mapping to the corresponding
 api request must be done in `router` class by adding the mapping to `self.routes`.

**How to extend to cater specific requests**

Add your specific request handler classes within `request_handlers` folder by extending `GenericRequestHandler` class.

### How to Run

You can simply call the below command:

```bash
python launcher.py &
```

If you want to wrap this in a shell script create a `.sh` file with the following contents:
```bash
#!/bin/sh
set -e

echo "Starting Simple Kafka Monitor..."
# variable to hold the status
rc=1
python launcher.py &
rc=$?
if [ $? -eq 1 ]; then
	echo "Kafka Monitor has some problems while starting. Aborting..."
	exit 1
fi
echo "Done"
```