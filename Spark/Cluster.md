### Iniciando o cluster

Para iniciar todos os workers bem como o master, basta executar:

`./spark/sbin/start-all.sh`

### Derrubando o cluster

Para derrubar todo o cluster, certifique-se que o job está finalizado (ou encerre-o), e então basta executar:

`./spark/sbin/stop-all.sh`

### Startando o master

`./spark/sbin/start-master.sh`

### Derrubando o master

`./spark/sbin/stop-master.sh`

### Startando os slaves

`./spark/sbin/start-slave.sh`

Para subir um slave específico, execute o script `./spark/sbin/start-slave.sh` do nó que você quer subir.

### Derrubando os slaves

`./spark/sbin/stop-slaves.sh`

Para derrubar um slave específico, execute o script `./spark/sbin/stop-slave.sh` do nó que você quer derrubar.
