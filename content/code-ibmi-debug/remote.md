To ensure the Debug Service runs securely, certificates need to be created for the service and the clients. This will allow clients to connect to the service securely in the future.

Certificates get created in `/QIBM/ProdData/IBMiDebugService/bin/certs`. The two important files that get created at:

* `debug_service.pfx` is used to start up the service on the server.
* `debug_service.crt` which is used as a client certifcate. This can be downloaded and imported later.