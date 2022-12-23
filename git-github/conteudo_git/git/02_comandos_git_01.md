<h1>Comandos do Git - Parte 01</h1>



<h2>1.Configurando o Git</h2>

1. Para verificar se o Git está instalado no sistema e a versão, digite o comando:

```bash
git version
```

2. Para listar todas as configurações do Git, digite o comando:

```bash
git config --list 
```

*Caso não apareça nenhuma configuração, você ainda não configurou o seu Git.*

3. Para configurar o seu **nome** no Git, digite o comando:

```bash
git config --global user.name "Seu_Nome"
```

*Substitua Seu_Nome, pelo seu nome. Exemplo: João*

4. Para verificar se o seu **nome** foi configurado corretamente no Git, digite o comando:

```bash
git config user.name
```

5. Para configurar o seu **e-mail** no Git, digite o comando:

```bash
git config --global user.email "seu_email@email.com"
```

*Substitua seu_email, pelo seu e-mail cadastrado no Github. Exemplo: joao@email.com*

6. Para verificar se o seu **e-mail** foi configurado corretamente no Git, digite o comando:

```bash
git config user.email
```

7. Para configurar o **Editor de Código padrão** do Git, digite o comando:

**Configurar o Nano:**

```bash
git config --global core.editor nano
```

**Configurar o VSCode:**

```bash
git config --global core.editor 'code --wait'
```

8. Para verificar se o seu **Editor de Código** foi configurado corretamente no Git, digite o comando:

```bash
git config core.editor
```

9. Para configurar o **nome padrão da branch principal** do repositório Git, digite o comando:

```bash
git config --global init.defaultBranch main
```

> Esta configuração é importante para que todes os seus repositórios, a branch principal seja definida como **main**.

10. Para verificar se o **nome padrão da branch principal** foi configurado como main, digite o comando:

```bash
git config init.defaultBranch
```

11. Para listar todas as configurações do Git, digite o comando:

```bash
git config --list 
```

*Observe que desta vez será exibida uma lista com todas as configurações você fez no seu Git.*

12. Para utilizar a estratégia de mesclagem de repositórios padrão ao invés de usar a estratégia de mesclagem rebase, digite o comando:

```bash
git config pull.rebase false
```

*Como a estratégia rebase pode afetar os commits do repositório remoto de outros usuários, aumentando a probabilidade de conflitos, é recomendado utilizar a estratégia padrão. O comando acima desativa a estratégia rebase como estratégia padrão.*

<br />

<div align="left"><img src="https://i.imgur.com/fu9QxlT.png" title="source: imgur.com" width="25px"/> <a href="https://git-scm.com/docs/git-config/pt_BR" target="_blank"><b>Documentação: <i>Git Config</i></b></a>

<br />


<h2>2.Configurando a Chave SSH</h2>

**SSH - Secure Socket Shell**, é um dos protocolos  específicos para implementar a segurança na troca de arquivos entre cliente e servidor  na Internet, usando criptografia. O objetivo do SSH é permitir que  pessoas desenvolvedoras ou outros usuários realizem alterações em sites e  servidores utilizando uma conexão simples e segura.

O Github utiliza o modelo de Criptografia Assimétrica, ou seja, utiliza duas chaves secretas separadas. **Essas chaves servem tanto para codificar quanto para decodificar o processo de comunicação entre o cliente e o servidor.** Ambas são conhecidas como chave-pública e chave-privada. 

As chaves SSH são geradas através de algoritmos complexos, de modo que seja improvável falsificar ou identificar a chave privada, ainda que a chave pública seja conhecida. Dessa maneira, é necessário manter a chave privada em segredo, sendo utilizada apenas por usuário autorizado. Já as chaves públicas podem ser compartilhadas com outras pessoas. 

Para gerar as **chaves SSH**, é necessário inserir informações como senhas, a chamadas de frase. Geralmente, utilizam-se frases curtas para gerar chaves públicas e privadas.

<div align="center"><img src="https://i.imgur.com/snWEIxN.png" title="source: imgur.com" /></div>

Para iniciar uma conexão em SSH no Github, é realizada uma negociação do protocolo, os algoritmos criptográficos e a chave da sessão, além de autenticar o servidor com uma chave de host e o usuário com autenticação de chave pública ou senha. Depois disso, trocam-se as informações, inclusive gráficos, arquivos e dados do terminal. Fazendo uma analogia, é como se a Chave Pública fosse um cadeado, que só pode ser aberto pela sua própria chave (Chave Privada).

