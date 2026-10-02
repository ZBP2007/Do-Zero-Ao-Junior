# 🚀 Fundamentos Locais do Git

Este guia contém um passo a passo detalhado e os comandos básicos do Git para o gerenciamento de controle de versão local.

## 📌 O que é o Git?

O **Git** é um sistema de controle de versão distribuído. Ele permite acompanhar o histórico de alterações nos seus arquivos, salvar pontos de restauração e entender o que mudou ao longo do tempo no seu projeto.

---

## 💻 Onde os comandos devem ser executados?

Todos os comandos mostrados neste guia devem ser digitados em uma **interface de linha de comando** (terminal).

* **Windows:** Abra o menu Iniciar e pesquise por **Git Bash** (instalado junto com o Git). Se preferir, você também pode usar o **Prompt de Comando (CMD)**, **PowerShell**, ou o terminal integrado do VS Code (`Ctrl + '`).
* **Linux / macOS:** Abra o aplicativo **Terminal** nativo do sistema ou o terminal integrado do seu editor de código.

---

## ⚙️ Passo 1: Configuração Inicial

Antes de usar o Git pela primeira vez, você precisa identificar quem você é. Essas informações serão associadas a cada salvamento (*commit*).

### Comandos:

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu.email@exemplo.com"
git config --list
```

### 🔍 Desmontando e entendendo os comandos:

* `git config --global user.name "Seu Nome"`
  * **`git`**: O programa principal que estamos chamando.
  * **`config`** *(configuração)*: Informa ao Git que queremos alterar ou ver alguma opção de configuração.
  * **`--global`** *(global/geral)*: Aplica essa configuração para **todos** os repositórios do seu usuário no computador.
  * **`user.name`** *(nome do usuário)*: A chave da propriedade que define o nome do autor dos salvamentos.
  * **`"Seu Nome"`**: O valor que você está definindo (seu nome ou apelido).

* `git config --global user.email "seu.email@exemplo.com"`
  * **`user.email`** *(e-mail do usuário)*: A chave da propriedade que define o e-mail de contato do autor.

* `git config --list`
  * **`--list`** *(lista)*: Exibe uma lista com todas as configurações ativas no momento.

---

## 📁 Passo 2: Criando a Pasta e Navegando pelo Terminal

Antes de iniciar o Git, usamos comandos básicos de navegação do próprio sistema operacional para preparar nossa pasta de trabalho.

### Comandos:

```bash
cd Desktop
mkdir meu-primeiro-projeto
cd meu-primeiro-projeto
pwd
```

### 🔍 Desmontando e entendendo os comandos:

* `cd Desktop`
  * **`cd`** *(change directory / mudar de diretório)*: Comando para navegar de uma pasta para outra.
  * **`Desktop`** *(Área de Trabalho)*: O nome do diretório para onde você quer ir.

* `mkdir meu-primeiro-projeto`
  * **`mkdir`** *(make directory / criar diretório)*: Comando para criar uma nova pasta.
  * **`meu-primeiro-projeto`**: O nome da nova pasta a ser criada.

* `cd meu-primeiro-projeto`
  * Entra na pasta recém-criada.

* `pwd`
  * **`pwd`** *(print working directory / imprimir diretório de trabalho)*: Exibe o caminho completo da pasta onde o terminal está posicionado no momento.

---

## 🚀 Passo 3: Inicializando o Repositório Git

Dentro da pasta do projeto, informe ao Git que ele deve começar a monitorar este diretório.

### Comando:

```bash
git init
```

### 🔍 Desmontando e entendendo o comando:

* **`git`**: Chama a ferramenta Git.
* **`init`** *(initialize / inicializar)*: Cria a estrutura oculta `.git` na pasta atual. A partir deste segundo, a pasta se torna um **repositório Git**.

---

## 🔄 Entendendo o Ciclo de Vida dos Arquivos

Antes de salvar um arquivo, entenda como o Git o enxerga em cada etapa:

```text
[ Working Directory ]  ---> (git add) --->  [ Staging Area ]  ---> (git commit) --->  [ Repository ]
   (Arquivos em vermelho)                  (Arquivos em verde)                   (Histórico Salvo)
