# Principais fundamentos do Git

## Os Três Estados

Os três estados do Git em relação ao seus arquivos, são basicamente: **Working Directory**, **Staging Area** e **Git Directory**.

![treeStates](https://git-scm.com/figures/18333fig0106-tn.png)

O *workflow* básico do Git pode ser descrito assim:

* Você modifica arquivos no seu diretório de trabalho.
* Você seleciona os arquivos, adicionando snapshots deles para sua área de preparação.
* Você faz um commit, que leva os arquivos como eles estão na sua área de preparação e os armazena permanentemente no seu diretório Git.

## Instalando o Git em sua máquina 

Para realizar a instalação do Git em seu Linux, utilizaremos o terminal. Lembrando que em algumas distribuições o Git já vem integrado com o próprio sistema.

### Ubuntu

```
apt-get install git
```

### Manjaro

```
pacman -S git
```

### Fedora

```
dnf install git
```

## Inicializando um Repositório em um Diretório Existente

Caso você esteja iniciando o monitoramento de um projeto existente com Git, você precisa ir para o diretório do projeto e digitar.

```
git init
```

## Clonando um Repositório Existente

Caso você queira copiar um repositório Git já existente — por exemplo, um projeto que você queira contribuir — o comando necessário é *git clone*.

Você clona um repositório com *git clone [url]*. Por exemplo, caso você queria clonar a biblioteca Git do Ruby chamada Grit, você pode fazê-lo da seguinte forma:

```
git clone git://github.com/schacon/grit.git
```

## Gravando Alterações no Repositório 

Você tem um repositório Git e um checkout ou cópia funcional dos arquivos para esse projeto. Você precisa fazer algumas mudanças e fazer o commit das partes destas mudanças em seu repositório cada vez que o projeto atinge um estado no qual você queira gravar.

Conforme você edita esses arquivos, o Git passa a vê-los como modificados, porque você os alterou desde seu último commit. Você seleciona esses arquivos modificados e então faz o commit de todas as alterações selecionadas e o ciclo se repete.

![writeChanges](https://git-scm.com/figures/18333fig0201-tn.png)

## Verificando o Status de Seus Arquivos

A principal ferramenta utilizada para determinar quais arquivos estão em quais estados é o comando *git status*. Se você executar este comando diretamente após uma clonagem, você deverá ver algo similar a isso:

```
git status
```

## Adicionado Novos Arquivos

Para passar a monitorar um novo arquivo, use o comando git add. Para monitorar o arquivo README, você pode rodar isso:

```
git add [nomeArquivo]
```

> Ou então podemos utilizar o *git add .* para adicionar todos os arquivos.

## Fazendo Commit de Suas Mudanças

Agora que a sua área de seleção está do jeito que você quer, você pode fazer o commit de suas mudanças. Lembre-se que tudo aquilo que ainda não foi selecionado — qualquer arquivo que você criou ou modificou que você não tenha rodado o comando *git add* desde que editou — não fará parte deste commit. Estes arquivos permanecerão como arquivos modificados em seu disco. Neste caso, a última vez que você rodou *git status*, viu que tudo estava selecionado, portanto você está pronto para fazer o commit de suas mudanças. O jeito mais simples é digitar *git commit*

```
git commit -m "Mensagem do seu Commit"
```

## Removendo Arquivos

Para remover um arquivo do Git, você tem que removê-lo dos arquivos que estão sendo monitorados (mais precisamente, removê-lo da sua área de seleção) e então fazer o commit. O comando *git rm* faz isso e também remove o arquivo do seu diretório para você não ver ele como arquivo não monitorado (untracked file) na próxima vez.

```
git rm nome-arquivo
```

## Adicionado Repositórios Remotos

Eu mencionei e dei algumas demonstrações de adição de repositórios remotos nas seções anteriores, mas aqui está como fazê-lo explicitamente. Para adicionar um novo repositório remoto no Git com um nome curto, para que você possa fazer referência facilmente, execute *git remote add [nomecurto] [url]*:

```
git remote add url-do-seu-repositório
```

## Pushing Para Seus Remotos

Quando o seu projeto estiver pronto para ser compartilhado, você tem que enviá-lo para a fonte. O comando para isso é simples: *git push [nome-remoto] [branch]*. Se você quer enviar o seu branch master para o servidor origin (novamente, clonando normalmente define estes dois nomes para você automaticamente), então você pode rodar o comando abaixo para enviar o seu trabalho para o servidor:

```
git push origin master
```

## Atualizando Seu Repositório

Quando queremos atualizar nosso arquivos com a última versão que se encontra em nosso remoto, que é muito utilizado quando temos mais de 1 pessoa trabalhando no projeto.

Para atualizar nosso repositório utilizamos o seguinte comando:

```
git pull 
```

## Branch e Merge

### Branch Básico 
Primeiro, digamos que você esteja trabalhando no seu projeto e já tem alguns commits 

![basicBranch](https://git-scm.com/figures/18333fig0310-tn.png)

Você decidiu que irá trabalhar na tarefa (issue) #53 do gerenciador de bugs ou tarefas que sua empresa usa. Para deixar claro, Git não é amarrado a nenhum gerenciador de tarefas em particular; mas já que a tarefa #53 tem um foco diferente, você criará um branch novo para trabalhar nele. Para criar um branch e mudar para ele ao mesmo tempo, você pode executar o comando *git checkout* com a opção *-b*:

```
git checkout -b iss53
```

Isso é um atalho para:

```
git branch iss53
git checkout iss53
```

![issueBranch](https://git-scm.com/figures/18333fig0311-tn.png)

Você trabalha no seu web site e faz alguns commits. Ao fazer isso o branch iss53 avançará, pois você fez o checkout dele, isto é, seu HEAD está apontando para ele.

```
git commit -m "adicionei um novo rodapé [issue 53]"
```

### Merge

Após o commit feito, devemos voltar para nossa branch *master* e escolher se vamos manter as alterações feitas, no caso eu quero manter. então farei um **merge**.

```
git checkout master
```

Então vamos *mesclar* nossas alterações com a branch principal, a **master**.

```
git merge iss53
```

Agora nossa branch **master** irá conter as modificações realizadas na branch **iss53**.

### Apagando uma Branch

Após termos feito nossa alteração, nossa branch não terá mais utilidade, então podemos exclui-la com o seguinte comando:

```
git branch -D iss53
```




