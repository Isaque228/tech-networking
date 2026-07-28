# IPv4

IPv4 (Internet Protocol version 4) é o protocolo de endereçamento lógico mais usado historicamente na internet e em redes locais. Usa endereços de 32 bits, geralmente representados em notação decimal pontuada (ex: 192.168.1.1), e é a base sobre a qual roteamento, subnetting e NAT foram construídos.

## Conceitos principais
- Endereço de 32 bits - dividido em 4 octetos de 8 bits cada, permitindo cerca de 4,3 bilhões de endereços únicos.
- Classes de endereços (A, B, C, D, E) - esquema histórico de divisão de faixas, hoje substituído na prática por CIDR.
- Máscara de sub-rede - define quantos bits do endereço identificam a rede e quantos identificam o host.
- CIDR (Classless Inter-Domain Routing) - notação como /24 que expressa a máscara de forma mais flexível que as classes tradicionais.
- Endereços privados (RFC 1918) - faixas reservadas para uso interno: 10.0.0.0/8, 172.16.0.0/12 e 192.168.0.0/16.
- NAT (Network Address Translation) - técnica que permite múltiplos hosts privados compartilharem um único IP público.
- Endereço de broadcast - último endereço de uma sub-rede, usado para enviar dados a todos os hosts dela.
- Esgotamento de IPv4 - a escassez de endereços públicos disponíveis, principal motivador da adoção de NAT e, no longo prazo, do IPv6.

## Na prática
- `ip addr show` (Linux) ou `ipconfig` (Windows) exibem os endereços IPv4 configurados nas interfaces de um host.
- Roteadores domésticos e corporativos usam NAT para que toda uma rede interna compartilhe um único IP público fornecido pelo provedor.
- Ferramentas como calculadoras de sub-rede online ou `ipcalc` ajudam a planejar faixas de IP e máscaras antes de configurar uma rede.
- Provedores de nuvem (AWS, GCP, Azure) ainda usam IPv4 como padrão em VPCs, geralmente combinando IPs privados internos com IPs públicos elásticos.

## Pontos de atenção
- Confundir máscara de sub-rede com endereço de rede é um erro comum ao configurar interfaces manualmente.
- Sobreposição de faixas privadas entre redes que precisam se conectar via VPN é uma causa frequente de conflitos de roteamento.
- O esgotamento de endereços IPv4 públicos torna caro e escasso obter blocos próprios, reforçando a dependência de NAT em quase todos os cenários.
- Erros de digitação em máscaras (ex: /24 vs /23) podem expor ou isolar hosts de forma não intencional, sendo uma fonte comum de incidentes de segurança.
