# Protocolos de Rede

Protocolos de rede são conjuntos de regras que definem como os dados são formatados, transmitidos e interpretados entre dispositivos. Conhecer os principais protocolos e para que servem é a base para entender qualquer troubleshooting, arquitetura de sistemas distribuídos ou configuração de infraestrutura.

## Conceitos principais
- HTTP/HTTPS - protocolo de aplicação para transferência de hipertexto; HTTPS adiciona criptografia via TLS.
- DNS (porta 53) - traduz nomes de domínio em endereços IP.
- SSH (porta 22) - acesso remoto seguro a shells e túneis criptografados.
- FTP/SFTP (portas 21/22) - transferência de arquivos; FTP é em texto claro, SFTP roda sobre SSH.
- SMTP/IMAP/POP3 (portas 25/143/110) - envio e recebimento de e-mails.
- ICMP - usado para diagnóstico e controle, base do `ping` e de mensagens de erro como "destino inacessível".
- ARP - resolve endereços IP para endereços MAC dentro de uma rede local.
- NTP (porta 123) - sincronização de horário entre dispositivos, crítico para logs e autenticação.
- SNMP (porta 161) - monitoramento e gerenciamento de dispositivos de rede.

## Na prática
- Analisar o protocolo correto para cada porta com `nmap -sV <host>` ajuda a identificar serviços expostos em um servidor.
- Capturas com Wireshark ou `tcpdump` permitem ver exatamente qual protocolo está trafegando em uma determinada porta ou interface.
- APIs modernas usam majoritariamente HTTP/HTTPS com JSON, mas protocolos binários como gRPC (sobre HTTP/2) são comuns em comunicação entre microsserviços.
- Certificados de autoridades como Let's Encrypt tornaram o HTTPS padrão até para sites simples, tornando HTTP puro cada vez mais raro em produção.

## Pontos de atenção
- Nunca expor serviços como FTP, Telnet ou SNMP v1/v2 sem criptografia em redes não confiáveis, pois trafegam credenciais em texto claro.
- Confundir a porta padrão de um protocolo com o protocolo em si é um erro: um serviço pode escutar em qualquer porta, a porta padrão é só uma convenção.
- ICMP costuma ser bloqueado por firewalls por padrão, o que faz o `ping` falhar mesmo quando o host está acessível por outros protocolos.
- Ao trocar protocolos legados (FTP, HTTP) pelos seus equivalentes seguros (SFTP, HTTPS), revisar também a aplicação cliente, pois nem sempre a migração é transparente.
