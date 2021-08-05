# porttitor-reckoning
Porttitor Reckoning Platform ©

Visão geral
###

# porttitor-reckoning [! [Build Status] (https://travis-ci.org/sergiohermes/porttitor-reckoning.svg?branch=master)] (https://travis-ci.org/sergiohermes/porttitor-reckoning)

## Visão geral
Este módulo fornece uma maneira simples de decodificar mensagens de dispositivos GPS no formato UBX.
Como o módulo NEO-M8U de alta precisão que criei,
<a href="https://docs.porttitor.com.br"> clique aqui para mais informações. </a> <br>
<br>
Este pacote não tem dependências! Isso é escrito em python puro usando apenas a lib padrão e oferece suporte a qualquer
fluxo de bytes padrão. As mensagens predefinidas não são adicionadas ao analisador por padrão, o que permite
você tem um controle rígido sobre quais mensagens podem ser analisadas.

Esta é a implementação mais rápida de um analisador? Provavelmente não. Se a velocidade é crítica, então você
provavelmente precisa escrever algo em C. Se você quiser algo que seja rápido o suficiente
e fácil de usar, você está no lugar certo. Continue lendo.

Suporta Python 3.5 e superior.


## Começo rápido

Instale o pacote com pip <br>
`pip install porttitor-reckoning`

Importe o módulo principal <br>
`from porttitor-reckoning import core`

Se a classe da mensagem desejada já foi definida, basta importá-la.
Caso contrário, você precisará construir as mensagens e classes sozinho, consulte os exemplos para obter mais informações. <br>
`from porttitor-reckoning import predefinido`

Construir o analisador <br>
`` `
parser = core.Parser ([
  predefinido.CLS_ACK,
  predefinido.CLS_NAV
])
`` `

Em seguida, você pode usar o analisador para decodificar mensagens de qualquer fluxo de bytes. <br>
`cls_name, msg_name, payload = parser.receive_from (porta)`

O resultado é uma tupla que pode ser descompactada conforme mostrado acima. <br>
As variáveis ​​`cls_name` e` msg_name` são strings, ie. `'NAV'`,`' PVT'`. <br>

A carga útil é a dupla nomeada da mensagem e pode ser acessada como um objeto. Os atributos compartilham os nomes dos campos. <br>
`print (cls_name, msg_name, payload.lat, payload.lng)`

Bitfields também são retornados como duplicatas nomeadas e podem ser acessados ​​da mesma maneira. <br>
`print (payload.flags.channel)`

Blocos repetidos são retornados como uma lista de blocos, os campos dentro de cada bloco também são chamados de tuplas. Todos os blocos repetidos nas mensagens predefinidas são denominados `RB`. <br>
`` `
para i no intervalo (len (payload.RB)):
  imprimir (payload.RB [i] .gnssId, payload.RB [i] .flags.health)
`` `

A melhor maneira de ver quais campos estão disponíveis é onde eles são definidos. No entanto, se você quiser inspecionar em tempo real, você pode `help (payload)` e olhar os atributos, ou usar o método protegido por tupla nomeado `payload._asdict ()` que retornará um dicionário ordenado de todos os atributos .


## Exemplos
Para exemplos completos, consulte o diretório de exemplos.

## TODO's
Quer contribuir? Sinta-se à vontade para enviar problemas ou solicitar solicitações.
Nada neste pacote é muito complicado, por favor, dê um crack e me ajude a melhorar isso.

- Adicionar a capacidade de empacotar mensagens em pacotes para comunicações bidirecionais
- Adicione mais e melhores testes
- Adicionar tipo de campo RU1_3
- Adicionar suporte assíncrono 
