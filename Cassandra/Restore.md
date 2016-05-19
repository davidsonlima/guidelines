### Copiando o schema de um nó do Cassandra

Para copiar o schema de todo keyspace, basta executar o seguinte:

`cqlsh -e "desc keyspace sotreq;" > schema.txt`

### Carregando schema em um novo Cassandra

`cqlsh -f schema.txt`

### Carregando dados de um snapshot de outro Cassandra

https://docs.datastax.com/en/cassandra/2.1/cassandra/operations/ops_backup_snapshot_restore_t.html

Outra opção é usar o script `cassandraloader.py tabela`, quando as tabelas não forem muito grande, pois o `sstableloader` fica agarrado se forem grandes.

Para realizar o procedimento copiando os arquivos *.db diretamente para o novo Cassandra, primeiro é necessário extrair o schema
