 # Plataforma de Gerenciamento de Ligas Esportivas

 Sistema web e mobile para **gestão completa de ligas, campeonatos, modalidades esportivas, equipes, atletas, documentos, partidas, resultados e classificações**.

 A plataforma será construída com arquitetura modular e preparada para evolução para um modelo **SaaS multi-tenant**, permitindo que diferentes ligas utilizem o mesmo sistema mantendo seus dados isolados.

---

 ## 1\. Resumo

 A plataforma tem como objetivo centralizar a administração de competições esportivas.

 O sistema terá quatro níveis principais de utilização:

```
ADMIN DA PLATAFORMA
        │
        ▼
      LIGA
        │
        ├───────────────┐
        ▼               ▼
      TIMES          COMPETIÇÕES
        │               │
        ▼               ▼
     ATLETAS        PARTIDAS/RESULTADOS
                        │
                        ▼
                 CLASSIFICAÇÕES
                        │
                        ▼
                    PÚBLICO
```

 O sistema deverá permitir que:

 - Um administrador cadastre e gerencie ligas.
- Uma liga cadastre campeonatos e modalidades.
- Uma liga cadastre e gerencie equipes.
- Equipes cadastrem seus atletas.
- Equipes enviem documentos dos atletas.
- A liga analise e aprove/reprove documentos.
- A liga crie partidas e fases.
- A liga lance resultados.
- O sistema calcule classificações automaticamente.
- O sistema gere uma classificação geral da competição.
- O público acompanhe campeonatos sem necessidade de autenticação.
- Futuramente, equipes possam utilizar aplicativo mobile.

---

 # 2\. Objetivos da Plataforma

 ## 2.1 Objetivo geral

 Criar uma plataforma digital capaz de **automatizar e centralizar a gestão de competições esportivas**, reduzindo controles manuais realizados através de planilhas, documentos e sistemas isolados.

 ## 2.2 Objetivos específicos

 ### Gestão

 - Gerenciar múltiplas ligas.
- Gerenciar múltiplos campeonatos.
- Gerenciar modalidades esportivas.
- Gerenciar categorias.
- Gerenciar equipes.
- Gerenciar atletas.
- Gerenciar documentos.

 ### Competição

 - Criar fases.
- Criar grupos.
- Criar rodadas.
- Criar partidas.
- Registrar resultados.
- Calcular classificações.
- Configurar critérios de desempate.
- Configurar regras de pontuação.

 ### Público

 - Exibir calendário.
- Exibir resultados.
- Exibir classificação.
- Exibir equipes.
- Exibir atletas.
- Exibir modalidades.
- Exibir classificação geral.

 ### Escalabilidade

 A plataforma deverá ser projetada para futuramente suportar:

 - Aplicativos mobile.
- Notificações.
- Estatísticas avançadas.
- Ranking de atletas.
- Artilharia.
- Cartões.
- Súmulas digitais.
- Transmissões.
- Domínios personalizados.
- Planos pagos.
- API pública.
- Integrações externas.

---

 # 3\. Perfis de Usuário

 ## 3.1 ADMIN

 Administrador global da plataforma.

 Permissões:

 - Criar ligas.
- Editar ligas.
- Bloquear ligas.
- Gerenciar usuários.
- Gerenciar configurações globais.
- Visualizar métricas da plataforma.

---

 ## 3.2 LIGA

 Administrador de uma determinada liga.

 Permissões:

 - Gerenciar campeonato.
- Gerenciar modalidades.
- Gerenciar categorias.
- Gerenciar equipes.
- Gerenciar atletas.
- Validar documentos.
- Criar fases.
- Criar grupos.
- Criar partidas.
- Registrar resultados.
- Gerenciar classificação.
- Gerenciar regras da competição.

---

 ## 3.3 TIME

 Representante de uma equipe.

 Permissões:

 - Gerenciar perfil do time.
- Cadastrar atletas.
- Editar atletas.
- Enviar documentação.
- Acompanhar aprovação.
- Inscrever atletas.
- Consultar jogos.
- Consultar resultados.
- Consultar classificação.

---

 ## 3.4 PÚBLICO

 Usuário sem autenticação.

 Pode:

 - Consultar ligas públicas.
- Consultar campeonatos.
- Consultar modalidades.
- Consultar partidas.
- Consultar resultados.
- Consultar classificação.
- Consultar equipes.
- Consultar atletas.

---

 # 4\. Stack Tecnológica

 ## 4.1 Visão geral

 | Camada | Tecnologia |
| --- | --- |
| Frontend Web | Next.js |
| UI | React |
| Linguagem | TypeScript |
| Backend | NestJS |
| API | REST |
| Banco | PostgreSQL |
| ORM | Prisma |
| Autenticação | JWT + Refresh Token |
| Validação | class-validator / Zod |
| Mobile | React Native + Expo |
| Testes unitários | Jest |
| Testes E2E | Playwright / Supertest |
| Documentação API | Swagger / OpenAPI |
| Containers | Docker |
| CI/CD | GitHub Actions |
| Controle de versão | Git + GitHub |
| Cache futuro | Redis |
| Storage | S3-compatible |
| Observabilidade futura | OpenTelemetry |

