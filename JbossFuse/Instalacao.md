###Instalação###

Utilizamos a versão 6.2.1

URL: xxxx

####Procedimentos####

```
tar xvzf ...
```

####Configurando usuário admin####

É preciso "descomentar" a última linha do arquivo <pasta do jboss>/etc/users:

```
admin=admin,admin,manager,viewer,Monitor, Operator, Maintainer, Deployer, Auditor, Administrator, SuperUser
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


####Acessando o Hawtio####

Para acessar o hawtio basta acessar http://localhost:8181
