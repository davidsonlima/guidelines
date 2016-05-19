### Habilitando acesso externo

Para habilitar acesso externo editamos a seguinte configuração no `apache-cassandra-2.2.3/conf/cassandra.yaml`.

```
start_rpc: true
rpc_address: 0.0.0.0
broadcast_rpc_address: localhost
```