A autenticação por meio de chave pública garante mais segurança do que outros meios de autenticação, como é o caso das senhas. Além disso, esse tipo de autenticação é amplamente utilizado para acesso privilegiado humano e máquina a máquina. 

<h3>2.1.Criar o par de Chaves SSH</h3>

1. Acesse a pasta do usuário, através do comando abaixo:

```bash
cd ~
```

2. Para criar a Chave SSH, utilize o comando abaixo:

```bash
ssh-keygen -t rsa -b 2048
```

3. Após executar o comando, será indicada a pasta onde será gravado o par de chaves, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/ZixCQrm.png" title="source: imgur.com" /></div>

4. Pressione a tecla **enter** do teclado para continuar. Na sequência, será solicitado o cadastramento de uma **frase**, que funcionará como uma senha da Chave, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/3LYQWgA.png" title="source: imgur.com" /></div>

5. Cadastre uma senha, ou pressione a tecla enter para deixar sem a senha. Na sequência será solicitada a confirmação da frase, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/sAizmSJ.png" title="source: imgur.com" /></div>

6. Digite a senha novamente, ou pressione a tecla enter para deixar sem a senha. Na sequência, será exibida a a confirmação da criação do par de chaves SSH, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/H3ezS1J.png" title="source: imgur.com" /></div>

<br />

| <img src="https://i.imgur.com/RfjtOFi.png" title="source: imgur.com" width="120px"/> | <div align="left">**DICA:** Caso você cadastre a frase na Chave SSH, todas as vezes que você efetuar comandos como o git push e o git pull, esta frase será solicitada pelo github.</div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

7. Após a criação da Chave, utilize o comando abaixo para visualizar o conteúdo da Chave pública:

```bash
cat ~/.ssh/id_rsa.pub
```

8. Será exibido no console o conteúdo da chave SSH pública. Selecione e copie o conteúdo do arquivo.

<br />

| <img src="https://i.imgur.com/RfjtOFi.png" title="source: imgur.com" width="120px"/> | <div align="left">**DICA:** Para recriar a chave SSH, apague a pasta .ssh através do comando rm -rf .ssh e repita os passos acima.</div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<h3>2.2.Adicionar a Chave Pública no Github</h3>

1. Acesse a sua conta do Github
2. Na Barra de Navegação superior da Conta do Github, clique no menu do seu Perfil, ao lado do botão **+**, e no menu que será aberto, clique na opção **Settings**.

<div align="center"><img src="https://i.imgur.com/QRPnPdA.png" title="source: imgur.com" /></div>

3. Na próxima tela, no menu localizado na lateral esquerda, clique na opção **SSH and GPG Keys**.

<div align="center"><img src="https://i.imgur.com/thbauWb.png" title="source: imgur.com" /></div>

4. Na próxima tela, clique no botão **New SSH Key**.

<div align="center"><img src="https://i.imgur.com/XX0KSUm.png" title="source: imgur.com" /></div>

5. Digite um nome para Chave no item **Title** (macOS, por exemplo) e cole a Chave que foi copiada no item **Key**.

<div align="center"><img src="https://i.imgur.com/GR2sByz.png" title="source: imgur.com" /></div>

6. A Chave foi adicionada no GitHub!

<div align="center"><img src="https://i.imgur.com/D57g5d2.png" title="source: imgur.com" /></div>

<br />

<div align="left"><img src="https://i.imgur.com/JACNZiR.png" title="source: imgur.com" width="25px"/> <a href="https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent" target="_blank"><b>Documentação: <i>Gerando a Chave SSH</i></b></a>

<br />

<h2>3.Criando o seu primeiro repositório local</h2>

1. Vamos checar qual é a sua pasta atual. Digite o comando:

```bash
pwd
```

*Verifique se você está na pasta do seu usuário (Home Directory).* 

2. Caso não esteja na pasta do seu usuário, digite o comando:

```bash
cd ~
```

3. Vamos criar o nosso primeiro repositório na pasta do usuário. Vamos criar a pasta **aulagit**, através do comando:

```bash
mkdir aulagit
```

4. Na sequência vamos acessar esta pasta através do comando:

```bash
cd aulagit
```

5. Dentro da pasta **aulagit**, vamos criar o nosso **Repositório Git Local**, através do comando:

```bash
git init
```

6. Para verificar se o repositório foi criado, utilize o comando:

```bash
git status
```

O comando **git status** mostra se a pasta atual é um repositório e qual é o status atual (vazio, possui arquivos aguardando para serem versionados, entre outros).

