# Modelo OSI

O Modelo OSI (Open Systems Interconnection) é um modelo de referência conceitual criado pela ISO que divide a comunicação de rede em 7 camadas, cada uma com uma responsabilidade específica. Ele importa porque fornece uma linguagem comum para descrever, comparar e depurar protocolos e tecnologias de rede, independente do fabricante ou implementação.

## Conceitos principais
- Camada 1 (Física) - transmissão de bits em meios físicos como cabos de cobre, fibra óptica e sinais de rádio.
- Camada 2 (Enlace/Data Link) - endereçamento MAC, switches, quadros (frames) e controle de acesso ao meio.
- Camada 3 (Rede) - endereçamento lógico (IP), roteamento entre redes diferentes, pacotes.
- Camada 4 (Transporte) - entrega de dados ponta a ponta, controle de fluxo e confiabilidade (TCP e UDP).
- Camada 5 (Sessão) - estabelecimento, gerenciamento e encerramento de sessões de comunicação.
- Camada 6 (Apresentação) - formatação, criptografia e compressão de dados (ex: SSL/TLS, codificação de caracteres).
- Camada 7 (Aplicação) - interface com o usuário final e aplicações, onde vivem HTTP, FTP, SMTP, DNS.
- Encapsulamento - cada camada adiciona seu próprio cabeçalho (header) aos dados da camada superior ao descer na pilha.
- PDU (Protocol Data Unit) - nome dado à unidade de dados em cada camada (bit, frame, pacote, segmento).

## Na prática
- Ferramentas de diagnóstico costumam ser mapeadas por camada: `ping` e `traceroute` atuam na camada 3, `arp` na camada 2, `netstat`/`ss` na camada 4, e ferramentas como `curl` na camada 7.
- Ao analisar um problema de rede, seguir o modelo OSI de baixo para cima (ou de cima para baixo) ajuda a isolar em qual camada está a falha, por exemplo: cabo desconectado (camada 1) vs DNS não resolvendo (camada 7).
- Analisadores de pacotes como o Wireshark exibem explicitamente em qual camada cada campo do pacote capturado se encontra.
- Equipamentos de rede são frequentemente classificados pela camada em que operam: hubs (camada 1), switches (camada 2), roteadores (camada 3), firewalls de aplicação (camada 7).

## Pontos de atenção
- O modelo OSI é teórico; a pilha TCP/IP usada na prática comprime essas 7 camadas em 4 ou 5, o que gera confusão ao comparar os dois modelos.
- Não confundir a camada 3 (endereço IP/lógico) com a camada 2 (endereço MAC/físico) ao investigar problemas de conectividade.
- Ferramentas e certificações usam o modelo OSI para fins didáticos, mas produtos reais nem sempre respeitam limites rígidos entre camadas (ex: NAT mistura camadas 3 e 4).
- Memorizar a ordem das camadas (Física, Enlace, Rede, Transporte, Sessão, Apresentação, Aplicação) é útil, mas entender a função de cada uma é mais importante que decorar o nome.
