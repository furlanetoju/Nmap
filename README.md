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



