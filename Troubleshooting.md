# Troubleshooting de Redes

Troubleshooting de redes é o processo estruturado de identificar, isolar e resolver problemas de conectividade e desempenho. Ter um método claro, geralmente inspirado no modelo OSI, evita perda de tempo com tentativas aleatórias e ajuda a chegar à causa raiz de forma mais rápida e confiável.

## Conceitos principais
- Abordagem em camadas - investigar de baixo para cima (física, enlace, rede, transporte, aplicação) para isolar em qual nível está a falha.
- Isolamento de escopo - determinar se o problema afeta um único host, uma sub-rede, um site inteiro ou é externo (ex: provedor de internet).
- Linha de base (baseline) - conhecer o comportamento normal da rede (latência, throughput) é essencial para identificar o que é realmente anômalo.
- Ponto único de falha (SPOF) - identificar componentes críticos sem redundância que, se falharem, derrubam toda uma parte da rede.
- Latência vs perda de pacotes - problemas diferentes com sintomas parecidos, mas causas e correções distintas.
- Captura de pacotes - análise detalhada do tráfego real trafegando na rede para confirmar hipóteses sobre a causa do problema.
- Divisão e conquista (divide and conquer) - testar em pontos intermediários do caminho de rede para restringir onde o problema realmente está.
- Documentação e histórico - registrar mudanças recentes na rede é frequentemente o primeiro lugar a checar, já que boa parte dos incidentes segue uma mudança.

## Na prática
- `ping` testa conectividade básica e mede latência/perda de pacotes até um destino.
- `traceroute`/`mtr` mostram o caminho e a latência em cada salto, ajudando a identificar em qual ponto da rede o problema ocorre.
- `tcpdump`/Wireshark capturam tráfego real para confirmar se pacotes estão saindo, chegando ou sendo descartados, e em qual protocolo.
- `dig`/`nslookup` isolam problemas de resolução de nomes antes de assumir que é um problema de conectividade de rede.
- `mtr` combina ping e traceroute continuamente, sendo muito útil para identificar perda de pacotes intermitente em um salto específico.

## Pontos de atenção
- Corrigir o sintoma sem entender a causa raiz (por exemplo, reiniciar um serviço repetidamente) tende a fazer o problema reaparecer.
- Assumir que "a rede está lenta" sem medir de fato é um erro comum; sempre buscar dados concretos (latência, perda, throughput) antes de agir.
- Ignorar mudanças recentes na infraestrutura (deploys, atualizações de firmware, alterações de firewall) atrasa o diagnóstico, já que boa parte dos incidentes tem uma causa recente identificável.
- ICMP bloqueado por firewalls pode fazer `ping`/`traceroute` parecerem indicar uma falha que não existe; sempre validar com outro protocolo antes de concluir que um host está inacessível.
