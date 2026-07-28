# IPv6

IPv6 é a versão mais recente do protocolo de Internet, criada para resolver o esgotamento de endereços do IPv4. Usa endereços de 128 bits, o que gera um espaço de endereçamento praticamente inesgotável, além de simplificar alguns aspectos de configuração e remover a necessidade estrutural de NAT.

## Conceitos principais
- Endereço de 128 bits - representado em 8 grupos de 4 dígitos hexadecimais separados por dois-pontos (ex: 2001:0db8::1).
- Compactação de zeros - sequências de zeros consecutivos podem ser abreviadas uma única vez com `::` no endereço.
- Tipos de endereço - unicast (um destino), multicast (grupo de destinos) e anycast (o destino mais próximo topologicamente); não existe broadcast no IPv6.
- SLAAC (Stateless Address Autoconfiguration) - permite que um host configure seu próprio endereço IPv6 sem depender de um servidor DHCP.
- Endereços link-local (fe80::/10) - usados apenas para comunicação dentro do mesmo segmento de rede, essenciais para protocolos de vizinhança.
- NDP (Neighbor Discovery Protocol) - substitui o ARP do IPv4, usando mensagens ICMPv6 para descoberta de vizinhos e roteadores.
- Ausência de NAT como necessidade - o espaço de endereços é tão grande que cada dispositivo pode ter um IP público único.
- Dual stack - operação simultânea de IPv4 e IPv6 na mesma interface, estratégia comum durante a transição.

## Na prática
- `ip -6 addr show` lista os endereços IPv6 configurados em um host Linux.
- A maioria dos sistemas operacionais modernos já habilita IPv6 por padrão e prioriza seu uso quando disponível na rede.
- Grandes provedores de conteúdo (Google, Facebook, Netflix) já servem uma parcela relevante do tráfego via IPv6, especialmente para redes móveis.
- Provedores de nuvem oferecem blocos IPv6 gratuitamente ao lado do IPv4, sendo comum configurar dual stack em VPCs modernas.

## Pontos de atenção
- A ausência de NAT tradicional muda o modelo de segurança: firewalls precisam ser configurados explicitamente, já que hosts internos podem ser diretamente endereçáveis.
- Ferramentas antigas de rede e alguns firewalls legados não tratam IPv6 corretamente, criando pontos cegos de segurança se não for configurado com atenção.
- Testar conectividade dupla (IPv4 e IPv6) é importante, pois falhas de rota IPv6 mal configuradas podem causar lentidão sutil (timeout no IPv6 antes de cair para IPv4).
- Notação e cálculo de sub-redes IPv6 seguem lógica diferente do IPv4 (tipicamente /64 para redes locais), não sendo uma simples extensão das regras de IPv4.
