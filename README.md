# Inframe 🎬

**A Inframe** é uma aplicação móvel de gestão de vídeos e clientes desenvolvida em **Flutter**.
A aplicação funciona como um painel de controlo centralizado para produtores/editores de vídeo, permitindo gerir clientes, acompanhar o estado dos projetos de vídeo e obter insights inteligentes através de Inteligência Artificial.

## Funcionalidades Principais

### 1. Gestão de Clientes e Projetos (CRM & PM)

- **Sincronização em Tempo Real:** Todos os dados são guardados e lidos diretamente do **Notion**. A app atua como uma interface móvel para uma base de dados Notion.
- **Gestão de Clientes:** Criar, editar campos e eliminar clientes.
- **Tracking de Vídeos:** Criar, editar campos e acompanhar o estado de cada vídeo (*Por gravar, Por Editar, Editado, Revisto, Publicado*).
- **Links Rápidos:** Acesso direto aos ficheiros brutos (Drive/Dropbox) e editados (Drive/YouTube).

### 2. Assistente de Produção AI 🤖

- **Integração com Google Gemini (2.5 Flash):** Um assistente integrado que analisa a base de dados do Notion.
- **Resumos Semanais:** Gera mensagens automáticas sobre entregas nos próximos 7 dias.
- **Chat Contextual:** O utilizador pode fazer perguntas em linguagem natural (ex: *"Quem é o cliente do vídeo de receitas de francesinha?"*) e a IA responde com base nos dados reais do projeto.

## Arquitetura e Tecnologias

Este projeto segue uma arquitetura **Serverless**, utilizando o Notion como Backend-as-a-Service (BaaS).

- **Frontend:** Flutter (Dart) com Material 3.
- **Base de Dados:** Notion API (REST).
- **AI Engine:** Google Generative AI SDK (Gemini 2.5 Flash).
- **Segurança:** Gestão de chaves de API via variáveis de ambiente (`flutter_dotenv`).

## Configuração e Instalação

Para rodar este projeto localmente, siga os passos abaixo:

### 1. Pré-requisitos

- Flutter SDK instalado.
- Uma conta no Notion (com acesso à API).
- Uma chave de API do Google AI Studio (Gemini).

### 2. Instalação

```
# Clonar o repositório
git clone [https://github.com/[utilizador]/inframe.git](https://github.com/[utilizador]/inframe.git)

# Entrar na pasta
cd inframe

# Instalar dependências
flutter pub get

```

### 3. Configuração do Ambiente (.env)

Por razões de segurança, as chaves de API não estão no código. Crie um ficheiro chamado `.env` na raiz do projeto e preencha com as suas credenciais:

```
# Chave de Integração do Notion (Internal Integration Secret)
NOTION_TOKEN=secret_oteu_token_aqui...

# ID da Base de Dados de Clientes (ver secção Estrutura Notion)
NOTION_CLIENTS_DB_ID=id_da_tua_database...

# ID da Base de Dados de Vídeos
NOTION_VIDEOS_DB_ID=id_da_tua_database...

# Google AI Studio Key
GEMINI_API_KEY=AIzaSy...

```

### 4. Executar

```
flutter run
```

## 🗂️ Estrutura da Base de Dados (Notion)

Para a aplicação funcionar corretamente, é necessário criar duas bases de dados no Notion com as seguintes propriedades exatas (case-sensitive):
Formato: Propriedade - Tipo

**Base de Dados: Clientes**


 **Name** - Title
 
 **Mail** - Email
 
 **Phone** - Phone number
 
**Base de Dados: Vídeos**

 **Name** - Title
 
 **Number** - Number (Auto-increment ID)
 
 **Status** - Select (Opções: *Por gravar, Por Editar, Editado, Revisto, Publicado*)
 
 **Client** - Relation (Ligado à base de Clientes)
 
 **PublishDate** - Date
 
 **RawLink** - URL
 
 **EditedLink** - URL

## 📝 Autor

Desenvolvido por Daniel Brás no âmbito da cadeira de **Desenvolvimento para Dispositivos Móveis, Mestrade em Engenharia Informática - Computação Móvel.**