```

1. **Working Directory (Diretório de Trabalho):** A pasta do seu computador onde você cria, edita ou deleta arquivos.
2. **Untracked (Não Monitorado):** Significa que um arquivo é totalmente novo e o Git ainda não rastreia as mudanças dele.
3. **Staging Area (Área de Preparação / Index):** A "zona de transição". É onde você coloca os arquivos que deseja incluir no próximo salvamento (*commit*).
4. **Repository (Repositório / Git History):** O banco de dados do Git contendo o histórico oficial e imutável dos seus *commits*.

---

## 🛠️ Passo 4: O Fluxo de Trabalho Passo a Passo

Tudo o que for feito nesta seção deve ser executado direto no **Git Bash** (ou terminal de sua preferência) com o terminal apontando para dentro da pasta do projeto.

### 1. Criar um arquivo de teste

```bash
echo "Meu primeiro arquivo no Git" > exemplo.txt
```

* **`echo`** *(ecoar/repetir)*: Imprime o texto informado.
* **`>`** *(redirecionamento)*: Pega a saída do texto e a grava dentro do arquivo `exemplo.txt` (criando o arquivo se ele não existir).

---

### 2. Verificar o status do projeto (O que é Untracked e Arquivo em Vermelho)

```bash
git status
```

### 🔍 Desmontando e entendendo o comando:

* **`git`**: Chama o Git.
* **`status`** *(estado/situação)*: Mostra a situação atual da sua pasta de trabalho (quais arquivos foram alterados, quais estão na Staging Area e quais são novos).

**O que você verá:** O arquivo `exemplo.txt` aparecerá **em vermelho**, categorizado como **Untracked** (Não monitorado).

---

### 3. Adicionar o arquivo à Staging Area (O que é a Staging Area e Arquivo em Verde)

```bash
git add exemplo.txt
# OU para adicionar tudo de uma vez:
git add .
```

### 🔍 Desmontando e entendendo o comando:

* **`git`**: Chama o Git.
* **`add`** *(adicionar)*: Move as alterações da sua pasta de trabalho para a Staging Area (zona de preparação).
* **`exemplo.txt`**: O arquivo específico a ser preparado.
* **`.`** *(ponto)*: No terminal, o ponto representa o **diretório atual completo**. Portanto, `git add .` significa "adicione todos os arquivos e modificações da pasta atual".

**O que você verá ao rodar `git status` novamente:** O arquivo `exemplo.txt` passará a aparecer **em verde**, indicando que está pronto para ser salvo.

---

### 4. Salvar as alterações (Commit)

```bash
git commit -m "Criando o arquivo de exemplo do projeto"
```

### 🔍 Desmontando e entendendo o comando:

* **`git`**: Chama o Git.
* **`commit`** *(comprometer/confirmar/gravar)*: Registra uma foto (snapshot) do estado atual dos arquivos que estavam na Staging Area, gravando permanente no histórico.
* **`-m`** *(message / mensagem)*: Flag (opção) que indica que você vai escrever a mensagem descritiva do commit diretamente na linha de comando.
* **`"Criando o arquivo de exemplo do projeto"`**: A mensagem explicativa do que foi alterado nesse salvamento.

---

## 📜 Passo 5: Visualizando o Histórico de Alterações

```bash
git log
git log --oneline
```

### 🔍 Desmontando e entendendo os comandos:

* `git log`
  * **`git`**: Chama o Git.
  * **`log`** *(diário/registro de bordo)*: Exibe a lista cronológica de todos os commits realizados no repositório.

* `git log --oneline`
  * **`--oneline`** *(uma linha)*: Formata a saída do registro para que cada commit ocupe apenas **uma única linha**, facilitando a leitura rápida.

---

## 💡 Resumo e Tradução das Palavras-Chave

| Palavra em Inglês | Tradução Direta | Significado no Git / Terminal |
| :--- | :--- | :--- |
| **config** | Configuração | Gerencia opções do sistema. |
| **global** | Global / Geral | Aplica a regra a todo o seu computador. |
| **init** *(initialize)* | Inicializar | Começa o monitoramento de uma pasta. |
| **status** | Estado / Situação | Exibe o momento atual dos arquivos. |
| **add** | Adicionar | Mova modificações para a área de preparação. |
| **commit** | Confirmar / Registrar | Grava um ponto na história do código. |
| **log** | Registro de bordo | Mostra o histórico de commits efetuados. |
| **untracked** | Não rastreado | Arquivo novo que o Git ainda não conhece. |
| **staging area** | Área de preparação | A "zona de transição" antes do commit. |

---

## 📝 OBSERVAÇÃO IMPORTANTE: Interface Gráfica vs. Terminal

> **Nota:** Todos os passos explicados neste guia utilizam a linha de comando (terminal/Git Bash). Embora existam interfaces gráficas (GUIs) e extensões no VS Code que facilitam a criação de pastas e execução de comandos Git, **praticar diretamente pelo terminal é fundamental por diversos motivos:**
>
> 1. **Compreensão Profunda do Funcionamento:** Executar os comandos manualmente força o desenvolvedor a entender *o que* realmente está acontecendo por baixo dos panos em cada etapa (diferença entre Working Directory, Staging Area e Repositório) em vez de apenas clicar em botões abstratos.
> 2. **Padrão na Indústria e Flexibilidade:** O terminal é universal. Se você precisar trabalhar em servidores remotos (via SSH), pipelines de integração contínua (CI/CD) ou máquinas onde não há interface gráfica disponível, o conhecimento dos comandos de terminal será a única forma de operar.
> 3. **Velocidade e Eficiência:** Desenvolvedores acostumados com o terminal executam fluxos completos de Git muito mais rápido digitando os comandos do que navegando com o mouse por menus e botões de editores.
> 4. **Diagnóstico e Resolução de Erros:** Quando ocorrem conflitos ou problemas mais complexos no código, a interface gráfica muitas vezes oculta detalhes essenciais. O terminal exibe mensagens de erro completas e possibilita um controle muito mais preciso para reparar o repositório.
>
> **Alternativa do Dia a Dia:**  
> Após fixar bem o funcionamento dos comandos no terminal, você pode perfeitamente mesclar sua rotina criando pastas via sistema operacional/VS Code e utilizando a aba de **Controle de Origem (Source Control)** no VS Code (`Ctrl + Shift + G`) para realizar os commits de forma visual.