---

 # 5\. Frontend Web

 ## Tecnologia

 **Next.js + React + TypeScript**

 O Next.js será utilizado para construção do frontend web, incluindo áreas administrativas e páginas públicas.

 ## Responsabilidades

 O frontend será responsável por:

 - Interface administrativa.
- Dashboard.
- Cadastro de ligas.
- Cadastro de campeonatos.
- Cadastro de modalidades.
- Cadastro de equipes.
- Cadastro de atletas.
- Upload de documentos.
- Gestão de partidas.
- Gestão de resultados.
- Classificação.
- Site público da liga.

 ## Estrutura sugerida

```
apps/
└── web/
    ├── app/
    │   ├── (public)/
    │   ├── (auth)/
    │   └── dashboard/
    │
    ├── components/
    ├── features/
    ├── hooks/
    ├── services/
    ├── lib/
    ├── types/
    └── styles/
```

---

 # 6\. Backend

 ## Tecnologia

 **NestJS + TypeScript**

 O backend será desenvolvido com NestJS utilizando arquitetura modular.

 ## Responsabilidades

 O backend será responsável por:

 - Autenticação.
- Autorização.
- Regras de negócio.
- Persistência.
- Validação.
- Gestão de usuários.
- Gestão de ligas.
- Gestão de campeonatos.
- Gestão de equipes.
- Gestão de atletas.
- Gestão documental.
- Gestão de partidas.
- Cálculo de classificação.
- Classificação geral.
- API pública.

 ## Estrutura sugerida

```
apps/
└── api/
    └── src/
        ├── auth/
        ├── users/
        ├── leagues/
        ├── championships/
        ├── sports/
        ├── categories/
        ├── teams/
        ├── athletes/
        ├── documents/
        ├── stages/
        ├── groups/
        ├── rounds/
        ├── matches/
        ├── results/
        ├── standings/
        ├── general-standings/
        ├── scoring-rules/
        ├── files/
        ├── notifications/
        ├── common/
        └── database/
```

---

 # 7\. Banco de Dados

 ## PostgreSQL

 O banco principal será o **PostgreSQL**, por ser um banco relacional adequado ao domínio, que possui muitas relações entre entidades.

 Exemplos:

```
Liga
 └── Campeonato
      └── Modalidade
           └── Categoria
                └── Equipe
                     └── Atleta
```

 Além disso:

```
Campeonato
 └── Fase
      └── Grupo
           └── Rodada
                └── Partida
```

---

 # 8\. ORM

 ## Prisma

 Será utilizado **Prisma ORM** para acesso ao PostgreSQL.

 Responsabilidades:

 - Modelagem.
- Queries.
- Migrations.
- Relacionamentos.
- Transações.
- Tipagem.

 Estrutura:

```
prisma/
├── schema.prisma
├── migrations/
└── seed.ts
```

---

 # 9\. Mobile

 ## React Native + Expo

 O aplicativo mobile será desenvolvido posteriormente utilizando:

```
React Native
+
Expo
+
TypeScript
```

 O aplicativo terá inicialmente foco nos usuários `TIME`.

 ### Funcionalidades mobile

 - Login.
- Dashboard do time.
- Cadastro de atletas.
- Upload de documentos.
- Consulta de documentação.
- Consulta de jogos.
- Consulta de resultados.
- Consulta de classificação.
- Notificações.

 Posteriormente:

 - Push notifications.
- Carteirinha digital.
- QR Code do atleta.
- Súmula digital.
- Estatísticas.

---

 # 10\. Arquitetura do Sistema

 A arquitetura inicial será baseada em **monólito modular**, evitando a complexidade prematura de microsserviços.

```
                    ┌─────────────────────┐
                    │      USUÁRIO        │
                    └──────────┬──────────┘
                               │
              ┌────────────────┼────────────────┐
              │                │                │
              ▼                ▼                ▼
       ┌─────────────┐  ┌─────────────┐  ┌─────────────┐
       │ Web         │  │ Mobile      │  │ API Pública │
       │ Next.js     │  │ React Native│  │             │
       └──────┬──────┘  └──────┬──────┘  └──────┬──────┘
              │                │                │
              └────────────────┼────────────────┘
                               ▼
                    ┌─────────────────────┐
                    │      NestJS API     │
                    ├─────────────────────┤
                    │ Auth                │
                    │ Users               │
                    │ Leagues             │
                    │ Championships       │
                    │ Sports              │
                    │ Teams               │
                    │ Athletes            │
                    │ Documents           │
                    │ Matches             │
                    │ Results             │
                    │ Standings           │
                    └──────────┬──────────┘
                               │
                    ┌──────────┴──────────┐
                    ▼                     ▼
             ┌──────────────┐      ┌──────────────┐
             │ PostgreSQL   │      │ File Storage │
             │              │      │ S3           │
             └──────────────┘      └──────────────┘
```

