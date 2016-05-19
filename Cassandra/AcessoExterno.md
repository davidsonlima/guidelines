### Habilitando acesso externo

Para habilitar acesso externo editamos a seguinte configuração no `conf/cassandra.yaml`.

```
start_rpc: true
rpc_address: 0.0.0.0
broadcast_rpc_address: localhost
```