7. Observe na imagem abaixo, que o repositório foi criado, não existe nenhum commit e não existe nenhuma pasta ou arquivo para ser "commitada" 

<div align="center"><img src="https://i.imgur.com/ZI8l3R8.png" title="source: imgur.com" width="90%"/></div>

8. Uma outra forma de verificar se o repositório foi criado é através do comando:

```bash
ls -a
```

*Observe que dentro da pasta aula git, foi criada uma pasta oculta com chamada **.git***

O comando **git init** criou a pasta `.git` (oculta), contendo as subpastas `objects`, `refs/heads`, `refs/tags` e alguns arquivos modelo.  Também foi criado um arquivo inicial chamado `HEAD`, que guarda a referencia `HEAD` da branch principal. o Head funciona como um ponteiro, indicando qual é a branch atual. 

9. Para descobrir qual é a sua branch atual, utilize o  comando:

```bash
git branch --show-current
```

O comando acima exibirá que no momento, o **HEAD** do repositório está na branch **main**, ou seja, a branch atual do repositório.

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="100px"/> | <div align="left"> **ATENÇÃO:** * O arquivo HEAD é um arquivo interno do Git, portanto, não deve ser manipulado manualmente.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<div align="left"><img src="https://i.imgur.com/fu9QxlT.png" title="source: imgur.com" width="25px"/> <a href="https://git-scm.com/docs/git-init/pt_BR" target="_blank"><b>Documentação: <i>Git Init</i></b></a>

<div align="left"><img src="https://i.imgur.com/fu9QxlT.png" title="source: imgur.com" width="25px"/> <a href="https://git-scm.com/docs/git-status/pt_BR" target="_blank"><b>Documentação: <i>Git Status</i></b></a>

<div align="left"><img src="https://i.imgur.com/fu9QxlT.png" title="source: imgur.com" width="25px"/> <a href="https://git-scm.com/docs/git-branch/pt_BR" target="_blank"><b>Documentação: <i>Git Branch</i></b></a>

<br />

<h2>4.Versionando os arquivos no repositório local</h2>

1. Antes começarmos a versionar, vamos criar alguns arquivos dentro do nosso repositório, através do comando abaixo:

```bash
touch portugol.txt java.txt mysql.txt
```

2. Na sequência, vamos editar os arquivos no VSCode, através do comando:

```bash
code .
```

<br />

| <img src="https://i.imgur.com/RfjtOFi.png" title="source: imgur.com" width="120px"/> | <div align="left">**DICA:** Caso o comando code . não funcione no macOS X, abra o VSCode, execute a combinação de teclas: command + shift + P, filtre pela palavra "shell" e selecione a opção "Install 'code' comand in PATH".</div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

3. A pasta **aulagit** será aberta no **VSCode**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/z6LMMQn.png" title="source: imgur.com" width="90%"/></div>

4. Vamos editar os 3 arquivos e adicionar as seguintes frases em cada arquivo:

- **portugol.txt:** Portugol é uma pseudo linguagem.
- **java.txt:** Java é uma Linguagem de programação.
- **mysql.txt:** MySQL é um Sistema Gerenciador de Banco de dados.

5. Na sequência, vamos adicionar os arquivos no índice do repositório (Staging), através do comando:

```bash
git add .
```

O comando **git add** atualiza o índice do repositório com o conteúdo atual encontrado na árvore de trabalho para preparar o conteúdo para o próximo commit. O **ponto** após o comando git add, indica que será adicionado todo o conteúdo atual, incluindo os arquivos e pastas.

O conteúdo adicionado é enviado para o **Staging**, que é um espaço temporário onde você determina quais mudanças serão adicionadas ao repositório. Utilizar o staging é muito simples com o comando **git add** você adiciona os arquivos para o staging, e quando estiver satisfeito com as alterações efetua um commit, que veremos na sequência.

| <img src="https://i.imgur.com/RfjtOFi.png" title="source: imgur.com" width="120px"/> | <div align="left">**DICA:** O git não versiona pastas vazias. Para versionar uma pasta é necessário adicionar arquivos dentro dela.</div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

6. Para verificar as alterações no repositório, utilize o comando:

```bash
git status
```

7. O comando **git status** retornará que existem arquivos aguardando para serem "commitados" no índice do repositório, como mostra a imagem abaixo:

<div align="left"><img src="https://i.imgur.com/WpqHlSQ.png" title="source: imgur.com" /></div>

8. Para "commitar" os arquivos, utilize o comando:

```bash
git commit -m "Meu primeiro commit"
```

O comando **git commit** cria um novo commit com todos os conteúdos atuais do índice e a mensagem informada entre aspas no registro log descrevendo todas as alterações que foram realizadas. Um novo commit é um herdeiro direto do `HEAD` que em geral é o topo do branch atual e o branch é atualizado para apontar para este novo commit.

> Os **commits** são as principais unidades de bloco de construção de uma linha do tempo do projeto Git. Os commits podem ser considerados instantâneos ou marcos ao longo da linha do tempo de um projeto Git. Os commits são criados com o comando **git commit** para capturar o estado de um projeto naquele momento.

9. Após executar o comando, será exibida a mensagem abaixo:

<div align="left"><img src="https://i.imgur.com/F5lijPS.png" title="source: imgur.com" /></div>

10. Para verificar se os arquivos e pastas foram "commitados", utilize o comando:

```bash
git status
```

11. O comando **git status** retornará que não existem arquivos aguardando para serem "commitados", como mostra a imagem abaixo:

<div align="left"><img src="https://i.imgur.com/BOIgZ5Y.png" title="source: imgur.com" /></div>

12. Para visualizar as informações do histórico de commits, utilize o comando:

```bash
git log
```

13. Observe na imagem abaixo, que serão exibidos todos os detalhes do commit:

<div align="left"><img src="https://i.imgur.com/IxI238Z.png" title="source: imgur.com" /></div>

<br />

<div align="left"><img src="https://i.imgur.com/fu9QxlT.png" title="source: imgur.com" width="25px"/> <a href="https://git-scm.com/docs/git-add/pt_BR" target="_blank"><b>Documentação: <i>Git Add</i></b></a>

<div align="left"><img src="https://i.imgur.com/fu9QxlT.png" title="source: imgur.com" width="25px"/> <a href="https://git-scm.com/docs/git-status/pt_BR" target="_blank"><b>Documentação: <i>Git Status</i></b></a>

<div align="left"><img src="https://i.imgur.com/fu9QxlT.png" title="source: imgur.com" width="25px"/> <a href="https://git-scm.com/docs/git-commit/pt_BR" target="_blank"><b>Documentação: <i>Git Commit</i></b></a>

<div align="left"><img src="https://i.imgur.com/fu9QxlT.png" title="source: imgur.com" width="25px"/> <a href="https://git-scm.com/docs/git-log/pt_BR" target="_blank"><b>Documentação: <i>Git log</i></b></a>

<br />

<h2>5.Entendendo o fluxo de trabalho do Git</h2>

Os seus repositórios locais consistem em três "árvores" mantidas pelo git:

- A primeira é o seu **Working Directory** (pasta de trabalho), ou seja, a pasta onde você criou o seu repositório e estão armazenados todos os arquivos do repositório (independente de estarem commitados). No nosso exemplo é a pasta **aulagit**, que foi criada na pasta do seu usuário (home directory) e inicializada como um repositório git.
- A segunda é a **Index** (índice) ou Staging Area, que funciona como uma área temporária onde ficam armazenados os arquivos que foram criados, atualizados ou apagados, desde o ultimo commit. As alterações no Stage são simplesmente alterações no **working Directory**, em que se pretende “avisar” ao repositório sobre essas alterações que foram realizadas. 
- A terceira é a **HEAD**, que funciona como uma espécie de ponteiro, possui a função de apontar para o último *commit* (confirmação) que você fez.        

<div align="left"><img src="https://i.imgur.com/GKHWuOW.png" title="source: imgur.com" /></div>

A **HEAD** aponta para o **último commit**, que foi realizado no repositório, logo quando você executa o comando **git commit você está dizendo para a HEAD que este novo commit é o mais atual e será a nova HEAD** do seu repositório.

Vamos entender o fluxo na prática! 

1. Crie mais 2 arquivos dentro do nosso repositório, através do comando abaixo:

```bash
touch spring.txt docker.txt
```

2. Na sequência, volte para **VSCode**, abra os 2 arquivos e adicione as seguintes frases em cada arquivo:

- **spring.txt:** Spring é um framwework.
- **docker.txt:** Docker é um gerenciador de containers.

3. Para verificar as alterações no repositório, utilize o comando:

```bash
git status
```

4. O comando **git status** retornará que existem arquivos que não foram adicionados no índice do repositório, como mostra a imagem abaixo:

<div align="left"><img src="https://i.imgur.com/JIpTtvE.png" title="source: imgur.com" /></div>