---

 # 11\. Arquitetura de Software

 A aplicação utilizará uma abordagem baseada em:

 - Modularização por domínio.
- Clean Architecture como referência.
- SOLID.
- Separation of Concerns.
- Domain-driven organization.
- API REST.
- DTOs.
- Services.
- Repositories.
- Guards.
- Policies/permissions.

 Fluxo principal:

```
Controller
    ↓
Application Service
    ↓
Domain / Business Rules
    ↓
Repository
    ↓
Database
```

---

 # 12\. Multi-tenancy

 A aplicação será preparada para múltiplas ligas.

```
PLATAFORMA
│
├── LIGA A
│   ├── Campeonato A
│   ├── Times
│   └── Atletas
│
├── LIGA B
│   ├── Campeonato B
│   ├── Times
│   └── Atletas
│
└── LIGA C
    ├── Campeonato C
    ├── Times
    └── Atletas
```

 No MVP será adotado o modelo:

 **Shared Database + Shared Schema + tenant\_id**

 As entidades pertencentes à liga possuirão referência ao respectivo `league_id`.

 Exemplo:

```
teams
-----------------
id
league_id
name
...
```

 O backend deverá garantir que um usuário não consiga acessar dados de outra liga.

---

 # 13\. Segurança

 ## Autenticação

 Utilizar:

```
Access Token
+
Refresh Token
```

 ## Autorização

 RBAC:

```
ADMIN
LIGA
TIME
```

 Exemplo:

```
ADMIN
 ├── league:create
 ├── league:update
 └── user:manage

LIGA
 ├── team:create
 ├── athlete:approve
 ├── match:create
 └── result:create

TIME
 ├── athlete:create
 ├── document:upload
 └── match:read
```

 ## Requisitos de segurança

 - Senhas armazenadas com hash seguro.
- Nunca armazenar senha em texto puro.
- Validação de entrada.
- Rate limiting.
- CORS configurado.
- Proteção contra acesso entre tenants.
- Controle de permissões.
- Logs de operações críticas.
- Validação de arquivos.
- Limite de tamanho para uploads.
- URLs privadas para documentos.
- HTTPS em produção.

---

 # 14\. Modelo Conceitual de Dados

 Principais entidades:

```
User
League
Championship
Sport
Category
Team
Athlete
AthleteDocument
Registration
Stage
Group
Round
Match
MatchResult
Standing
GeneralStanding
ScoringRule
```

---

 # 15\. Principais Relacionamentos

```
User
 │
 ├──────────────► League
 │
 └──────────────► Team

League
 │
 ├──────────────► Championship
 ├──────────────► Team
 └──────────────► User

Championship
 │
 ├──────────────► Sport
 ├──────────────► Category
 ├──────────────► Stage
 └──────────────► ScoringRule

Team
 │
 ├──────────────► Athlete
 └──────────────► Match

Athlete
 │
 └──────────────► AthleteDocument

Stage
 │
 ├──────────────► Group
 └──────────────► Round

Round
 │
 └──────────────► Match

Match
 │
 └──────────────► MatchResult
```

---

 # 16\. Modelo de Dados Inicial

 ## User

```
User
- id
- name
- email
- passwordHash
- role
- status
- createdAt
- updatedAt
```

 ## League

```
League
- id
- name
- slug
- description
- logo
- status
- createdAt
- updatedAt
```

 ## Championship

```
Championship
- id
- leagueId
- name
- description
- startDate
- endDate
- status
```

 ## Sport

```
Sport
- id
- name
- type
- description
```

 ## Category

```
Category
- id
- championshipId
- sportId
- name
- gender
- ageGroup
```

 ## Team

```
Team
- id
- leagueId
- name
- shortName
- logo
- status
```

 ## Athlete

```
Athlete
- id
- name
- cpf
- birthDate
- gender
- photo
- status
```

 ## Registration

```
Registration
- id
- athleteId
- teamId
- categoryId
- status
```

 ## Document

```
AthleteDocument
- id
- athleteId
- type
- fileUrl
- status
- rejectionReason
- reviewedAt
- reviewedBy
```

 ## Match

```
Match
- id
- championshipId
- categoryId
- stageId
- roundId
- homeTeamId
- awayTeamId
- scheduledAt
- location
- status
```

 ## MatchResult

```
MatchResult
- id
- matchId
- homeScore
- awayScore
- finishedAt
```

---

 # 17\. Motor de Classificação

 O sistema deverá evitar regras específicas de uma única modalidade.

 A classificação será baseada em regras configuráveis.

 Exemplo:

```
ScoringRule

- championshipId
- victoryPoints
- drawPoints
- defeatPoints
- criteria[]
```

 Critérios possíveis:

```
POINTS
WINS
GOAL_DIFFERENCE
GOALS_FOR
HEAD_TO_HEAD
FAIR_PLAY
```

 Para modalidades diferentes:

```
FUTEBOL

Vitória = 3
Empate = 1
Derrota = 0
```

 Enquanto:

```
VÔLEI

3x0 / 3x1 = 3 pontos
3x2 = 2 pontos
2x3 = 1 ponto
0x3 / 1x3 = 0 pontos
```

 O cálculo deve ser implementado como serviço de domínio:

```
StandingsCalculationService
```

---

 # 18\. Classificação Geral

 A classificação geral será independente da classificação das modalidades.

 Exemplo:

```
GeneralStanding

Team A
Futebol: 10
Futsal: 8
Vôlei: 12
----------------
Total: 30
```

 As regras serão configuráveis.

 Exemplo:

```
1º lugar = 10 pontos
2º lugar = 8 pontos
3º lugar = 6 pontos
4º lugar = 4 pontos
Participação = 1 ponto
```

---

 # 19\. API

 A API seguirá padrão REST.

 ## Autenticação

```
POST /auth/login
POST /auth/refresh
POST /auth/logout
```

 ## Usuários

```
GET    /users
GET    /users/:id
POST   /users
PATCH  /users/:id
DELETE /users/:id
```

 ## Ligas

```
GET    /leagues
GET    /leagues/:id
POST   /leagues
PATCH  /leagues/:id
DELETE /leagues/:id
```

 ## Times

```
GET    /leagues/:leagueId/teams
POST   /leagues/:leagueId/teams
GET    /teams/:id
PATCH  /teams/:id
```

 ## Atletas

```
GET    /teams/:teamId/athletes
POST   /teams/:teamId/athletes
GET    /athletes/:id
PATCH  /athletes/:id
```

 ## Documentos

```
POST  /athletes/:athleteId/documents
GET   /athletes/:athleteId/documents
PATCH /documents/:id/approve
PATCH /documents/:id/reject
```

 ## Partidas

```
GET   /championships/:id/matches
POST  /championships/:id/matches
GET   /matches/:id
PATCH /matches/:id
```

 ## Resultados

```
POST  /matches/:id/result
PATCH /matches/:id/result
```

 ## Classificação

```
GET /championships/:id/standings
GET /leagues/:id/general-standing
```

---

 # 20\. API Pública

 As informações públicas deverão possuir endpoints específicos.

```
GET /public/leagues/:slug
GET /public/leagues/:slug/championships
GET /public/championships/:id/matches
GET /public/championships/:id/results
GET /public/championships/:id/standings
GET /public/teams/:id
```

 Isso permitirá que o frontend público seja desacoplado da área administrativa.

---

 # 21\. Upload de Documentos

 Os documentos dos atletas não devem ser armazenados diretamente no PostgreSQL.

 Arquitetura:

```
Frontend
    │
    ▼
Backend
    │
    ▼
Object Storage
    │
    ├── documents/
    ├── athletes/
    └── logos/
```

 O banco armazenará apenas os metadados:

```
documentId
athleteId
fileName
mimeType
storageKey
status
```

---

 # 22\. Estrutura do Monorepo

```
sports-league-platform/
│
├── apps/
│   ├── web/
│   ├── api/
│   └── mobile/
│
├── packages/
│   ├── ui/
│   ├── types/
│   ├── config/
│   └── validation/
│
├── prisma/
│   ├── schema.prisma
│   ├── migrations/
│   └── seed.ts
│
├── docs/
│   ├── architecture/
│   ├── uml/
│   ├── api/
│   └── decisions/
│
├── .github/
│   └── workflows/
│
├── docker-compose.yml
├── package.json
├── turbo.json
└── README.md
```

 Pode ser utilizado **Turborepo** para gerenciamento do monorepo.

---

 # 23\. Metodologia de Desenvolvimento

 Será utilizado **Agile/Scrum adaptado para desenvolvimento de produto**, com ciclos curtos e entregas incrementais.

 A metodologia terá elementos de:

 - Scrum.
- Kanban.
- TDD quando aplicável.
- CI/CD.
- Code Review.
- Continuous Delivery.

---

 # 24\. Organização das Sprints

```
Sprint
│
├── Planning
├── Desenvolvimento
├── Code Review
├── Testes
├── QA
├── Deploy
└── Retrospectiva
```

 Cada sprint deverá produzir uma funcionalidade potencialérios de aceite estiveremmente utilizável.

---

 # 25\. Definition of Ready

 Uma tarefa poderá entrar em desenvolvimento quando:

 - Requisito estiver definido.
