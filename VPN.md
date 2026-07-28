# VPN

VPN (Virtual Private Network) é uma tecnologia que cria um túnel criptografado entre dois pontos através de uma rede não confiável, geralmente a internet, fazendo com que o tráfego pareça e se comporte como se estivesse em uma rede privada. É amplamente usada para acesso remoto seguro, interconexão entre filiais e proteção de privacidade.

## Conceitos principais
- Tunelamento - técnica de encapsular pacotes de um protocolo dentro de outro para atravessar uma rede intermediária de forma transparente.
- Site-to-site VPN - conecta duas redes inteiras (por exemplo, matriz e filial) de forma permanente, como se fossem uma única rede lógica.
- Client-to-site VPN (acesso remoto) - conecta um dispositivo individual a uma rede corporativa, comum para trabalho remoto.
- IPsec - conjunto de protocolos que fornece autenticação e criptografia no nível de rede, muito usado em VPNs site-to-site.
- OpenVPN - solução de VPN baseada em SSL/TLS, flexível e amplamente compatível entre plataformas.
- WireGuard - protocolo de VPN moderno, com implementação mais simples e desempenho superior comparado a soluções mais antigas.
- Split tunneling - configuração em que apenas parte do tráfego do cliente passa pela VPN, enquanto o restante segue direto para a internet.
- Autenticação e chaves - VPNs dependem de certificados, chaves pré-compartilhadas ou credenciais para autenticar as partes antes de estabelecer o túnel.

## Na prática
- Empresas usam VPNs client-to-site para permitir que colaboradores remotos acessem sistemas internos como se estivessem no escritório.
- VPNs site-to-site com IPsec são comuns para interligar data centers próprios com ambientes de nuvem pública (AWS VPN Gateway, Azure VPN Gateway).
- WireGuard tem ganhado adoção por sua simplicidade de configuração e melhor desempenho em comparação a OpenVPN e IPsec tradicionais.
- Serviços de VPN comercial voltados a consumidores focam em privacidade e contorno de restrições geográficas, um uso diferente do cenário corporativo de acesso remoto.

## Pontos de atenção
- Uma VPN mal configurada pode criar um ponto único de falha ou um gargalo de performance, já que todo o tráfego tunelado passa por um único ponto de entrada/saída.
- Split tunneling aumenta o risco de segurança, pois parte do tráfego do dispositivo não passa pelas proteções da rede corporativa.
- MTU mal ajustado em túneis VPN é uma causa comum de lentidão intermitente, já que o overhead de encapsulamento reduz o espaço útil por pacote.
- VPN não é sinônimo de anonimato total: o provedor da VPN ainda pode ver o tráfego, e a criptografia protege o transporte, não necessariamente o conteúdo de aplicações inseguras.
