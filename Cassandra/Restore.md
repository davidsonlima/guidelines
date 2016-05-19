### Carregando dados de um snapshot de outro Cassandra

https://docs.datastax.com/en/cassandra/2.1/cassandra/operations/ops_backup_snapshot_restore_t.html

Outra opção é usar o script `cassandraloader.py tabela`, quando as tabelas não forem muito grande, pois o `sstableloader` fica agarrado se forem grandes.
