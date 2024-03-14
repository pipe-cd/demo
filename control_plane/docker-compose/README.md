# Installing a Control Plane locally by docker-compose

This demo shows how to easily install a Control Plane on local by docker-compose.

> Note: See the doc [Install Control Plane](https://pipecd.dev/docs/installation/install-control-plane/) for production-ready installation.


## Installation
1. Change the image versions in [docker-compose.yaml](docker-compose.yaml) if you want.

2. Run a Control Plane by this command:
```sh
docker-compose up
```

After executing the above command, you will see logs like below if success.

```log
pipecd-server-1   | successfully loaded control-plane configuration
pipecd-server-1   | successfully connected to file store
pipecd-server-1   | successfully connected to data store
pipecd-server-1   | grpc server will be run without tls
pipecd-server-1   | grpc server will be run without tls
pipecd-server-1   | grpc server is running on [::]:9080
pipecd-server-1   | grpc server is running on [::]:9083
pipecd-server-1   | grpc server will be run without tls
pipecd-server-1   | admin server is running on 9085
pipecd-server-1   | grpc server is running on [::]:9081
pipecd-server-1   | start running http server on :9082
```

## Confirmation

1. Access the PipeCD's console running on http://localhost:8080.
2. Enter a value as below and `CONTINUE`.
   - `Project Name`: `control-plane-local`

3. Enter values as below and `LOGIN`.
   - `Username`: `hello-pipecd`
   - `Password`: `hello-pipecd`

4. You will see the applications page. Success!

## Clean up

To clean up the Control Plane, execute this command:

```sh
docker-compose down
```

Tips: By following commands instead of above `docker-compose down`, you can keep data such as Pipeds or applications on the Control Plane even after restarting/updating the server component.

```sh
# Restart only the server component.
docker-compose rm -fsv pipecd-server
docker-compose up pipecd-server
```

## Acknowledgements

This demo is based on [@kevin-namba](https://github.com/kevin-namba)'s great work [[Add docker compose deployment PR#4139]](https://github.com/pipe-cd/pipecd/pull/4139).