5. Na sequência, vamos adicionar os arquivos no índice do repositório, através do comando:

```bash
git add .
```

6. Para verificar as alterações no repositório, utilize o comando:

```bash
git status
```

7. O comando **git status** retornará que existem arquivos aguardando para serem "commitados" no índice do repositório, como mostra a imagem abaixo:

<div align="left"><img src="https://i.imgur.com/kAbUDmf.png" title="source: imgur.com" /></div>

8. Para "commitar" os arquivos, utilize o comando:

```bash
git commit -m "Meu segundo commit"
```

9. Para verificar as alterações no repositório, utilize o comando:

```bash
git status
```

10. O comando **git status** retornará que não existem arquivos aguardando para serem "commitados", como mostra a imagem abaixo:

<div align="left"><img src="https://i.imgur.com/BOIgZ5Y.png" title="source: imgur.com" /></div>

11. Para visualizar as informações do histórico de commits, utilize o comando:

```bash
git log
```

12. Observe na imagem abaixo, que serão exibidos todos os detalhes do commit:

<div align="left"><img src="https://i.imgur.com/esS7wBR.png" title="source: imgur.com" /></div>

*Observe que o **HEAD** do repositório passou a ser o **"Meu segundo commit"**.*

<br />

<h2>6.Atualizar o conteúdo de um arquivo</h2>

1. Volte para **VSCode**, abra o arquivo **spring.txt** e atualize o seu conteúdo:

- **spring.txt:** Spring é um framwework Java.

2. Para checar as mudanças que aconteceram no arquivo **spring.txt**, utilize o comando:

```bash
git diff
```

3. O comando **git diff** retornará que o arquivo **spring.txt** foi modificado e indica quais foram as alterações, como mostra a imagem abaixo:

<div align="left"><img src="https://i.imgur.com/B7tUQdv.png" title="source: imgur.com" /></div>

4. Para verificar as alterações no repositório, utilize o comando:

```bash
git status
```

5. O comando **git status** retornará que o arquivo **spring.txt** foi atualizado e ainda não foi adicionado no índice do repositório, como mostra a imagem abaixo:

<div align="left"><img src="https://i.imgur.com/xETINlK.png" title="source: imgur.com" /></div>

6. Na sequência, vamos adicionar **apenas o arquivo spring.txt** no índice do repositório, através do comando:

```bash
git add spring.txt
```

7. Para verificar as alterações no repositório, utilize o comando:

```bash
git status
```

8. O comando **git status** retornará que o arquivo **spring.txt** está aguardando para ser "commitado" no índice do repositório, como mostra a imagem abaixo:

<div align="left"><img src="https://i.imgur.com/XC8uxsD.png" title="source: imgur.com" /></div>

9. Para "commitar" o arquivo **spring.txt**, utilize o comando:

```bash
git commit -m "Meu terceiro commit"
```

10. Para verificar as alterações no repositório, utilize o comando:

```bash
git status
```

11. O comando **git status** retornará que não existem arquivos aguardando para serem "commitados", como mostra a imagem abaixo:

<div align="left"><img src="https://i.imgur.com/BOIgZ5Y.png" title="source: imgur.com" /></div>

12. Para visualizar o histórico de commits, utilize o comando:

```bash
git log
```

13. Observe na imagem abaixo, que serão exibidos todos os detalhes do commit:

<div align="left"><img src="https://i.imgur.com/RtYyCxQ.png" title="source: imgur.com" /></div>

14. Observe que o **HEAD** do repositório passou a ser o **"Meu terceiro commit"**.

<br />

<div align="left"><img src="https://i.imgur.com/fu9QxlT.png" title="source: imgur.com" width="25px"/> <a href="https://git-scm.com/docs/git-diff/pt_BR" target="_blank"><b>Documentação: <i>Git Diff</i></b></a>

<br />


<h2>7.Desfazendo um commit</h2>

1. Vamos desfazer o commit **Meu terceiro commit**, através do comando:

```bash
git reset HEAD~1
```

2. Para checar o status do repositório, utilize o comando:

```bash
git status
```

3. O comando **git status** retornará que o arquivo **spring.txt** voltou a ficar disponível para ser adicionado, como mostra a imagem abaixo:

<div align="left"><img src="https://i.imgur.com/xETINlK.png" title="source: imgur.com" /></div>

4. Para visualizar o histórico dos commits, utilize o comando:

```bash
git log
```

5. Observe na imagem abaixo, que o **HEAD** do repositório passou a ser o **"Meu segundo commit"**, após o **Meu terceiro commit** ser desfeito:

