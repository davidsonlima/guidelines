###Instalação###

Utilizamos a versão 6.2

URL: xxxx

####Procedimentos####

```
tar xvzf ...
```

####Iniciando o Jboss Fuse####

```
./bin/fuse
```

####Comandos iniciais####

Primeiro é necessário criar uma fábrica:

```
fabric:create --wait-for-provisioning
```

Depois precisamos criar um container child:

```
container-create-child root child
```

Startando o container:

```
container-connect child
```

####Instalando como serviço####

Adicione a feature wrapper e utilize o seguinte comando:

```
wrapper:install -d jbossfuse -n jbossfuse
```

Será exibido na tela os comandos para ativar o serviço na máquina.
