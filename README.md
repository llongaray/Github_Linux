![Alt text](https://cdn.iconscout.com/icon/free/png-256/readme-3629011-3030236.png)

## Olá, abaixo contem os conhecimentos necessários para criar uma 'KEY SSH' e comandos posteriores.

>   1. Abrir o terminal;
>   2. Acessar a pasta ".ssh";

`$ cd ~/.ssh/`

###     Configuenando email e usuario do github no terminal.(Obrigatório)*
######  Digite o seguinte comando no terminal para adicionar seu email:
`$ git config --global user.email "[SEU_EMAIL_DO_GITHUB]"`
######  Digite o seguinte comando no terminal para adicionar seu usuario:
`$ git config --global user.name "[SEU_USER_DO_GITHUB]"`

#### Passo 1 — Criando o par de chaves:
######  O primeiro passo é criar uma par de chaves na máquina do cliente (geralmente seu computador):
`$ ssh-keygen` 
######  Por padrão, as versões mais recentes do ssh-keygen criarão um par de chaves RSA de 3072 bits, que é seguro o suficiente para a maioria dos casos de uso (você pode usar o sinalizador -b 4096 para criar uma chave maior de 4096 bits).
######  Após digitar o comando, você deve ver o seguinte resultado:

>Output  
>
>Generating public/private rsa key pair.  
>
>Enter file in which to save the key (/your_home/.ssh/id_rsa):

######  Pressione ENTER para salvar o par de chaves no sub-diretório .ssh/ no seu diretório home, ou especifique um caminho alternativo.
######  Se você tivesse gerado anteriormente um par de chaves SSH, pode ser que veja o seguinte prompt:

>Output
>
>/home/your_home/.ssh/id_rsa already exists.
>
>Overwrite (y/n)?

######  Se escolher substituir a chave no disco, você não poderá autenticar-se usando a chave anterior. Seja cuidadoso ao selecionar o sim, uma vez que este é um processo destrutivo que não pode ser revertido.
######  Então, você deve ver o seguinte prompt:

>Output
>
>Enter passphrase (empty for no passphrase):

######  Aqui você pode digitar uma frase secreta de forma opcional, o que é altamente recomendado. Uma frase secreta adiciona uma camada adicional de segurança para evitar que os usuários não autorizados façam login.
######  Você deve ver um resultado parecido com o seguinte:

![Alt text](https://github.com/felipengeletrica/Fundamentos_2022-2/blob/Leonardo_2022/.docs/1-Criando-Key-SSH.png)

######  Agora, você tem uma chave pública e uma chave privada que poderá usar para se autenticar. O próximo passo é colocar a chave pública no seu servidor para que você possa usar a autenticação baseada em chaves SSH para fazer login.





#### Passo 2 — Copiando a chave pública para o seu github.

######  1.  Acessar local da sua ssh-key;
`$ cd ~/.ssh/`
######  2.  Visualizar arquivos dentro do diretório;
`$ ls`
######  3.  Ler a ssh-key(Privada/Pública);
`$ cat [NOME_DA_KEY].pub/ cat [NOME_DA_KEY]`
######  4.  Copie o texto que aparecer ao dar o comando (copiar da .pub);

>Ctrl+Shift+C

![Alt text](https://github.com/felipengeletrica/Fundamentos_2022-2/blob/Leonardo_2022/.docs/2-Copiando-Key-SSH.png)

######  5.  Entre no seu github;

>github.com

######  6.  Vá em configurações/Settings;
######  7.  Entre em "SSH and GPG keys";
######  8.  Em SSH key click em "New SSH key";
######  9.  No campo "title" coloque o nome da sua key;
######  10. No campo "Key type" não mexa;
######  11. No campo "Key" cole a sua SSH-Key copiada anteriormente;

>Ctrl+V

######  12. Click em "Add SSH key";

#### Passo 3 - Automatizando autenticação da ssh-key pelo arquivo "config".

######  Dentro do diretório "~/.ssh/" digite o seguinte comando para acessar o VS Code:
`$ code .`
######  No VS Code no canto esquerdo estará todos os arquivos que se encontram dentro do diretório "~/.ssh/" (Sua SSH-Keys). Na barra acima deles click no icon de uma folha de papel para criar um novo arquivo.

######  Nomei o arquivo como "config".

######  Dentro do arquivo "config" digite o seguinte texto:
      Host github.com
         Hostname      ssh.github.com
         Port          443


####  Passo 4 - Adicionando SSH-Key.

######  No Terminal entre no diretório "~/.ssh/" e digite o seguinte comando:
`$ ssh-add [NOME_DA_KEY_PRIVADA]`
######  A seguinte mensagem será exibida:

      Enter passphrase for [NOME_DA_KEY]:
      Identity added: [NOME_DA_KEY] ([SEU_EMAIL_DO_GITHUB])

![Alt text](https://github.com/felipengeletrica/Fundamentos_2022-2/blob/Leonardo_2022/.docs/3-ADD-Key.png)

####  Passo 5 - Clonando seu repositório para o seu computador.

######  Crie uma pasta para colocar seus repositórios com o comando:
`$ mkdir [NOME_DA_PASTA]`
######  Entre dentro da pasta com o camando:
`$ cd ~/[NOME_DA_PASTA]`
######  Vá até seu github ("github.com") e entre no repositório que deseja clonar.
######  Click no botão verde "<> CODE" e depois na opção "SSH".
######  Copie o link que aparecer com:

>Ctrl+C

######  Volte para o terminal e digite o seguinte comando (Colar no terminal com "Ctrl+Shift+V"):
`$ git clone [LINK_COPIADO]`
######  Aparecerá a seguinte mensagem:

######  Agora entre na pasta do repositório com o comando:
`$ cd [NOME_DO_REPOSITÓRIO]`
######  Para editar pelo VS Code digite o comando dentro do diretório:
`$ code .`

![Alt text](https://github.com/felipengeletrica/Fundamentos_2022-2/blob/Leonardo_2022/.docs/4-git-clone.png)


####  Passo 6 - Comandos IMPORTANTES*:
#####  1º Para criar uma ramificação/branch digite o comando a seguir: (Estar dentro do diretório criando pelo comando "git clone"/Pasta do repositório em questão)*
`$ git checkout -b [NOME_DA_RAMIFICAÇÃO]`
######  Há seguinte messagem deve aparecer:

>Switched to a new branch '[NOME_DA_RAMIFICAÇÃO]'

#####  2º Para verificar o status do repositório digite o comando:
`$ git status`
#####  3º Para adicionar a "Fila" os arquivos alterados digite:
`$ git add [NOME_DO_ARQUIVO]`
######  OU para adicionar todos os arquivos:
`$ git add *`
#####  4º Para commit/comentar o ou os arquivos digite:
`$ git commit -m "[MENSAGEM]"`
#####  5º Para enviar para o github os arquivo que estão na "Fila" digite:
`$ git push`
######  OU para enviar para uma ramificação/branch criada digite:
`$ git push origin [NOME_DA_RAMIFICAÇÃO]`

![Alt text](https://github.com/felipengeletrica/Fundamentos_2022-2/blob/Leonardo_2022/.docs/5-Criando-Branch-e-push.png)