<div align="left"><img src="https://i.imgur.com/esS7wBR.png" title="source: imgur.com" /></div>

*O comando **git reset HEAD~1** redefiniu o `HEAD` atual para um commit anterior (~1) ao commit atual, desfazendo o mesmo.*

| <img src="https://i.imgur.com/RfjtOFi.png" title="source: imgur.com" width="120px"/> | <div align="left">**DICA:** Para desfazer o commit e apagar todos os arquivos e pastas que foram commitados, utilize o comando git reset HEAD~1 -- hard.</div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

6. Vamos refazer o commit **Meu terceiro commit**, através do comando:

```bash
git commit -a -m "Meu terceiro commit"
```

*A opção **-a** é o equivalente a fazer o **git add** . junto com o comando **git commit**.*

| <img src="https://i.imgur.com/RfjtOFi.png" title="source: imgur.com" width="120px"/> | <div align="left">**DICA:** A opção -a funciona apenas se for um commit de atualização do arquivo. Para arquivos novos é necessário usar os comandos git add e na sequência o git commit.</div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<div align="left"><img src="https://i.imgur.com/fu9QxlT.png" title="source: imgur.com" width="25px"/> <a href="https://git-scm.com/docs/git-reset/pt_BR" target="_blank"><b>Documentação: <i>Git Reset</i></b></a>
<br />


<h2>8.Publicando o Repositório Local no Github</h2>

<h3>8.1.Criar o Repositório Remoto no Github</h3>


Vamos criar o repositório no Github:

1. Acesse a sua conta do Github

2. Na Barra de Navegação superior da Conta do Github, clique no botão **+** e no menu que será aberto, clique na opção **New repository**.

<div align="center"><img src="https://i.imgur.com/JBoiJv1.png" title="source: imgur.com" /></div>

3. Crie um **Repositório Público**, chamado **aulagit**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/8qxr1c4.png" title="source: imgur.com" /></div>

4. Em seguida clique no botão **Create Repository** no final da tela.
4. Será aberta uma tela semelhante a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/RgrjbyQ.png" title="source: imgur.com" /></div>

6. Copie o endereço do Repositório indicado pela seta amarela. Observe que foi copiado o endereço **ssh**.

<h3>8.2.Conectar o Repositório Local com o Repositório Remoto</h3>

1. Crie a conexão do Repositório Local com o Repositório Remoto, através do comando:

```bash
git remote add origin git@github.com:rafaelq80/aulagit.git
```

*Observe que depois da palavra origin foi inserido o **endereço SSH do Repositório Remoto** que foi copiado do Github.*

2. Para confirmar se o Repositório Local está conectado com o Repositório Remoto, utilize o comando:

```bash
git remote -v
```

3. Observe na imagem abaixo, que será exibido o endereço do Repositório Remoto, confirmando a conexão:

<div align="left"><img src="https://i.imgur.com/jXhsgBV.png" title="source: imgur.com" /></div>

<h3>8.3.Enviar o conteúdo do Repositório Local para o Github</h3>

1. Envie o conteúdo do Repositório Local para o Repositório Remoto, através do comando:

```bash
git push origin main
```

Observe que no comando **git push** foram adicionados 2 parâmetros:

- **origin:** O Repositório Remoto;
- **main:** A Branch do Repositório Local, que será enviada para o Repositório Remoto.

2. Observe na imagem abaixo, que será solicitada a frase que foi cadastrada na chave ssh que você cadastrou. Digite a frase cadastrada.

<div align="left"><img src="https://i.imgur.com/fMX0XQ7.png" title="source: imgur.com" /></div>

3. Volte para o Github e verifique se os arquivos estão disponíveis no Repositório Remoto, no Github, como mostra a imagem abaixo:

<div align="left"><img src="https://i.imgur.com/5ou5Nhd.png" title="source: imgur.com" /></div>

<br />

<div align="left"><img src="https://i.imgur.com/fu9QxlT.png" title="source: imgur.com" width="25px"/> <a href="https://git-scm.com/docs/git-remote/pt_BR" target="_blank"><b>Documentação: <i>Git Remote</i></b></a>
<div align="left"><img src="https://i.imgur.com/fu9QxlT.png" title="source: imgur.com" width="25px"/> <a href="https://git-scm.com/docs/git-push/pt_BR" target="_blank"><b>Documentação: <i>Git Push</i></b></a>

<br /><br />

<div align="left"><a href="../README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div>
