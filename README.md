# OneClinic

**Sistema SaaS de Gestão Inteligente para Clínicas de Estética**

> Projeto individual — Engenharia de Software  
> Status: Em desenvolvimento  
> Meta atual: integração completa entre Frontend e Backend e conclusão do módulo de Agenda até novembro de 2026.

---

# 1. Sobre o Projeto

O **OneClinic** é uma plataforma web SaaS voltada à gestão integrada de clínicas de estética, com foco em organização operacional, segurança dos dados, controle financeiro, estoque, clientes, profissionais e agendamentos.

A proposta é substituir processos fragmentados, como planilhas, agendas manuais e registros descentralizados, por uma única plataforma.

O sistema foi projetado com arquitetura **multi-tenant**, permitindo que diferentes clínicas utilizem a mesma aplicação com isolamento lógico dos dados.

### Principais objetivos

- Centralizar os dados e processos da clínica.
- Reduzir erros operacionais e retrabalho.
- Facilitar o gerenciamento de clientes e profissionais.
- Automatizar e organizar a agenda.
- Controlar planos, pacotes, cupons, estoque e financeiro.
- Permitir evolução futura para um produto SaaS escalável.
- Aplicar boas práticas de segurança e proteção de dados.

---

# 2. Projeto Individual

O OneClinic está sendo desenvolvido individualmente por:

**Wedley Silva Schmoeller**

Responsável pelo planejamento, arquitetura, documentação, desenvolvimento, integração, testes e evolução do sistema.

---

# 3. Status Atual

O projeto possui uma parte importante da interface já desenvolvida.

### Já concluído / disponível

- [x] Estrutura inicial do projeto
- [x] Telas principais do Frontend
- [x] Interface de autenticação
- [x] Tela de login
- [x] Cadastro de usuários
- [x] Controle inicial de usuários e níveis de acesso
- [x] Estrutura visual dos módulos
- [x] Modelagem inicial do sistema
- [x] Documentação de requisitos
- [x] Documentação de regras de negócio
- [x] Documento de visão
- [x] Mapa de riscos
- [x] Modelagem arquitetural C4
- [x] Definição da stack tecnológica

### Próxima etapa principal

A prioridade atual é **integrar o Backend Django ao Frontend Vue.js**, substituindo os dados/mockups existentes por dados reais provenientes da API.

---

# 4. Objetivo da Próxima Fase

A próxima fase do projeto não consiste em reconstruir as telas.

As interfaces já existentes devem ser aproveitadas.

O foco será:

1. Estruturar e finalizar as APIs necessárias no Backend.
2. Conectar o Frontend às APIs.
3. Implementar autenticação real entre Frontend e Backend.
4. Persistir os dados no PostgreSQL.
5. Implementar as regras de negócio.
6. Criar validações no Backend.
7. Integrar os módulos existentes.
8. Testar os fluxos completos.
9. Priorizar a conclusão do módulo de Agenda até novembro de 2026.

---

# 5. Stack Tecnológica

## Frontend

- Vue.js 3
- Vite
- PrimeVue
- JavaScript/TypeScript conforme a implementação do projeto
- Node.js
- NPM

Responsabilidades:

- Interface do usuário
- Navegação
- Formulários
- Validações de experiência do usuário
- Consumo da API
- Exibição dos dados
- Controle visual de permissões

## Backend

- Python
- Django
- Django REST Framework
- API REST
- Arquitetura em camadas

Responsabilidades:

- Regras de negócio
- Autenticação
- Autorização
- Validação dos dados
- Controle de acesso
- Persistência
- Integrações
- Auditoria

## Banco de Dados

- PostgreSQL

Recursos utilizados/propostos:

- UUID
- JSONB
- Constraints
- Relacionamentos
- Índices
- Controle de integridade

## Autenticação

A autenticação possui estrutura de cadastro e login de usuários.

A próxima etapa é conectar essa autenticação ao fluxo completo:

```text
Frontend Vue.js
      ↓
API Django REST
      ↓
Autenticação
      ↓
PostgreSQL
```

O sistema também prevê proteção de sessão e controle de acesso por nível de usuário.

---

# 6. Pré-requisitos

Antes de executar o projeto, é necessário possuir as seguintes ferramentas instaladas:

| Tecnologia | Versão recomendada |
|---|---|
| Git | 2.x ou superior |
| Node.js | 18+ |
| NPM | compatível com Node.js |
| Python | 3.11+ |
| PostgreSQL | 14+ |
| Vue.js | 3 |
| Django | definido no `requirements.txt` |

Recomenda-se utilizar:

- VS Code
- PostgreSQL local ou Supabase
- Git
- Terminal/PowerShell

Para verificar as instalações:

```bash
git --version
node --version
npm --version
python --version
psql --version
```

No Windows, caso `python` não funcione:

```bash
py --version
```

---

# 7. Clonando o Projeto

Clone o repositório:

```bash
git clone <URL_DO_REPOSITORIO>
```

Entre na pasta:

```bash
cd OneClinic
```

Caso o projeto possua Frontend e Backend em diretórios separados, a estrutura esperada será semelhante a:

```text
OneClinic/
│
├── frontend/
├── backend/
├── README.md
└── .gitignore
```

A estrutura real do projeto deve ser mantida conforme o repositório.

---

# 8. Configuração do PostgreSQL

O OneClinic utiliza PostgreSQL como banco de dados.

É possível utilizar:

- PostgreSQL instalado localmente;
- Supabase;
- Outro servidor PostgreSQL compatível.

## 8.1 Criando o banco localmente

Após instalar o PostgreSQL, crie um banco:

```sql
CREATE DATABASE oneclinic;
```

Caso seja necessário criar um usuário específico:

```sql
CREATE USER oneclinic_user WITH PASSWORD 'sua_senha';
```

Conceda acesso ao banco:

```sql
GRANT ALL PRIVILEGES ON DATABASE oneclinic TO oneclinic_user;
```

> Os comandos podem variar de acordo com a configuração da instalação do PostgreSQL.

---

# 9. Configuração das Variáveis de Ambiente

As informações sensíveis não devem ser armazenadas diretamente no código-fonte.

O Backend deve utilizar um arquivo `.env`.

Exemplo:

```env
DEBUG=True

SECRET_KEY=sua-chave-secreta

DB_NAME=oneclinic
DB_USER=oneclinic_user
DB_PASSWORD=sua_senha
DB_HOST=localhost
DB_PORT=5432

ALLOWED_HOSTS=localhost,127.0.0.1

CORS_ALLOWED_ORIGINS=http://localhost:5173
```

Caso esteja utilizando Supabase, substitua os dados de conexão pelos fornecidos pelo projeto.

### Importante

O arquivo `.env` não deve ser enviado para o Git.

No `.gitignore`:

```gitignore
.env
.env.*
```

---

# 10. Instalação do Backend Django

Entre na pasta do Backend:

```bash
cd backend
```

## 10.1 Criar ambiente virtual

No Windows:

```bash
python -m venv venv
```

Ou:

```bash
py -m venv venv
```

No Linux/macOS:

```bash
python3 -m venv venv
```

## 10.2 Ativar o ambiente virtual

### Windows PowerShell

```powershell
.\venv\Scripts\Activate.ps1
```

### Windows CMD

```cmd
venv\Scripts\activate
```

### Linux/macOS

```bash
source venv/bin/activate
```

Após ativar, o terminal deverá apresentar algo semelhante a:

```text
(venv)
```

---

# 11. Instalar Dependências do Django

Com o ambiente virtual ativado:

```bash
python -m pip install --upgrade pip
```

Depois:

```bash
pip install -r requirements.txt
```

Caso o projeto ainda não possua um `requirements.txt`, as principais dependências podem ser instaladas com:

```bash
pip install django
pip install djangorestframework
pip install psycopg2-binary
pip install python-dotenv
pip install django-cors-headers
```

Depois, recomenda-se gerar o arquivo:

```bash
pip freeze > requirements.txt
```

---

# 12. Configuração do Django

O Backend deverá possuir uma estrutura semelhante a:

```text
backend/
│
├── manage.py
│
├── config/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
├── apps/
│   ├── accounts/
│   ├── clientes/
│   ├── agenda/
│   ├── planos/
│   ├── estoque/
│   ├── financeiro/
│   └── notificacoes/
│
├── requirements.txt
├── .env
└── venv/
```

A estrutura pode variar conforme a implementação atual.

---

# 13. Executar as Migrations

Ainda dentro da pasta `backend` e com o ambiente virtual ativado:

```bash
python manage.py makemigrations
```

Depois:

```bash
python manage.py migrate
```

As migrations irão criar e atualizar as tabelas do banco PostgreSQL de acordo com os modelos Django.

---

# 14. Criar Superusuário

Para acessar o Django Admin:

```bash
python manage.py createsuperuser
```

O terminal solicitará:

```text
Username:
Email:
Password:
Password (again):
```

Depois será possível acessar:

```text
http://127.0.0.1:8000/admin/
```

---

# 15. Executar o Backend

Com o ambiente virtual ativado:

```bash
python manage.py runserver
```

O Backend estará disponível normalmente em:

```text
http://127.0.0.1:8000/
```

A API poderá ser acessada através dos endpoints definidos no projeto.

Exemplo:

```text
http://127.0.0.1:8000/api/
```

---

# 16. Instalação do Frontend Vue.js

Abra outro terminal.

Acesse a pasta do Frontend:

```bash
cd frontend
```

Instale as dependências:

```bash
npm install
```

---

# 17. Configuração do Frontend

O Frontend deve possuir uma variável indicando a URL da API Django.

Exemplo de `.env`:

```env
VITE_API_URL=http://127.0.0.1:8000/api
```

Caso a aplicação utilize outra variável ou estrutura de configuração, deve-se seguir o padrão já existente no projeto.

Exemplo de uso:

```javascript
const API_URL = import.meta.env.VITE_API_URL;
```

---

# 18. Executar o Frontend

Dentro da pasta `frontend`:

```bash
npm run dev
```

O Vite deverá informar algo semelhante a:

```text
Local: http://localhost:5173/
```

Acesse:

```text
http://localhost:5173
```

---

# 19. Executando Frontend e Backend

Para executar o sistema completo, é necessário manter **dois terminais abertos**.

### Terminal 1 — Backend

```bash
cd backend
```

Ative o ambiente virtual:

```powershell
.\venv\Scripts\Activate.ps1
```

Execute:

```bash
python manage.py runserver
```

Backend:

```text
http://127.0.0.1:8000
```

### Terminal 2 — Frontend

```bash
cd frontend
```

Execute:

```bash
npm run dev
```

Frontend:

```text
http://localhost:5173
```

---

# 20. Fluxo de Execução

```text
                    ┌──────────────────┐
                    │      Usuário     │
                    └────────┬─────────┘
                             │
                             ↓
                    ┌──────────────────┐
                    │   Vue.js + Vite  │
                    │ localhost:5173   │
                    └────────┬─────────┘
                             │
                         HTTP/REST
                             │
                             ↓
                    ┌──────────────────┐
                    │ Django REST API  │
                    │ 127.0.0.1:8000  │
                    └────────┬─────────┘
                             │
                             ↓
                    ┌──────────────────┐
                    │    PostgreSQL    │
                    │      :5432       │
                    └──────────────────┘
```

---

# 21. Integração Frontend + Backend

Esta é a principal atividade técnica da próxima etapa.

## Estado atual

As telas do Frontend já estão prontas.

O objetivo é conectar essas telas às APIs reais.

### Fluxo esperado

