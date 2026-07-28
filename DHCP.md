# DHCP

DHCP (Dynamic Host Configuration Protocol) é o protocolo responsável por atribuir automaticamente configurações de rede, como endereço IP, máscara de sub-rede, gateway e servidores DNS, aos dispositivos que entram em uma rede. Sem ele, cada host precisaria ser configurado manualmente, o que seria inviável em redes de qualquer tamanho relevante.

## Conceitos principais
- Processo DORA - sequência de mensagens Discover, Offer, Request e Acknowledge que caracteriza a negociação entre cliente e servidor DHCP.
- Escopo (scope/pool) - a faixa de endereços IP que o servidor DHCP está autorizado a distribuir aos clientes.
- Lease (concessão) - o tempo pelo qual um endereço IP é atribuído a um cliente antes de precisar ser renovado.
- Reserva (DHCP reservation) - associação fixa entre um endereço MAC e um IP específico, garantindo que um dispositivo sempre receba o mesmo endereço.
- Relay DHCP (DHCP relay agent) - mecanismo que permite que requisições DHCP atravessem roteadores para alcançar um servidor em outra sub-rede.
- Opções DHCP - parâmetros adicionais entregues junto ao IP, como gateway padrão (option 3), servidores DNS (option 6) e domínio.
- APIPA/Link-Local - endereço automático (169.254.x.x) que um host atribui a si mesmo quando não consegue contatar um servidor DHCP.
- Conflito de IP - situação em que dois dispositivos recebem ou configuram o mesmo endereço, geralmente causada por escopos mal dimensionados ou IPs estáticos sobrepostos.

## Na prática
- Roteadores domésticos e switches corporativos costumam ter um servidor DHCP embutido, mas ambientes maiores centralizam isso em servidores dedicados (Windows Server, ISC DHCP, dnsmasq).
- `ipconfig /release` e `ipconfig /renew` (Windows) ou `dhclient` (Linux) permitem forçar a liberação e renovação manual de uma concessão DHCP.
- É comum reservar IPs fixos via DHCP para impressoras, servidores e equipamentos de infraestrutura, evitando configuração estática manual em cada dispositivo enquanto mantém o IP previsível.
- Em redes com múltiplas sub-redes, um único servidor DHCP central atende todas elas através de relay agents configurados nos roteadores de cada segmento.

## Pontos de atenção
- Dois servidores DHCP ativos na mesma rede sem coordenação causam conflitos de IP e comportamento imprevisível nos clientes.
- Um escopo DHCP mal dimensionado (muito pequeno para o número de dispositivos) causa esgotamento de endereços e falhas de conectividade em horários de pico.
- Tempo de lease muito curto gera tráfego de renovação excessivo; muito longo dificulta a reutilização rápida de endereços quando dispositivos saem da rede.
- Ao migrar ou trocar o servidor DHCP, é importante garantir que reservas e escopos sejam replicados, para não gerar mudanças inesperadas de IP em equipamentos críticos.