- Critérios de aceite estiverem definidos.
- Dependências conhecidas.
- Design definido quando necessário.
- Critérios técnicos conhecidos.

---

 # 26\. Definition of Done

 Uma funcionalidade será considerada concluída quando:

 - Código implementado.
- Testes unitários implementados.
- Testes de integração quando aplicável.
- Code review realizado.
- Lint executado.
- Build executado.
- Documentação atualizada.
- Migration criada quando necessária.
- Critérios de aceite atendidos.
- Deploy realizado em ambiente de homologação.

---

 # 27\. Git Flow

 Estrutura sugerida:

```
main
 │
 └── develop
      │
      ├── feature/auth
      ├── feature/leagues
      ├── feature/teams
      ├── feature/athletes
      └── feature/matches
```

 Pull Requests serão obrigatórios para merge na branch principal.

 Padrão de commit:

```
feat: adiciona cadastro de liga
fix: corrige cálculo de classificação
refactor: reorganiza módulo de atletas
test: adiciona testes de standings
docs: atualiza documentação da API
chore: atualiza dependências
```

---

 # 28\. Testes

 ## Testes unitários

 Principalmente:

 - Serviços.
- Regras de negócio.
- Cálculo de classificação.
- Critérios de desempate.
- Permissões.

 Exemplo:

```
StandingsCalculationService
```

 deve possuir testes para:

```
vitória
empate
derrota
saldo de gols
confronto direto
empates entre equipes
```

 ## Testes de integração

 Validar:

```
API
 ↓
Service
 ↓
Repository
 ↓
PostgreSQL
```

 ## Testes E2E

 Fluxos principais:

```
ADMIN cria liga
        ↓
LIGA cria campeonato
        ↓
LIGA cria time
        ↓
TIME cadastra atleta
        ↓
TIME envia documento
        ↓
LIGA aprova documento
        ↓
LIGA cria partida
        ↓
LIGA lança resultado
        ↓
Sistema atualiza classificação
```

---

 # 29\. CI/CD

 Pipeline:

```
Push / Pull Request
        │
        ▼
Install
        │
        ▼
Lint
        │
        ▼
Type Check
        │
        ▼
Unit Tests
        │
        ▼
Integration Tests
        │
        ▼
Build
        │
        ▼
Docker Image
        │
        ▼
Deploy
```

---

 # 30\. Ambientes

 Serão utilizados:

```
LOCAL
  ↓
DEVELOPMENT
  ↓
STAGING
  ↓
PRODUCTION
```

 Cada ambiente deverá possuir banco e configurações independentes.

---

 # 31\. Observabilidade

 Inicialmente:

 - Logs estruturados.
- Logs de erro.
- Health check.
- Métricas básicas.

 Endpoints:

```
GET /health
GET /health/database
```

 Futuramente:

```
OpenTelemetry
Prometheus
Grafana
Sentry
```

---

 # 32\. Roadmap do MVP

 ## Sprint 0 — Fundação

 ### Objetivo

 Preparar infraestrutura e arquitetura.

 ### Entregas

 - Repositório.
- Monorepo.
- Docker.
- PostgreSQL.
- NestJS.
- Next.js.
- Prisma.
- CI.
- ESLint.
- Prettier.
- Ambiente local.

---

 ## Sprint 1 — Autenticação

 ### Entregas

 - User.
- Roles.
- Login.
- Logout.
- Refresh token.
- Guards.
- RBAC.

---

 ## Sprint 2 — Liga

 ### Entregas

 - CRUD de liga.
- Dashboard.
- Logo.
- Status.
- Usuário responsável.

---

 ## Sprint 3 — Campeonatos e modalidades

 ### Entregas

 - Campeonato.
- Modalidade.
- Categoria.
- Regras básicas.

---

 ## Sprint 4 — Times

 ### Entregas

 - Cadastro de times.
- Edição.
- Logo.
- Usuário TIME.
- Associação com liga.

---

 ## Sprint 5 — Atletas

 ### Entregas

 - Cadastro.
- Edição.
- CPF.
- Data de nascimento.
- Foto.
- Inscrição em modalidade.

---

 ## Sprint 6 — Documentação

 ### Entregas

 - Upload.
- Storage.
- Status.
- Aprovação.
- Reprovação.
- Motivo da reprovação.

---

 ## Sprint 7 — Estrutura da competição

 ### Entregas

 - Fases.
- Grupos.
- Rodadas.
- Partidas.
- Calendário.

---

 ## Sprint 8 — Resultados

 ### Entregas

 - Cadastro de resultado.
- Edição.
- Validação.
- Histórico.

---

 ## Sprint 9 — Classificação

 ### Entregas

 - Cálculo automático.
- Pontuação.
- Critérios de desempate.
- Classificação por modalidade.

---

 ## Sprint 10 — Classificação geral

 ### Entregas

 - Regras gerais.
