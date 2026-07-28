# Subnetting

Subnetting (sub-redes) é a técnica de dividir uma rede IP maior em redes menores e mais gerenciáveis. É uma habilidade fundamental em redes porque permite organizar hosts logicamente, reduzir domínios de broadcast, melhorar segurança por segmentação e usar o espaço de endereços com mais eficiência.

## Conceitos principais
- Máscara de sub-rede - define a fronteira entre a parte de rede e a parte de host de um endereço IP.
- Notação CIDR - representa a máscara como um número de bits, por exemplo /26 significa 26 bits para rede e 6 para hosts.
- Endereço de rede - o primeiro endereço de uma sub-rede, usado para identificar a rede em si (não atribuível a um host).
- Endereço de broadcast - o último endereço de uma sub-rede, usado para se comunicar com todos os hosts dela.
- Hosts utilizáveis - o total de endereços da sub-rede menos os reservados para rede e broadcast (2^n - 2, sendo n o número de bits de host).
- VLSM (Variable Length Subnet Mask) - técnica de usar máscaras de tamanhos diferentes dentro da mesma rede para otimizar o uso de endereços.
- Supernetting (agregação de rotas) - o processo inverso, agrupar várias sub-redes menores em um bloco maior para simplificar tabelas de roteamento.
- Domínio de broadcast - o conjunto de hosts que recebe o tráfego de broadcast de uma sub-rede; menor a sub-rede, menor o domínio.

## Na prática
- Ferramentas como `ipcalc` ou calculadoras de sub-rede online agilizam o cálculo de rede, broadcast, máscara e faixa de hosts a partir de um IP e prefixo.
- Empresas segmentam redes por função (ex: /24 para usuários, /28 para servidores, /29 para equipamentos de rede) para isolar tráfego e aplicar políticas de firewall específicas.
- Provedores de nuvem usam sub-redes para separar camadas de aplicação, como sub-redes públicas (com acesso à internet) e privadas (apenas internas) dentro de uma VPC.
- Ao planejar uma rede nova, é comum reservar blocos maiores do que o necessário no momento, para permitir crescimento sem redesenhar o endereçamento depois.

## Pontos de atenção
- Esquecer de descontar os endereços de rede e broadcast ao calcular quantos hosts cabem em uma sub-rede é um erro clássico de principiante.
- Sub-redes muito grandes aumentam o domínio de broadcast e podem degradar a performance da rede; sub-redes muito pequenas desperdiçam endereços e geram complexidade de gestão.
- Ao redimensionar uma sub-rede existente (mudar a máscara), é preciso revisar rotas estáticas, regras de firewall e configurações de DHCP que referenciam a faixa antiga.
- Erros de sobreposição de faixas entre sub-redes diferentes (especialmente ao interligar redes via VPN) causam conflitos de roteamento difíceis de diagnosticar.
