# DNS

DNS (Domain Name System) é o sistema distribuído responsável por traduzir nomes de domínio legíveis por humanos (como exemplo.com) em endereços IP que os computadores usam para se comunicar. É uma peça essencial da internet, já que praticamente toda navegação, e-mail e chamada de API depende de uma resolução DNS bem-sucedida antes de qualquer outra coisa acontecer.

## Conceitos principais
- Hierarquia DNS - estrutura em árvore com a raiz (.), domínios de topo (TLDs como .com, .br), domínios de segundo nível e subdomínios.
- Registro A/AAAA - mapeia um nome de domínio para um endereço IPv4 (A) ou IPv6 (AAAA).
- Registro CNAME - cria um alias, apontando um nome de domínio para outro nome de domínio.
- Registro MX - define os servidores responsáveis por receber e-mails de um domínio.
- Registro NS - indica quais servidores são autoritativos para responder consultas sobre um domínio.
- Servidor recursivo vs autoritativo - o recursivo faz o trabalho de buscar a resposta percorrendo a hierarquia; o autoritativo é a fonte final da informação sobre um domínio específico.
- TTL (Time to Live) - tempo que uma resposta DNS pode ser mantida em cache antes de precisar ser consultada novamente.
- Cache DNS - armazenamento temporário de respostas em resolvedores, sistemas operacionais e navegadores, para acelerar consultas repetidas.

## Na prática
- `dig`, `nslookup` e `host` são as ferramentas de linha de comando mais usadas para consultar registros DNS e depurar problemas de resolução.
- Serviços de DNS gerenciado (Route 53, Cloudflare DNS, Google Cloud DNS) são amplamente usados para hospedar zonas DNS de domínios de produção com alta disponibilidade.
- Ao migrar um site ou serviço, é comum ajustar o TTL para um valor baixo antes da mudança, garantindo propagação rápida, e voltar a um valor mais alto depois para reduzir carga nos servidores.
- CDNs e balanceadores de carga globais usam DNS (como respostas geolocalizadas ou GeoDNS) para direcionar usuários ao servidor mais próximo ou disponível.

## Pontos de atenção
- Alterações em registros DNS não têm efeito imediato para todos os usuários por causa do cache distribuído; o tempo de propagação real pode ser maior que o TTL configurado.
- Um erro de configuração no registro NS de um domínio pode torná-lo completamente inacessível, mesmo que o servidor de destino esteja funcionando perfeitamente.
- Depender de um único provedor DNS sem redundância é um ponto único de falha; quedas de grandes provedores DNS já causaram indisponibilidade generalizada de serviços populares.
- DNS tradicionalmente trafega sem criptografia (porta 53/UDP), o que motivou a adoção crescente de DNS sobre HTTPS (DoH) e DNS sobre TLS (DoT) para privacidade.