```text
Usuário
   ↓
Tela Vue.js
   ↓
Service / API Client
   ↓
Django REST API
   ↓
Regra de negócio
   ↓
PostgreSQL
   ↓
Resposta JSON
   ↓
Vue.js
   ↓
Interface atualizada
```

---

# 22. Organização Recomendada da Integração

No Frontend, criar uma camada responsável pelas chamadas da API.

Exemplo conceitual:

```text
frontend/
└── src/
    ├── api/
    │   ├── auth.ts
    │   ├── clientes.ts
    │   ├── agenda.ts
    │   ├── planos.ts
    │   ├── estoque.ts
    │   └── financeiro.ts
    │
    ├── components/
    ├── pages/
    ├── layouts/
    ├── router/
    ├── stores/
    └── services/
```

No Backend:

```text
backend/
├── apps/
│   ├── accounts/
│   ├── clientes/
│   ├── agenda/
│   ├── planos/
│   ├── estoque/
│   ├── financeiro/
│   └── notificacoes/
│
├── config/
├── manage.py
├── requirements.txt
└── .env
```

A estrutura real deve seguir o que já foi implementado no projeto, evitando reorganização desnecessária.

---

# 23. API

A API deve possuir endpoints organizados por domínio.

Exemplo:

```text
/api/auth/
/api/clientes/
/api/agendamentos/
/api/profissionais/
/api/planos/
/api/pacotes/
/api/cupons/
/api/produtos/
/api/estoque/
/api/pagamentos/
/api/financeiro/
/api/notificacoes/
```

Exemplos de operações:

```http
GET    /api/clientes/
POST   /api/clientes/
GET    /api/clientes/{id}/
PUT    /api/clientes/{id}/
PATCH  /api/clientes/{id}/
```

Agenda:

```http
GET    /api/agendamentos/
POST   /api/agendamentos/
GET    /api/agendamentos/{id}/
PUT    /api/agendamentos/{id}/
DELETE /api/agendamentos/{id}/
```

---

# 24. Multi-tenancy

O sistema foi projetado para permitir múltiplas clínicas.

O isolamento deve ser realizado através do identificador da clínica:

```text
clinica_id
```

As operações do sistema devem considerar o tenant autenticado.

Exemplo:

```text
Usuário
   ↓
Clínica autenticada
   ↓
API
   ↓
Filtro por clinica_id
   ↓
Dados daquela clínica
```

Nenhum usuário deve conseguir consultar ou alterar dados pertencentes a outra clínica.

---

# 25. Níveis de Acesso

O sistema possui três níveis principais:

| Nível | Função |
|---|---|
| Admin | Gestão completa da clínica |
| Secretário | Operação administrativa |
| Profissional | Atendimento e agenda própria |

### Admin

Pode:

- Gerenciar colaboradores
- Gerenciar clientes
- Gerenciar agenda
- Gerenciar planos e pacotes
- Gerenciar estoque
- Gerenciar financeiro
- Visualizar relatórios
- Alterar configurações

### Secretário

Pode:

- Gerenciar clientes
- Gerenciar agenda
- Gerenciar estoque
- Operar financeiro básico
- Realizar operações administrativas

### Profissional

Pode:

- Visualizar sua agenda
- Consultar clientes relacionados aos seus atendimentos
- Registrar atendimentos
- Registrar consumo de materiais

As permissões devem ser validadas **também no Backend**, e não somente no Frontend.

---

# 26. Módulos do Sistema

## 26.1 Autenticação

### Situação

**Já possui cadastro e login de usuários.**

### Próximas tarefas

- [ ] Integrar login Frontend → Backend
- [ ] Persistir sessão
- [ ] Proteger rotas da API
- [ ] Implementar autorização por nível
- [ ] Integrar logout
- [ ] Validar sessão expirada
- [ ] Garantir proteção das rotas do Frontend
- [ ] Testar acesso indevido

---

## 26.2 Clientes

Funcionalidades previstas:

- [ ] Cadastro
- [ ] Edição
- [ ] Inativação
- [ ] Consulta
- [ ] Busca
- [ ] Filtros
- [ ] Paginação
- [ ] Histórico
- [ ] Crédito acumulado

Campos principais:

```text
id
clinica_id
nome
telefone
email
cpf
endereco
credito
data_cadastro
```

---

## 26.3 Agenda — PRIORIDADE

A Agenda é o principal objetivo de conclusão da fase atual.

### Objetivo

Permitir que a clínica visualize e gerencie seus atendimentos de maneira organizada, evitando conflitos de horários.

### Funcionalidades

- [ ] Visualização diária
- [ ] Visualização semanal
- [ ] Filtro por profissional
- [ ] Cadastro de agendamento
- [ ] Edição de agendamento
- [ ] Cancelamento
- [ ] Motivo de cancelamento
- [ ] Confirmação
- [ ] Conclusão
- [ ] Controle de horários
- [ ] Validação de conflito
- [ ] Associação cliente/profissional
- [ ] Associação com plano/pacote
- [ ] Controle de pagamento
- [ ] Observações
- [ ] Produtos utilizados
- [ ] Baixa de estoque ao concluir atendimento

### Dados principais

```text
agendamento
├── cliente
├── profissional
├── data
├── hora_inicio
├── hora_fim
├── tipo
├── status
├── valor
├── pagamento
└── observações
```

### Regra fundamental

O Backend deve impedir que um profissional possua dois agendamentos conflitantes.

A validação deve existir no Backend e, quando possível, também ser reforçada pelo banco de dados.

---

## 26.4 Planos e Pacotes

Funcionalidades:

- [ ] Cadastro de planos
- [ ] Cadastro de pacotes
- [ ] Definição de preço
- [ ] Definição de sessões
- [ ] Controle de validade
- [ ] Controle de sessões restantes
- [ ] Consumo de sessão
- [ ] Status do plano
- [ ] Histórico de utilização

---

## 26.5 Cupons

Funcionalidades:

- [ ] Cadastro
- [ ] Código único
- [ ] Desconto percentual
- [ ] Desconto fixo
- [ ] Data de validade
- [ ] Limite de utilização
- [ ] Controle de uso por cliente
- [ ] Histórico de utilização

---

## 26.6 Estoque

Funcionalidades:

- [ ] Cadastro de produtos
- [ ] Edição
- [ ] Inativação
- [ ] Entrada
- [ ] Saída
- [ ] Uso em atendimento
- [ ] Venda
- [ ] Perda/avaria
- [ ] Estoque mínimo
- [ ] Alertas
- [ ] Histórico de movimentações

### Regra

> O estoque não deve ficar negativo.

---

## 26.7 Financeiro

Funcionalidades:

- [ ] Registro de pagamentos
- [ ] Métodos de pagamento
- [ ] Parcelamento
- [ ] Descontos
- [ ] Controle de parcelas
- [ ] Inadimplência
- [ ] Caixa
- [ ] Entradas
- [ ] Saídas
- [ ] Fechamento
- [ ] Recibos

---

## 26.8 Notificações

Canais planejados:

- WhatsApp
- E-mail
- SMS

Funcionalidades:

- [ ] Lembretes de agendamento
- [ ] Cobranças
- [ ] Avisos
- [ ] Promoções
- [ ] Histórico de mensagens
- [ ] Registro de status de envio

---

## 26.9 Dashboard

### Admin

- [ ] Receita
- [ ] Sessões
- [ ] Estoque crítico
- [ ] Inadimplência
- [ ] Caixa
- [ ] Indicadores

### Secretário

- [ ] Agenda do dia
- [ ] Confirmações
- [ ] Estoque crítico

### Profissional

- [ ] Próximos atendimentos
- [ ] Agenda
- [ ] Sessões realizadas

---

## 26.10 Relatórios

