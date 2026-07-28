# Routing (Roteamento)

Roteamento é o processo de encaminhar pacotes de dados entre redes diferentes até que cheguem ao seu destino final. É a função central de um roteador e a base que permite que redes isoladas (como a rede de uma empresa e a internet) se comuniquem entre si através de múltiplos saltos.

## Conceitos principais
- Tabela de roteamento - estrutura que armazena, para cada destino conhecido, qual é o próximo salto (next hop) e por qual interface enviar o pacote.
- Rota padrão (default gateway) - a rota usada quando nenhuma entrada mais específica na tabela corresponde ao destino.
- Roteamento estático - rotas configuradas manualmente pelo administrador, previsíveis mas sem adaptação automática a falhas.
- Roteamento dinâmico - rotas aprendidas automaticamente através de protocolos como OSPF, BGP ou EIGRP, que se adaptam a mudanças na topologia.
- Métrica - valor numérico usado para escolher entre múltiplas rotas possíveis para o mesmo destino (menor custo geralmente vence).
- Roteamento entre VLANs (inter-VLAN routing) - necessário para que dispositivos em VLANs diferentes se comuniquem, feito por um roteador ou switch de camada 3.
- BGP (Border Gateway Protocol) - protocolo que sustenta o roteamento entre provedores e organizações na internet global.
- TTL (Time to Live) - contador que limita quantos saltos um pacote pode dar antes de ser descartado, evitando loops infinitos.

## Na prática
- `ip route` (Linux) ou `route print` (Windows) exibem a tabela de roteamento local de um host.
- `traceroute`/`tracert` mostra o caminho (saltos) que os pacotes percorrem até um destino, útil para identificar onde a latência ou perda de pacotes ocorre.
- Redes corporativas normalmente usam roteamento estático para links simples e protocolos dinâmicos como OSPF em ambientes com múltiplos roteadores redundantes.
- Provedores de nuvem oferecem tabelas de rotas configuráveis em VPCs, permitindo direcionar tráfego para gateways de internet, VPNs ou peering entre redes.

## Pontos de atenção
- Uma rota padrão mal configurada ou ausente é uma das causas mais comuns de "sem acesso à internet, mas rede local funcionando".
- Rotas estáticas não se ajustam automaticamente a falhas de link, exigindo intervenção manual, o que pode causar indisponibilidades prolongadas se não houver monitoramento.
- Loops de roteamento (routing loops) podem ocorrer quando rotas mal configuradas se referenciam mutuamente; o TTL evita que isso trave a rede indefinidamente, mas o problema de fundo continua.
- Rotas mais específicas (máscara maior) sempre têm prioridade sobre rotas mais genéricas na tabela, algo que gera confusão ao depurar por que um pacote seguiu um caminho inesperado.
