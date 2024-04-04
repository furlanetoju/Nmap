# Nmap

Opção para uma "varredura UDP"

```
-sU
```

Detectar em qual sistema operacional o alvo está sendo executado.
```
-O
```

O Nmap fornece uma opção para detectar a versão dos serviços em execução no destino.
```
-sV
```

Aumentar a verbosidade? :shipit:

-V

**O nível de verbosidade um é bom, mas o nível de verbosidade dois é melhor! (Nota : é altamente recomendável usar sempre pelo menos esta opção)**
```
-vV
```

**Devemos sempre salvar o resultado de nossas varreduras - isso significa que só precisamos executar a varredura uma vez (reduzindo o tráfego de rede e, portanto, a chance de detecção) e nos dá uma referência para usar ao escrever relatórios para clientes.**

Qual opção você usaria para salvar os resultados do nmap em três formatos principais?
```
-oA
```
Qual opção você usaria para salvar os resultados do nmap em um formato "normal"?
```
-oN
```

Um formato de saída muito útil: como você salvaria os resultados em um formato "grepable"?
```
-oG
```

Às vezes, os resultados que obtemos simplesmente não são suficientes. **Se não nos importamos com o barulho que fazemos**, podemos ativar o modo **“agressivo”**. Esta é uma opção abreviada que ativa a detecção de serviço, detecção de sistema operacional, traceroute e verificação de script comum.

Para ativar essa configuração:
```
-A 
```

O Nmap oferece cinco níveis de modelo de "tempo". Eles são usados ​​essencialmente para aumentar a velocidade de execução da verificação. **Porém, tenha cuidado: velocidades mais altas são mais barulhentas e podem causar erros!**

Para definir o modelo de tempo para o nível 5?
```
-T5
```

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

