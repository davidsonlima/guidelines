###Instalação



###New node

Para adicionar um novo nó, deve-se manter o mesmo `cluster.name`, apontar o mesmo `number_of_replicas` e `number_of_shards`.

Caso não seja usado multicast para descobrir o cluster, aponte os ips dos possíveis nó master na configuração `discovery.zen.ping.unicast.hosts`.
