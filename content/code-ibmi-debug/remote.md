To ensure the Debug Service runs securely, certificates need to be created for the service and the clients. This will allow clients to connect to the service securely.

Certificates get created in `/QIBM/ProdData/IBMiDebugService/bin/certs`. The two import files that get created at:

* `debug_service.pfx` is used to start up the service on the server.
* `debug_service.crt` will be downloaded to the clients (where VS Code is running) later