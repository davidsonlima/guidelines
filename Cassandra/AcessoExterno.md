### Habilitando acesso externo & Thrift

Para habilitar acesso externo editamos a seguinte configuração no `conf/cassandra.yaml`.

```
start_rpc: true
listen_address:
rpc_address: 0.0.0.0
broadcast_rpc_address: <ip>
```