- Ranking geral.
- Pontuação por modalidade.
- Ranking das equipes.

---

 ## Sprint 11 — Portal público

 ### Entregas

 - Página pública da liga.
- Campeonato.
- Modalidades.
- Jogos.
- Resultados.
- Classificação.
- Times.

---

 ## Sprint 12 — MVP Release

 ### Entregas

 - Testes E2E.
- Correções.
- Segurança.
- Performance.
- Documentação.
- Deploy.
- Monitoramento.

---

 # 33\. Critério para considerar o MVP pronto

 O MVP será considerado concluído quando o seguinte fluxo funcionar completamente:

```
ADMIN
 │
 └──► Cria LIGA
          │
          ▼
        LIGA
          │
          ├──► Cria CAMPEONATO
          │
          ├──► Define MODALIDADE
          │
          ├──► Cadastra TIMES
          │
          └──► Cria COMPETIÇÃO
                     │
                     ▼
                   TIMES
                     │
                     └──► Cadastram ATLETAS
                                │
                                └──► Enviam DOCUMENTOS

LIGA
 │
 ├──► Aprova atletas
 │
 ├──► Cria partidas
 │
 └──► Lança resultados
            │
            ▼
       CLASSIFICAÇÃO
            │
            ▼
      CLASSIFICAÇÃO GERAL
            │
            ▼
          PÚBLICO
```

---

 # 34\. UML — Diagrama de Casos de Uso

```
flowchart LR
    Admin((ADMIN))
    Liga((LIGA))
    Time((TIME))
    Publico((PÚBLICO))

    subgraph Plataforma
        UC1[Gerenciar Ligas]
        UC2[Gerenciar Campeonatos]
        UC3[Gerenciar Modalidades]
        UC4[Gerenciar Times]
        UC5[Gerenciar Atletas]
        UC6[Gerenciar Documentos]
        UC7[Gerenciar Partidas]
        UC8[Registrar Resultados]
        UC9[Consultar Classificação]
        UC10[Consultar Resultados]
        UC11[Consultar Jogos]
        UC12[Gerenciar Classificação Geral]
    end

    Admin --> UC1
    Admin --> UC2

    Liga --> UC2
    Liga --> UC3
    Liga --> UC4
    Liga --> UC5
    Liga --> UC6
    Liga --> UC7
    Liga --> UC8
    Liga --> UC12

    Time --> UC5
    Time --> UC6
    Time --> UC9
    Time --> UC10
    Time --> UC11

    Publico --> UC9
    Publico --> UC10
    Publico --> UC11
    Publico --> UC12
```

---

 # 35\. UML — Diagrama de Classes

```
classDiagram

class User {
    +UUID id
    +String name
    +String email
    +String passwordHash
    +Role role
    +Status status
}

class League {
    +UUID id
    +String name
    +String slug
    +String description
    +Status status
}

class Championship {
    +UUID id
    +String name
    +Date startDate
    +Date endDate
    +Status status
}

class Sport {
    +UUID id
    +String name
    +String type
}

class Category {
    +UUID id
    +String name
    +String gender
    +String ageGroup
}

class Team {
    +UUID id
    +String name
    +String shortName
    +String logo
}

class Athlete {
    +UUID id
    +String name
    +String cpf
    +Date birthDate
    +String gender
    +String photo
}

class AthleteDocument {
    +UUID id
    +String type
    +String fileUrl
    +DocumentStatus status
    +String rejectionReason
}

class Registration {
    +UUID id
    +RegistrationStatus status
}

class Stage {
    +UUID id
    +String name
    +StageType type
}

class Group {
    +UUID id
    +String name
}

class Round {
    +UUID id
    +String name
    +Int number
}

class Match {
    +UUID id
    +Date scheduledAt
    +String location
    +MatchStatus status
}

class MatchResult {
    +UUID id
    +Int homeScore
    +Int awayScore
}

class ScoringRule {
    +UUID id
    +Int victoryPoints
    +Int drawPoints
    +Int defeatPoints
}

class Standing {
    +UUID id
    +Int position
    +Int points
    +Int games
    +Int wins
    +Int draws
    +Int losses
    +Int goalsFor
    +Int goalsAgainst
    +Int goalDifference
}

User "1" --> "0..*" League : manages
User "1" --> "0..*" Team : represents

League "1" --> "0..*" Championship
League "1" --> "0..*" Team

Championship "1" --> "1..*" Category
Championship "1" --> "1..*" Stage
Championship "1" --> "0..*" ScoringRule

Sport "1" --> "0..*" Category

Category "1" --> "0..*" Registration
Team "1" --> "0..*" Registration
Athlete "1" --> "0..*" Registration

Athlete "1" --> "0..*" AthleteDocument

Stage "1" --> "0..*" Group
Stage "1" --> "0..*" Round

Round "1" --> "0..*" Match
Group "1" --> "0..*" Match

Team "1" --> "0..*" Match : home
Team "1" --> "0..*" Match : away

Match "1" --> "0..1" MatchResult

Category "1" --> "0..*" Standing
Team "1" --> "0..*" Standing
```

