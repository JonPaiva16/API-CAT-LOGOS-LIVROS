# 📚 Catálogo de Livros — API REST

API REST desenvolvida com **FastAPI** para gerenciamento de um catálogo de livros.

O projeto foi desenvolvido aplicando conceitos de **Engenharia de Software**, utilizando separação de responsabilidades entre rotas, serviços e repositórios, além de testes automatizados, integração com uma API externa, containerização com Docker e pipeline de CI/CD.

## 📌 Funcionalidades

- Cadastro e consulta de livros
- Validação das informações dos livros
- Verificação de ISBN duplicado
- Validação do ano de publicação
- Consulta à **Open Library** para complementar e validar informações do livro
- API documentada automaticamente pelo Swagger
- Testes automatizados
- Execução através de Docker
- Pipeline de integração contínua com GitHub Actions
- Deploy em ambiente AWS

## 🏗️ Arquitetura

O projeto utiliza uma arquitetura organizada em camadas:

```text
Rotas
  ↓
Services
  ↓
Repository
  ↓
Dados
```

### Rotas

Responsáveis por receber as requisições HTTP e encaminhá-las para os serviços.

### Services

Contêm as regras de negócio da aplicação, como:

- impedir ISBN duplicado;
- impedir cadastro de livros com ano futuro;
- consultar a Open Library.

### Repository

Responsável pelo acesso e gerenciamento dos dados dos livros.

### Cliente Open Library

Responsável pela comunicação com a API externa da Open Library.

## 🛠️ Tecnologias

| Tecnologia | Utilização |
|---|---|
| **Python** | Linguagem principal |
| **FastAPI** | Desenvolvimento da API REST |
| **Pydantic** | Modelagem e validação dos dados |
| **Pytest** | Testes automatizados |
| **Docker** | Containerização da aplicação |
| **GitHub Actions** | Integração contínua e deploy |
| **AWS** | Infraestrutura e deploy |
| **Open Library API** | Consulta de informações sobre livros |

## 📂 Estrutura

```text
projeto-final-es-main/
│
├── app/
│   ├── main.py
│   ├── models.py
│   ├── repository.py
│   ├── services/
│   │   └── livro.py
│   └── clients/
│       └── open_library.py
│
├── tests/
├── Dockerfile
├── infra.yml
├── requirements.txt
└── .github/
    └── workflows/
```

## 🚀 Executando localmente

### 1. Criar ambiente virtual

```bash
python -m venv .venv
```

### 2. Ativar

**Windows:**

```bash
.venv\Scripts\activate
```

**Linux/Mac:**

```bash
source .venv/bin/activate
```

### 3. Instalar dependências

```bash
pip install -r requirements.txt
```

### 4. Executar

```bash
uvicorn main:app --reload
```

A API estará disponível em:

```text
http://localhost:8000
```

Documentação Swagger:

```text
http://localhost:8000/docs
```

## 🧪 Testes

Os testes são executados utilizando **pytest**:

```bash
pytest --cov=app --cov-report=term-missing
```

As chamadas para a Open Library são simuladas nos testes, permitindo que eles sejam executados sem depender de uma conexão com a API externa.

## 🐳 Docker

A aplicação possui um `Dockerfile` para execução em container.

```bash
docker build -t catalogo-livros .
docker run -p 8000:8000 catalogo-livros
```

## ⚙️ Integração Contínua

O projeto utiliza **GitHub Actions** para executar automaticamente:

- Pylint para análise do código;
- Pytest para execução dos testes;
- verificação de cobertura dos testes.

## ☁️ Deploy

O projeto possui infraestrutura definida em **AWS CloudFormation**, permitindo criar uma instância EC2 para executar a API através de Docker.

A infraestrutura também utiliza Elastic IP para manter um endereço público estável para a aplicação.

## 🎯 Objetivo do projeto

O projeto teve como objetivo aplicar na prática conceitos de **Engenharia de Software e desenvolvimento de APIs**, trabalhando com arquitetura em camadas, regras de negócio, testes, integração com serviços externos, containerização, integração contínua e deploy em nuvem.
