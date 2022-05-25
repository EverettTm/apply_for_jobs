# Avaliação de conhecimentos em Desenvolvimento de Software

## Considere os seguintes dados:
 
Url para acesso: https://main.d2shxk5imahqcz.amplifyapp.com
## Diagrama em anexo
Diagrama de processos.png
## Explicando o projeto
Primeiro eu fiz o front end, no come�o tive uma certa dificuldade em rodas o ReactJS no AWS Amplify, mas no fim deu tudo certo, devido a imprevistos que eu acabei tendo durante a semana, acabei ficando alguns dias sem o computador deixando o prazo mais curto, por conta disso acabei fazendo um frontend mais simples, sem muita est�tica por�m focando na sua funcionalidade.

Depois fui realizar o banco de dados utilizando o DynamoDB, fiz em MYSQL que � o que eu mais tenho pr�tica, depois de tudo configurado consegui conectar tudo certo e partir para a fun��o Lambda.

A fun��o Lambda foi o mais divertido e desafiador de ser feito, primeiro precisava fazer uma fun��o que pegava os dados do front end, criptografar a senha e inclu�a no banco de dados. Minha ideia inicial era fazer com Python j� que seria a linguagem que eu mais tenho familiaridade, por�m tive muita dificuldade de fazer o pyodbc funcionar no Lambda, nao sei se foi uma quest�o de configura��o errada ou algo do tipo, no fim para n�o perder muito tempo optei por fazer via nodeJS mesmo. Pelo node utilizei o sequelize para fazer a integra��o com o banco de dados. Feito isso consegui inserir os dados, por�m pensei em alterar um pouco a proposta. Utilize o nodemailer para enviar um email ao cliente com uma chave de acesso e com a mesma ele consegue visualizar a senha. Escolhi gerar e criptografar no backend por ser mais seguro e dif�cil de acessar caso algu�m tenha inten��es maliciosas. Somente a senha do email que envia a senha que est� com baixa seguran�a, coloque em texto puro por�m se tivesse um pouco mais tempo teria colocado em uma vari�vel de ambiente.
Depois precisei fazer a fun��o  para pegar os dados e fazer a l�gica para verificar se o n�mero de views ou as horas  j� tinham expirado, e tamb�m apagar a senha caso o mesmo j� tenha atingido o n�mero de views ou o tempo apagando a senha.

Por fim, fui fazer o API Gateway, foi a parte mais simples do processo, fiz a API e fiz os m�todos para chamar no front e conectar com a fun��o Lambda.


## Seguran�a :
Primeiro que eu n�o me preocupei em fazer um sistemas de usu�rios,preferi focar apenas na parte de fazer o c�digo funcionar.
O sistema se protege de alguns tipos de ataques, por�m o mesmo apresenta algumas vulnerabilidades ( como por exemplo dados sens�veis em texto puro).
Considerando o OWASP 10 o programa se protege de alguns tipos de ataques com injection, j� que n�o � poss�vel injetar SQL por exemplo.
Insecurence design tamb�m � outro exemplo, em sistemas como C++ builder s�o sistemas inseguros.
Security Misconfiguration.
Componentes vulner�veis, s� utilizei componentes que recebem atualiza��o �ndice de seguranca.
S�o alguns exemplos do OWASP 10 que o sistema est� nos conformes.
Ficou faltando os logs que eu gostaria de ter inclu�do mas infelizmente n�o consegui fazer a tempo, mas julgo muito importante para verificar se o sistema est� sendo atacado e gerar uma auditoria do sistema.
Os logs s�o extremamente importantes, eu j� implementei e utilizo at� hoje nos sistemas em que eu trabalho, fazendo uma conex�o com uma api do telegram e enviando todos os logs para meu celular assim monitorando os ataques, como eu disse antes infelizmente n�o deu tempo de implementar esse sistema