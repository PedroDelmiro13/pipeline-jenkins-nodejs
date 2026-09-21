# Pipeline Jenkins Node.js

Projeto Node.js utilizado para demonstrar um pipeline de CI/CD com Jenkins.

## Requisitos

* Node.js
* npm

## Instalação

Clone o repositório:

```bash
git clone <URL_DO_REPOSITORIO>
cd pipeline-jenkins-nodejs
```

Instale as dependências:

```bash
npm install
```

## Build

Execute o build:

```bash
npm run build
```

O comando apenas simula uma etapa de build e exibe uma mensagem de sucesso.

## Testes

Execute os testes automatizados:

```bash
npm test
```

Os testes utilizam **Jest** e **Supertest**.

## Execução

Inicie a aplicação:

```bash
npm start
```

O servidor será iniciado pelo arquivo `server.js`.

## Comandos disponíveis

```bash
npm install    # Instala as dependências
npm run build  # Executa o build
npm test       # Executa os testes
npm start      # Inicia a aplicação
```

## Jenkins

O projeto pode ser utilizado em um pipeline executando as etapas:

```text
Checkout → npm install → npm run build → npm test → npm start
```

## GitHub Actions

O projeto também possui uma pipeline utilizando GitHub Actions.

O workflow executa as seguintes etapas:

1. Checkout do código
2. Configuração do Node.js
3. Instalação das dependências
4. Build da aplicação
5. Execução dos testes
6. Análise SAST com Semgrep
7. Inicialização da aplicação
8. Análise DAST com OWASP ZAP

### SAST - Semgrep

O Semgrep realiza uma análise estática do código-fonte.

Essa etapa verifica possíveis vulnerabilidades e padrões inseguros
sem precisar executar a aplicação.

Foram utilizadas regras de segurança e recomendações relacionadas
ao OWASP Top 10.

### DAST - OWASP ZAP

O OWASP ZAP realiza uma análise dinâmica da aplicação.

Diferente do SAST, o DAST é executado com a aplicação em funcionamento,
enviando requisições para identificar possíveis vulnerabilidades
durante a execução.

### Fluxo da pipeline

```text
Checkout
   ↓
Setup Node
   ↓
Instalação das dependências
   ↓
Build
   ↓
Testes
   ↓
SAST - Semgrep
   ↓
Inicialização da aplicação
   ↓
DAST - OWASP ZAP