---

 # 36\. UML — Diagrama de Sequência: Cadastro de Atleta

```
sequenceDiagram
    actor Time as TIME
    participant Web as Frontend
    participant API as Backend
    participant Auth as Auth
    participant DB as PostgreSQL
    participant Storage as File Storage

    Time->>Web: Acessa cadastro de atleta
    Web->>API: POST /teams/{id}/athletes
    API->>Auth: Valida token
    Auth-->>API: Usuário autorizado

    API->>DB: Cria atleta
    DB-->>API: Atleta criado

    API-->>Web: Retorna atleta
    Web-->>Time: Exibe cadastro

    Time->>Web: Envia documento
    Web->>API: POST /athletes/{id}/documents
    API->>Storage: Upload do arquivo
    Storage-->>API: storageKey

    API->>DB: Salva metadados
    DB-->>API: Documento criado

    API-->>Web: Documento pendente
    Web-->>Time: Upload concluído
```

---

 # 37\. UML — Diagrama de Sequência: Resultado

```
sequenceDiagram
    actor Liga as LIGA
    participant Web as Frontend
    participant API as Backend
    participant DB as PostgreSQL
    participant Calc as Standings Service

    Liga->>Web: Informa resultado
    Web->>API: POST /matches/{id}/result

    API->>DB: Busca partida
    DB-->>API: Partida

    API->>DB: Salva resultado
    DB-->>API: Resultado salvo

    API->>Calc: Recalcular classificação
    Calc->>DB: Busca partidas da competição
    DB-->>Calc: Resultados

    Calc->>Calc: Calcula pontos
    Calc->>Calc: Aplica desempates

    Calc->>DB: Atualiza standings
    DB-->>Calc: Classificação atualizada

    Calc-->>API: Cálculo concluído
    API-->>Web: Resultado atualizado
    Web-->>Liga: Classificação atualizada
```

---

 # 38\. UML — Diagrama de Arquitetura

```
flowchart TB

    User[Usuário]

    subgraph Clients
        Web[Next.js Web]
        Mobile[React Native Mobile]
    end

    subgraph Backend
        API[NestJS API]

        Auth[Auth Module]
        League[League Module]
        Championship[Championship Module]
        Team[Team Module]
        Athlete[Athlete Module]
        Match[Match Module]
        Standing[Standing Module]
        Document[Document Module]
    end

    subgraph Infrastructure
        DB[(PostgreSQL)]
        Storage[(Object Storage)]
        Cache[(Redis - Futuro)]
    end

    User --> Web
    User --> Mobile

    Web --> API
    Mobile --> API

    API --> Auth
    API --> League
    API --> Championship
    API --> Team
    API --> Athlete
    API --> Match
    API --> Standing
    API --> Document

    Auth --> DB
    League --> DB
    Championship --> DB
    Team --> DB
    Athlete --> DB
    Match --> DB
    Standing --> DB

    Document --> Storage

    API -.-> Cache
```

---

 # 39\. UML — Fluxo de Negócio

 Mermaid flowchart: ADMIN cria Liga, LIGA configura Campeonato, LIGA cadastra Modalidades, LIGA cadastra Times, TIME cadastra Atletas, TIME envia Documentos, LIGA analisa Documentos, Documento aprovado?, Atleta habilitado, Atleta pendente, LIGA cria Partidas, LIGA registra Resultado, Sistema recalcula Classificação, Sistema atualiza Classificação Geral, Público consulta Campeonato

---

 # 40\. ADR — Decisões Arquiteturais

 ## ADR-001 — Monólito modular

 **Decisão:** utilizar monólito modular no MVP.

 **Motivo:**

 A aplicação ainda estará validando produto e domínio. Microsserviços adicionariam complexidade operacional sem benefício proporcional nessa fase.

 A arquitetura deverá permitir extração futura de módulos caso necessário.

---

 ## ADR-002 — PostgreSQL

 **Decisão:** PostgreSQL.

 **Motivo:**

 O domínio possui grande quantidade de relacionamentos e transações, favorecendo um banco relacional.

---

 ## ADR-003 — Prisma

 **Decisão:** Prisma como ORM.

 **Motivo:**

 Integração com TypeScript, tipagem e migrations.

---

 ## ADR-004 — REST

 **Decisão:** REST no MVP.

 **Motivo:**

 É simples, amplamente conhecido e suficiente para web, mobile e API pública.

 GraphQL poderá ser avaliado posteriormente.

---

 ## ADR-005 — Multi-tenancy

 **Decisão:** Shared Database / Shared Schema.

 **Motivo:**

 Menor custo operacional e simplicidade inicial.

 O isolamento será garantido por regras de autorização e `league_id`.

