# Nmap

Ao fazer a varredura de portas com o Nmap , existem três tipos básicos de varredura. Estes são:

  - Varreduras de conexão TCP `-sT`
  - Varreduras SYN **"semi-abertas"** `-sS`
  - Varreduras UDP `-sU`

Além disso, existem vários tipos de varredura de portas menos comuns, alguns dos quais também abordaremos (embora com menos detalhes). Estes são:

  - Varreduras nulas de `TCP-sN`
  - Varreduras TCP `-sF`
  - Varreduras de Natal TCP`-sX`
    
A maioria deles (com exceção das varreduras UDP) é usada para propósitos muito semelhantes; no entanto, a forma como funcionam difere entre cada varredura. Isso significa que, embora uma das três primeiras varreduras provavelmente seja a sua escolha na maioria das situações, vale a pena ter em mente que existem outros tipos de varredura.

Em termos de varredura de rede, também examinaremos brevemente a varredura ICMP ou `ping`.

Na primeira conexão a uma rede alvo em uma atribuição de caixa preta, nosso primeiro objetivo é obter um **“mapa” da estrutura da rede** – ou, em outras palavras, queremos ver quais endereços IP contêm hosts ativos e quais não. .

Uma maneira de fazer isso é usar o Nmap para realizar a chamada **"varredura de ping"**. É exatamente como o nome sugere: o Nmap envia um pacote `ICMP` para cada endereço IP possível da rede especificada. Ao receber uma resposta, ele marca o endereço IP que respondeu como ativo. Por motivos que veremos em uma tarefa posterior, isso nem sempre é exato; no entanto, pode fornecer uma espécie de linha de base e, portanto, vale a pena abordá-la.

Para realizar uma varredura de ping, usamos a opção `-sn` em conjunto com intervalos de IP que podem ser especificados com uma notação hífen (-) ou CIDR. ou seja, poderíamos escanear a 192.168.0.x rede usando:
```
nmap -sn 192.168.0.1-254
```
ou
```
nmap -sn 192.168.0.0/24
```

O `-sn` switch diz ao Nmap para não varrer nenhuma porta - forçando-o a confiar principalmente em pacotes de eco `ICMP` (ou solicitações ARP em uma rede local, se executadas com `sudo` ou diretamente como usuário **root**) para identificar alvos. Além das solicitações de eco ICMP, o `-sn` switch também fará com que o nmap envie um pacote **TCP SYN** para a porta 443 do alvo, bem como um pacote **TCP ACK** (ou TCP SYN se não for executado como root) para a porta 80 do alvo.
