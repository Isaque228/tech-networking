# Switching

Switching é o processo de encaminhar quadros (frames) dentro de uma mesma rede local, usando endereços MAC para decidir por qual porta enviar cada quadro. É a base da comunicação em redes locais (LANs) modernas, tendo substituído hubs por ser muito mais eficiente ao evitar colisões e desperdício de banda.

## Conceitos principais
- Tabela MAC (CAM table) - mapeia endereços MAC aprendidos a portas físicas do switch, construída dinamicamente conforme o tráfego passa.
- Domínio de colisão - em switches, cada porta é seu próprio domínio de colisão, diferente dos hubs onde toda a rede compartilhava um único domínio.
- VLAN (Virtual LAN) - segmentação lógica de uma rede física em múltiplas redes independentes, isolando tráfego e domínios de broadcast.
- Trunk (802.1Q) - link entre switches ou entre switch e roteador que carrega tráfego de múltiplas VLANs simultaneamente, usando tags de identificação.
- Spanning Tree Protocol (STP) - protocolo que evita loops em topologias com links redundantes, bloqueando caminhos duplicados até serem necessários.
- Switch de camada 2 vs camada 3 - switches L2 encaminham por MAC; switches L3 também roteiam entre VLANs usando IP, como um roteador integrado.
- Broadcast, unicast e multicast - tipos de tráfego que um switch trata de formas diferentes (unicast é direcionado, broadcast e multicast são replicados conforme a política).
- Port security - recurso que limita quantos ou quais endereços MAC podem se conectar a uma porta específica, mitigando riscos de segurança.

## Na prática
- Comandos como `show mac address-table` (Cisco) exibem a tabela de aprendizado de MACs de um switch gerenciável.
- VLANs são amplamente usadas para separar tráfego de convidados, voz (VoIP), servidores e usuários dentro da mesma infraestrutura física.
- Data centers usam switches de alta capacidade com recursos como LACP (agregação de links) para aumentar banda e redundância entre switches.
- Ambientes com switches empilháveis (stacking) permitem gerenciar múltiplos equipamentos físicos como se fossem um único switch lógico.

## Pontos de atenção
- Loops físicos acidentais (cabo conectado nas duas pontas do mesmo switch) podem derrubar uma rede inteira rapidamente se o STP estiver desabilitado ou mal configurado.
- Portas configuradas na VLAN errada são uma causa comum e sutil de "dispositivo não consegue acessar a rede", já que a conectividade física existe mas o isolamento lógico impede a comunicação.
- Excesso de broadcast em VLANs muito grandes ("broadcast storm") degrada a performance de toda a rede; segmentar em VLANs menores mitiga esse risco.
- Trocar um switch sem revisar a configuração de trunks e VLANs pode causar indisponibilidade, pois a configuração de portas raramente é replicada automaticamente.
