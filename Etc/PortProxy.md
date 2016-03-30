### Listar redirects

`netsh interface portproxy show all`

### Adicionar port redirect

`netsh interface portproxy add v4tov4 listenport=3340 listenaddress=10.1.1.110 connectport=3389 connectaddress=10.1.1.110`

### Remover port redirect

`netsh interface portproxy delete v4tov4 listenport=3340 listenaddress=10.1.1.110`
