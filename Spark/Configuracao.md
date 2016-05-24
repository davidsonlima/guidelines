### Configurando o master

conf/spark-env.sh
```
# Essas opções irão fazer com que ocorra um clean up do dir /work dos slaves
export SPARK_WORKER_OPTS="-Dspark.worker.cleanup.enabled=true -Dspark.worker.cleanup.interval=1800 -Dspark.worker.cleanup.appDataTtl=604800"
```

#### Apontando os slaves

Adicionar cada DNS público dos workers (slaves) no arquivo `conf/slaves`

### Executando o job

Ao executar o comando `spark-submit`, utilize a opção `--supervise` para que o driver seja supervisionado e seja reiniciado em caso da execução ser abortadas inesperadamente.
