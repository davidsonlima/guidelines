### Configurando


Para o Elasticsearch não ficar perdendo mensagens em um bulk load, não deixe de configurar:

```
threadpool:
    bulk:
        type: cached
        size: 8
        queue_size: 150
```

Obs.: `size` diz respeito a quantidade de cores da máquina.