- [ ] Financeiro
- [ ] Clientes
- [ ] Estoque
- [ ] Profissionais
- [ ] Agenda
- [ ] Caixa
- [ ] Inadimplência
- [ ] Exportação PDF
- [ ] Exportação CSV

---

# 27. Segurança

O projeto considera a natureza sensível dos dados tratados.

### Requisitos

- [ ] Hash seguro de senhas
- [ ] Autenticação
- [ ] Autorização
- [ ] Proteção das APIs
- [ ] Isolamento por `clinica_id`
- [ ] Validação de entrada
- [ ] Proteção contra acesso indevido
- [ ] Controle de sessão
- [ ] Logs de auditoria
- [ ] Backup
- [ ] Tratamento seguro de erros

### Referências

- LGPD
- OWASP Top 10
- Boas práticas de segurança de aplicações web
- Princípios de segurança da informação

---

# 28. Regras de Negócio Prioritárias

### Usuários

- E-mail deve ser único dentro da clínica.
- Usuários só podem executar operações autorizadas.
- Admin não pode excluir a própria conta.

### Clientes

- Nome é obrigatório.
- Clientes devem ser preferencialmente inativados em vez de removidos definitivamente.
- Histórico deve ser preservado.

### Agenda

- Cliente é obrigatório.
- Profissional é obrigatório.
- Data e horário são obrigatórios.
- Não pode haver conflito de horário.
- Cancelamento deve possuir motivo.
- Atendimento concluído pode gerar movimentação financeira e de estoque.

### Estoque

- Não pode haver estoque negativo.
- Toda movimentação deve ser registrada.

### Financeiro

- Pagamentos devem possuir cliente.
- Parcelas devem possuir vencimento.
- Débitos vencidos devem ser identificáveis.

---

# 29. Testes

A integração deverá ser acompanhada por testes.

## Backend

- [ ] Testes de autenticação
- [ ] Testes de autorização
- [ ] Testes de clientes
- [ ] Testes de agenda
- [ ] Testes de conflito de horário
- [ ] Testes de financeiro
- [ ] Testes de estoque

## Frontend

- [ ] Testes de formulários
- [ ] Testes de navegação
- [ ] Testes de permissões
- [ ] Testes de integração com API
- [ ] Testes dos principais fluxos

### Teste prioritário da Agenda

```text
Criar cliente
      ↓
Criar profissional
      ↓
Criar agendamento
      ↓
Validar disponibilidade
      ↓
Salvar
      ↓
Exibir na agenda
      ↓
Editar
      ↓
Confirmar
      ↓
Concluir
      ↓
Atualizar financeiro/estoque
```

---

# 30. Solução de Problemas

## Backend não inicia

Verifique se o ambiente virtual está ativado:

```bash
.\venv\Scripts\Activate.ps1
```

Depois:

```bash
python manage.py runserver
```

## Erro de banco de dados

Verifique:

```env
DB_NAME=
DB_USER=
DB_PASSWORD=
DB_HOST=
DB_PORT=
```

Teste se o PostgreSQL está em execução.

Depois execute:

```bash
python manage.py migrate
```

## Erro `No module named ...`

Com o ambiente virtual ativado:

```bash
pip install -r requirements.txt
```

Caso o pacote não esteja no arquivo:

```bash
pip install nome-do-pacote
```

E atualize:

```bash
pip freeze > requirements.txt
```

## Erro no `npm install`

No Windows PowerShell:

```powershell
Remove-Item -Recurse -Force node_modules
```

Depois:

```bash
npm install
```

## Frontend não consegue acessar o Backend

Verifique se o Django está rodando:

```text
http://127.0.0.1:8000
```

Verifique a variável do Frontend:

```env
VITE_API_URL=http://127.0.0.1:8000/api
```

Também verifique a configuração de CORS no Django.

---

# 31. Cronograma de Desenvolvimento

## Fase 1 — Integração da Autenticação

**Objetivo:** conectar o sistema de usuários existente.

