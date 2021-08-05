# porttitor-reckoning
Porttitor Reckoning Platform ©

Visão geral
###

Este módulo fornece uma maneira simples de decodificar mensagens de dispositivos uBlox GPS no formato UBX. Como o módulo NEO-M8U de alta precisão que criei, clique aqui para obter mais informações.

Este pacote não tem dependências! Isso é escrito em python puro usando apenas a lib padrão e oferece suporte a qualquer fluxo de bytes padrão. As mensagens predefinidas não são adicionadas ao analisador por padrão, isso permite que você tenha um controle rígido sobre quais mensagens podem ser analisadas.

Esta é a implementação mais rápida de um analisador UBX? Provavelmente não. 
Se a velocidade for crítica, você provavelmente precisará escrever algo em C. 
Se quiser algo que seja rápido e fácil de usar, você está no lugar certo. Continue lendo.

Suporta Python 3.5 e superior.
