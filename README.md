

# ProspAI

ProspAI é uma aplicação de inteligência artificial desenvolvida para otimizar estratégias de vendas através da análise de dados de clientes. A aplicação oferece uma API RESTful robusta e uma interface MVC baseada em Spring Boot e Thymeleaf, que facilita a navegação e a utilização dos recursos disponíveis.

## Índice
1. [Visão Geral do Projeto](#visão-geral-do-projeto)
2. [Arquitetura](#arquitetura)
3. [Tecnologias Utilizadas](#tecnologias-utilizadas)
4. [Pré-requisitos](#pré-requisitos)
5. [Instalação e Configuração](#instalação-e-configuração)
6. [Deploy no Azure](#deploy-no-azure)
   - [Deploy Usando IntelliJ IDEA](#deploy-usando-intellij-idea)
   - [Deploy Usando Eclipse](#deploy-usando-eclipse)
7. [Testes](#testes)
8. [Como Contribuir](#como-contribuir)
9. [Licença](#licença)

## Visão Geral do Projeto

ProspAI é uma plataforma que combina inteligência artificial e análise de dados para melhorar a tomada de decisão em vendas. Através da integração com fontes de dados externas, como Reclame Aqui e Procon, a aplicação consegue analisar feedbacks de clientes e oferecer predições e relatórios detalhados para otimização de estratégias de vendas.

## Arquitetura

A aplicação ProspAI é composta de duas partes principais:

- **API RESTful**: Construída utilizando Spring Boot, oferecendo endpoints para operações CRUD sobre clientes, feedbacks, predições, relatórios, estratégias de vendas, e usuários.
- **Interface MVC**: Baseada em Thymeleaf, a interface MVC proporciona uma experiência de usuário intuitiva e permite a visualização e manipulação dos dados de forma amigável.

A aplicação utiliza HATEOAS (Hypermedia as the Engine of Application State) para melhorar a navegabilidade e autodescoberta de recursos na API.

## Tecnologias Utilizadas

- Java 21
- Gradle
- Spring Boot
- Spring Data JPA com integração ao SQL Server
- Thymeleaf para a camada de visualização (MVC)
- HATEOAS para hiperlinks de recursos na API REST
- OpenAPI/Swagger para documentação da API
- JavaScript e Bootstrap para interatividade e design responsivo

## Pré-requisitos

Antes de executar ou fazer deploy da aplicação, certifique-se de que você tenha os seguintes requisitos instalados:

- **Java 21**: Certifique-se de que o Java 21 está instalado e configurado.
- **Gradle**: Para construir o projeto.
- **SQL Server**: A aplicação utiliza um banco de dados SQL Server.
- **Azure CLI**: Para comandos de linha de comando relacionados ao Azure.
- **IDE (IntelliJ IDEA ou Eclipse)**: Para desenvolvimento e deploy direto pela IDE.
- **Conta no Azure**: Necessária para deploy na nuvem.

## Instalação e Configuração

### 1. Clone o Repositório

```bash
git clone https://github.com/seu-usuario/prospai.git
cd prospai
```

### 2. Configure o Banco de Dados

Atualize as configurações do banco de dados no arquivo `src/main/resources/application.properties` conforme necessário:

```properties
spring.datasource.url=jdbc:sqlserver://<seu-servidor>:<porta>;databaseName=<nome-do-banco>
spring.datasource.username=<usuario>
spring.datasource.password=<senha>
```

### 3. Execute a Aplicação Localmente

- Compile e execute o projeto usando Gradle:

```bash
./gradlew bootRun
```

- Acesse a aplicação através do navegador: [http://localhost:8080](http://localhost:8080).

## Deploy no Azure

Esta seção explica como realizar o deploy da aplicação ProspAI no Azure diretamente usando IntelliJ IDEA ou Eclipse.

### Deploy Usando IntelliJ IDEA

1. **Instale o Azure Toolkit para IntelliJ:**
   - Vá para `File > Settings > Plugins`.
   - Procure por "Azure Toolkit for IntelliJ" e instale o plugin.
   - Reinicie o IntelliJ IDEA após a instalação.

2. **Logue no Azure pela IDE:**
   - Clique em `View > Tool Windows > Azure Explorer`.
   - Clique com o botão direito em `Azure` e selecione `Sign In`.
   - Escolha o método de login (dispositivo, diretório, etc.) e siga as instruções para autenticar.

3. **Configurar o Projeto para Deploy:**
   - No painel do Azure, clique com o botão direito em `App Services` e selecione `Create`.
   - Preencha as informações necessárias:
     - **Subscription**: Sua assinatura do Azure.
     - **Resource Group**: Selecione um existente ou crie um novo.
     - **App Name**: Nome único para sua aplicação.
     - **Runtime Stack**: Selecione `Java 21` e `Gradle`.
   - Clique em `Finish` para criar o Web App.

4. **Deploy da Aplicação:**
   - Clique com o botão direito no projeto na janela `Project`.
   - Selecione `Azure > Deploy to Azure Web App`.
   - Escolha a aplicação criada anteriormente e clique em `OK`.
   - O IntelliJ IDEA iniciará o processo de build e deploy da aplicação para o Azure.

5. **Verificar o Deploy:**
   - Após o deploy ser concluído, o console do IntelliJ mostrará um link para a aplicação em execução. Clique no link para verificar se a aplicação está funcionando corretamente.

### Deploy Usando Eclipse

1. **Instale o Azure Toolkit para Eclipse:**
   - Vá para `Help > Eclipse Marketplace`.
   - Procure por "Azure Toolkit for Eclipse" e instale o plugin.
   - Reinicie o Eclipse após a instalação.

2. **Logue no Azure pela IDE:**
   - No menu `Azure Explorer`, clique em `Sign In`.
   - Autentique-se utilizando seu método preferido.

3. **Configurar o Projeto para Deploy:**
   - Clique com o botão direito em `Azure Explorer > Web Apps` e selecione `Create`.
   - Configure os detalhes da sua aplicação (similar ao passo no IntelliJ):
     - **App Name**: Nome do seu aplicativo.
     - **Runtime**: `Java 21` com `Gradle`.
   - Clique em `Finish` para criar o Web App.

4. **Deploy da Aplicação:**
   - Clique com o botão direito no projeto no `Project Explorer`.
   - Selecione `Azure > Publish as Azure Web App`.
   - Selecione o Web App que você criou anteriormente e clique em `Deploy`.

5. **Verificar o Deploy:**
   - O Eclipse abrirá o link para sua aplicação ao finalizar o deploy. Acesse o link para verificar o status da aplicação.

## Testes

Após o deploy, você pode testar os endpoints da API acessando a documentação Swagger no Azure:

- **Ambiente na Nuvem (Azure)**: [https://prospai.azurewebsites.net/swagger-ui.html](https://prospai.azurewebsites.net/swagger-ui.html)

### Scripts JSON de CRUD para Testes

Certifique-se de que todos os testes estão documentados e que scripts de exemplo para operações CRUD estão incluídos. Aqui está um exemplo de um script JSON para criar um cliente:

```json
{
  "nome": "string",
  "email": "string",
  "telefone": "string",
  "segmentoMercado": "string",
  "scoreEngajamento": 0,
  "dataCriacao": "2024-09-16T22:46:35.511Z"
}
```

## Como Contribuir

1. **Fork o projeto.**
2. **Crie um branch de funcionalidade:**
   ```bash
   git checkout -b nova-funcionalidade
   ```
3. **Commit suas alterações:**
   ```bash
   git commit -m 'Adiciona nova funcionalidade'
   ```
4. **Envie o branch:**
   ```bash
   git push origin nova-funcionalidade
   ```
5. **Abra um Pull Request.**

## Licença

Este projeto é licenciado sob os termos da MIT License.

---

Este `README.md` oferece uma visão abrangente para que qualquer desenvolvedor possa configurar, executar, testar e fazer o deploy da aplicação **ProspAI** na Azure, diretamente de IntelliJ IDEA ou Eclipse, usando Gradle e Java 21. Certifique-se de testar todas as instruções antes de entregar para garantir que elas funcionem conforme o esperado.