- [ ] Login Frontend → Backend
- [ ] Sessão
- [ ] Logout
- [ ] Proteção de rotas
- [ ] Permissões
- [ ] Tratamento de erros

## Fase 2 — Integração dos Cadastros

**Objetivo:** substituir dados estáticos por dados reais.

- [ ] Clientes
- [ ] Profissionais
- [ ] Colaboradores
- [ ] Produtos
- [ ] Planos
- [ ] Cupons

## Fase 3 — Agenda

**Objetivo:** concluir o módulo principal até novembro.

- [ ] API de agendamentos
- [ ] Modelo de dados
- [ ] CRUD
- [ ] Disponibilidade
- [ ] Conflitos
- [ ] Status
- [ ] Cancelamentos
- [ ] Integração com clientes
- [ ] Integração com profissionais
- [ ] Integração com planos/pacotes
- [ ] Integração com pagamentos
- [ ] Integração com estoque
- [ ] Testes completos

## Fase 4 — Financeiro e Estoque

- [ ] Pagamentos
- [ ] Parcelas
- [ ] Caixa
- [ ] Inadimplência
- [ ] Produtos
- [ ] Movimentações
- [ ] Alertas

## Fase 5 — Notificações e Relatórios

- [ ] Histórico de mensagens
- [ ] WhatsApp
- [ ] E-mail
- [ ] Dashboards
- [ ] Relatórios
- [ ] Exportações

---

# 32. Meta de Entrega — Novembro de 2026

A meta principal da etapa atual é ter, até **novembro de 2026**, um fluxo de agenda funcional e integrado ao restante da aplicação.

### Resultado esperado

```text
LOGIN
  ↓
DASHBOARD
  ↓
CLIENTES
  ↓
PROFISSIONAIS
  ↓
AGENDA
  ↓
AGENDAMENTO
  ↓
VALIDAÇÃO DE CONFLITO
  ↓
CONFIRMAÇÃO
  ↓
ATENDIMENTO
  ↓
FINANCEIRO / ESTOQUE
```

A prioridade é entregar primeiro um fluxo funcional e consistente, evitando desenvolver todos os módulos superficialmente antes de integrar os principais processos.

---

# 33. Roadmap

## Curto prazo

- [ ] Integrar Frontend e Backend
- [ ] Finalizar autenticação integrada
- [ ] Conectar cadastros existentes à API
- [ ] Criar serviços de API no Frontend
- [ ] Finalizar modelos e endpoints necessários

## Médio prazo

- [ ] Implementar Agenda
- [ ] Validar conflitos
- [ ] Integrar clientes e profissionais
- [ ] Integrar planos e pacotes
- [ ] Integrar financeiro
- [ ] Integrar estoque
- [ ] Criar testes dos fluxos principais

## Longo prazo

- [ ] Notificações
- [ ] WhatsApp
- [ ] Relatórios
- [ ] Dashboards
- [ ] Deploy
- [ ] Observabilidade
- [ ] Melhorias de segurança
- [ ] Evolução do modelo SaaS

---

# 34. Documentação do Projeto

O projeto possui documentação relacionada a:

- Documento de Visão
- Requisitos Funcionais
- Requisitos Não Funcionais
- Regras de Negócio
- Fluxos do Sistema
- Modelo C4
- Mapa de Riscos
- Arquitetura
- Segurança
- LGPD
- Roadmap

A documentação deve acompanhar a evolução da implementação.

---

# 35. Licenciamento

O projeto possui caráter privado e está sujeito às regras de propriedade intelectual definidas pelo autor.

Não é autorizada a reprodução, comercialização ou criação de projetos derivados a partir do código, arquitetura, documentação ou conceito sem autorização.

---

# 36. Autor

**Wedley Silva Schmoeller**

Desenvolvedor Web / Full Stack

Projeto desenvolvido individualmente como solução SaaS para gestão de clínicas de estética.

---

# OneClinic

**Gestão inteligente para clínicas de estética.**

> Centralização. Organização. Segurança. Automação.