---

 # 41\. Requisitos Não Funcionais

 ## Performance

 Meta inicial:

```
API p95 < 500ms
```

 para operações comuns.

 ## Disponibilidade

 Objetivo inicial:

```
>= 99%
```

 ## Segurança

 - HTTPS.
- JWT.
- RBAC.
- Hash de senha.
- Validação.
- Rate limiting.
- Controle de acesso por liga.

 ## Escalabilidade

 A arquitetura deverá permitir:

```
Web
 ↓
Load Balancer
 ↓
API x N
 ↓
PostgreSQL
```

 Posteriormente:

```
API
 ↓
Redis
 ↓
Workers
 ↓
Queue
```

---

 # 42\. Roadmap Futuro

 Após o MVP:

 ## Estatísticas

 - Artilharia.
- Assistências.
- Cartões.
- Aproveitamento.
- Estatísticas por atleta.

 ## Mobile

 - App do time.
- Push notification.
- Carteirinha digital.
- QR Code.

 ## Comunicação

 - Notícias.
- Comunicados.
- Notificações.

 ## Monetização

 - Planos.
- Assinaturas.
- Limites por plano.
- Pagamentos.

 ## White-label

 - Logo.
- Cores.
- Domínio personalizado.
- Identidade visual da liga.

 ## Integrações

 - WhatsApp.
- E-mail.
- Push.
- Streaming.
- Redes sociais.

---

 # 43\. Estrutura Final do Projeto

```
sports-league-platform/
│
├── apps/
│   ├── web/
│   ├── api/
│   └── mobile/
│
├── packages/
│   ├── ui/
│   ├── types/
│   ├── validation/
│   └── config/
│
├── prisma/
│   ├── schema.prisma
│   ├── migrations/
│   └── seed.ts
│
├── docs/
│   ├── architecture/
│   ├── uml/
│   ├── api/
│   ├── adr/
│   └── requirements/
│
├── tests/
│   ├── e2e/
│   └── integration/
│
├── .github/
│   └── workflows/
│
├── docker-compose.yml
├── package.json
├── turbo.json
├── README.md
└── LICENSE
```

---

 # 44\. Visão de Longo Prazo

 A visão da plataforma é evoluir de um sistema de gerenciamento de campeonatos para uma **plataforma completa de infraestrutura esportiva**.

```
                    SPORTS PLATFORM
                           │
        ┌──────────────────┼──────────────────┐
        │                  │                  │
      LIGAS              TIMES             ATLETAS
        │                  │                  │
        ▼                  ▼                  ▼
  CAMPEONATOS          ELENCOS          DOCUMENTOS
        │
        ▼
    MODALIDADES
        │
        ▼
      PARTIDAS
        │
        ▼
    RESULTADOS
        │
        ▼
   CLASSIFICAÇÕES
        │
        ▼
     ESTATÍSTICAS
        │
        ▼
      PÚBLICO
```

 O MVP deverá permanecer focado no núcleo:

 > **Liga → Campeonato → Modalidade → Time → Atleta → Partida → Resultado → Classificação.**

 Todas as funcionalidades adicionais deverão ser desenvolvidas posteriormente sem comprometer esse núcleo.

---

 # 45\. Próximo Passo de Engenharia

 Após a aprovação deste documento, a ordem recomendada de implementação é:

```
1. Definir requisitos funcionais detalhados
          ↓
2. Validar modelo de domínio
          ↓
3. Criar ERD definitivo
          ↓
4. Criar schema PostgreSQL/Prisma
          ↓
5. Criar estrutura do monorepo
          ↓
6. Implementar autenticação/RBAC
          ↓
7. Implementar módulo Liga
          ↓
8. Implementar Campeonato/Modalidade
          ↓
9. Implementar Times
          ↓
10. Implementar Atletas
          ↓
11. Implementar Documentos
          ↓
12. Implementar Partidas
          ↓
13. Implementar Resultados
          ↓
14. Implementar Classificação
          ↓
15. Implementar Portal Público
          ↓
16. Testes E2E
          ↓
17. Deploy do MVP
```

---

 # Status

 | Item | Valor |
| --- | --- |
| **Projeto** | Plataforma de Gerenciamento de Ligas Esportivas |
| **Versão** | `0.1.0` |
| **Status** | Planejamento / Arquitetura |
| **Objetivo atual** | Desenvolvimento do MVP |
| **Arquitetura** | Monólito modular preparado para evolução |
| **Backend** | NestJS + TypeScript |
| **Frontend** | Next.js + React \+ TypeScript |
| **Mobile** | React Native + Expo |
| **Database** | PostgreSQL |
| **ORM** | Prisma |
| **API** | REST |
| **Metodologia** | Agile/Scrum + práticas de CI/CD |
| **Licença** | A definir |
