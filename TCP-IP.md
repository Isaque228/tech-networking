# TCP/IP

TCP/IP é o conjunto de protocolos que efetivamente faz a internet e a maioria das redes corporativas funcionarem. Diferente do modelo OSI, que é teórico, o TCP/IP é um modelo prático e implementado, organizado em 4 camadas (Aplicação, Transporte, Internet e Enlace/Acesso à Rede). Entender essa pilha é essencial porque é sobre ela que todo o restante da comunicação de dados se apoia.

## Conceitos principais
- Camada de Aplicação - concentra os protocolos usados diretamente pelos programas, como HTTP, DNS, SMTP e FTP, correspondendo às camadas 5-7 do OSI.
- Camada de Transporte - responsável pela entrega de dados entre processos, com TCP (confiável, orientado a conexão) e UDP (rápido, sem garantias).
- Camada de Internet (ou Rede) - trata do endereçamento IP e do roteamento de pacotes entre redes distintas.
- Camada de Acesso à Rede (Enlace) - lida com a entrega física dos dados dentro de uma mesma rede local, incluindo endereços MAC.
- Three-way handshake - processo de abertura de conexão TCP com os pacotes SYN, SYN-ACK e ACK.
- Números de porta - identificam o processo/serviço de destino dentro de um host (ex: 80 para HTTP, 443 para HTTPS, 53 para DNS).
- Sockets - a combinação de endereço IP + porta + protocolo que identifica uma conexão de forma única.
- Fragmentação e MTU - divisão de pacotes grandes para caber no tamanho máximo de transmissão de um enlace.

## Na prática
- `ss -tuln` ou `netstat -tuln` mostram portas e conexões TCP/UDP abertas em um host Linux.
- `curl -v` expõe as fases da conexão TCP/TLS e da requisição HTTP, útil para depurar falhas de aplicação.
- Servidores web escutam em portas conhecidas (80/443), enquanto aplicações client-server customizadas costumam usar portas efêmeras/altas dinamicamente.
- Firewalls e balanceadores de carga operam fortemente sobre a camada de transporte, filtrando ou distribuindo tráfego por IP:porta.

## Pontos de atenção
- TCP garante entrega e ordem, mas isso tem custo de latência (handshake, retransmissões); para tráfego sensível a atraso, como VoIP e streaming, UDP costuma ser preferido.
- Portas abaixo de 1024 exigem privilégios administrativos em sistemas Unix-like, o que impacta o design de serviços que precisam rodar sem root.
- Confundir a camada de "Internet" do TCP/IP com a "internet pública" é um erro comum: a camada de Internet existe também em redes internas isoladas.
- Problemas de MTU mal configurado (ex: em túneis VPN) causam perda silenciosa de pacotes grandes, sendo uma causa clássica e difícil de diagnosticar de lentidão intermitente.
