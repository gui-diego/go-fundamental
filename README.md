# golang-study

![Go Version](https://img.shields.io/badge/Go-1.25-00ADD8?logo=go&logoColor=white)

Projeto de estudo em Go que demonstra fundamentos da linguagem, testes unitários, containerização com Docker e integração contínua via GitHub Actions.

## Sobre

Este repositório faz parte da minha jornada de aprendizado em Go. O objetivo é praticar conceitos básicos da linguagem — funções, pacotes, testes e build — além de configurar uma pipeline simples de CI/CD e uma imagem Docker.

## Funcionalidades

- Função `Somar` que recebe dois inteiros e retorna a soma
- Programa de linha de comando que demonstra o uso da função
- Teste unitário com o pacote `testing` da biblioteca padrão
- Dockerfile para executar a aplicação em container
- Pipeline no GitHub Actions que roda testes, executa o programa e publica a imagem no Docker Hub

## Stack

- **Go 1.25** — linguagem principal
- **testing** — testes unitários (stdlib)
- **Docker** — containerização
- **GitHub Actions** — integração contínua

## Estrutura do projeto

```
golang-study/
├── main.go                  # Função Somar e ponto de entrada
├── main_test.go             # Testes unitários
├── go.mod                   # Definição do módulo Go
├── Dockerfile               # Build e execução em container
└── .github/workflows/
    └── ci.yaml              # Pipeline de CI/CD
```

## Pré-requisitos

- [Go 1.25+](https://go.dev/dl/) instalado
- [Docker](https://www.docker.com/) (opcional, para rodar via container)

## Como executar

### Localmente

```bash
# Executar diretamente
go run main.go

# Compilar binário
go build -o main

# Executar o binário (Windows)
.\main.exe

# Executar o binário (Linux/macOS)
./main
```

Saída esperada:

```
2 + 2 = 4
```

### Testes

```bash
# Rodar todos os testes
go test

# Rodar com saída detalhada
go test -v
```

### Docker

```bash
# Build da imagem
docker build -t golang-study .

# Executar o container
docker run golang-study
```

## CI/CD

O workflow em `.github/workflows/ci.yaml` é disparado em pull requests para a branch `main` e executa:

1. `go test` — valida os testes unitários
2. `go run main.go` — executa o programa
3. Build e push da imagem Docker para `guidft/golang-study:latest`