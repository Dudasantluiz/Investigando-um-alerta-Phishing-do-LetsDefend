# Investigando-um-alerta-Phishing-do-LetsDefend

O Lets Defend SIEM detectou um e-mail de phishing e enviou um alerta. Neste artigo, mostrarei passo a passo como investiguei o alerta seguindo o guia fornecido pelo Lets Defend SIEM.

Primeiramente, foi criado um caso para investigar este alerta.

![image alt](https://github.com/Dudasantluiz/Investigando-um-alerta-Phishing-do-LetsDefend/blob/5ebe0d72db1871c0a2ed644c49be73591fd38339/Phishing/Captura%20de%20tela%202026-04-16%20102741.png)

Cliquei em continuar e fui redirecionado para a interface do playbook, onde o processo de investigação teve início.
![image alt](https://github.com/Dudasantluiz/Investigando-um-alerta-Phishing-do-LetsDefend/blob/97ad6eed07586417fd47bf82875553aa857d59a7/Phishing/Captura%20de%20tela%202026-04-16%20103419.png)

Então começou o manual de instruções.

O primeiro passo foi "Analisar o e-mail" e coletar informações sobre a mensagem recebida. O próprio alerta contém a maior parte das informações

![image alt](https://github.com/Dudasantluiz/Investigando-um-alerta-Phishing-do-LetsDefend/blob/ede3ceaedd862969ab986d8e7edd49d095294000/Phishing/Captura%20de%20tela%202026-04-16%20103719.png)

Após analisar o e-mail, encontrei o seguinte:

Quando foi enviado?
31 de janeiro de 2021, 15h48

Qual é o endereço SMTP do e-mail?
49.234.43.39

Qual é o endereço do remetente?
accounting@cmail.carleton.ca

Qual é o endereço do destinatário?
richard@letsdefend.io

O conteúdo do e-mail é suspeito? Para verificar se o conteúdo do e-mail é suspeito, acesse a segurança de e-mail no painel do Let's Defend SIEM e procure o endereço de e-mail do destinatário.

Clique no e-mail, copie o nome do anexo e cole-o no VirusTotal para confirmar se o anexo é suspeito.

![image alt](https://github.com/Dudasantluiz/Investigando-um-alerta-Phishing-do-LetsDefend/blob/8abb2b7cda2576dd44dda03f6951cf309623d99d/Phishing/Captura%20de%20tela%202026-04-16%20104438.png)

Após pesquisar o nome no VirusTotal, constatou-se que se trata de um vírus malicioso, pois 47 de 65 fornecedores o classificam como tal.
![image alt](https://github.com/Dudasantluiz/Investigando-um-alerta-Phishing-do-LetsDefend/blob/00f93749e01ffeeb7f0828ff130637a67c3ee6b7/Phishing/Captura%20de%20tela%202026-04-16%20104738.png)
Com base nos resultados, o conteúdo do e-mail é suspeito.
Existe algum tipo de vínculo? Sim
Com base na minha pesquisa anterior, constatei que há um anexo no e-mail
![image alt](https://github.com/Dudasantluiz/Investigando-um-alerta-Phishing-do-LetsDefend/blob/03d691a42d8d88be4b72242afcd4b5d5d9b4e3c4/Phishing/Captura%20de%20tela%202026-04-16%20104912.png)

Para analisar o anexo, utilizei o VirusTotal e o Hybrid Analysis e, com base no que descobri, o anexo é malicioso.
![image alt](https://github.com/Dudasantluiz/Investigando-um-alerta-Phishing-do-LetsDefend/blob/4ceee2c076b0ded32ca3cb0c660b61e7528781e0/Phishing/Captura%20de%20tela%202026-04-16%20104738.png)
![image alt](https://github.com/Dudasantluiz/Investigando-um-alerta-Phishing-do-LetsDefend/blob/fb525d212b476ab47ceb21401b6eeaf83de2f881/Phishing/Captura%20de%20tela%202026-04-16%20105322.png)

Para confirmar se o e-mail foi entregue ao usuário, acessei o canal de investigação, cliquei no alerta e verifiquei a ação do dispositivo.

Pressione Enter ou clique para ver a imagem em tamanho real.
![image alt](https://github.com/Dudasantluiz/Investigando-um-alerta-Phishing-do-LetsDefend/blob/84c6c70a30a71925ddd33b2ed6f24d86d01ce018/Phishing/Captura%20de%20tela%202026-04-16%20105716.png)

Após verificar a ação do dispositivo destacada em vermelho, consta como permitida, o que significa que foi "Entregue".
![image alt](https://github.com/Dudasantluiz/Investigando-um-alerta-Phishing-do-LetsDefend/blob/e0c45c6327b6f43e7c773e13acc9617f306271d9/Phishing/Captura%20de%20tela%202026-04-16%20105839.png)

Clique em “EXCLUIR” para continuar.
![image alt](https://github.com/Dudasantluiz/Investigando-um-alerta-Phishing-do-LetsDefend/blob/b2782d7721408a59348e87f85a944ea4a037f059/Phishing/Captura%20de%20tela%202026-04-16%20110102.png)

Para confirmar se o anexo foi aberto ou não, acessei o VirusTotal e verifiquei o endereço de contato.
Ao verificar o endereço de contato, comparei as informações com o gerenciamento de logs do SIEM, consultando o sistema de gerenciamento de logs.

![image alt](https://github.com/Dudasantluiz/Investigando-um-alerta-Phishing-do-LetsDefend/blob/a27acd3f70289236f56073c0f042e34ae47bdcdd/Phishing/Captura%20de%20tela%202026-04-16%20110742.png)
 Encontrei um endereço de contato que coincide com o mostrado no total de vírus acima.
