### Bloqueando saída na porta 80 UDP 
`iptables -A OUTPUT -p udp -m udp --dport 80 -j REJECT`
