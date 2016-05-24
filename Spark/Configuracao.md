### Configurando o master

conf/spark-env.sh
```
export SPARK_WORKER_OPTS="-Dspark.worker.cleanup.enabled=true -Dspark.worker.cleanup.interval=1800 -Dspark.worker.cleanup.appDataTtl=604800"
```

Adicionar cada DNS público dos workers (slaves) no arquivo `conf/slaves`
