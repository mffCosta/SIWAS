# Proposta de Projecto

**Título:** Sistema de Informação Web para Gestão Integrada de Agenda, Assiduidade e Informação Operacional em Contextos de Intervenção na Área da Saúde  
**Estudante:** Maria de Fátima Freitas Costa · 2304361  
**Orientador:** Pedro Pestana  
**Data:** 25/03/2026  
**Versão:** 1.0

---

## Sinopse

<!-- Três parágrafos máximo. -->
<!-- §1: O problema que o projecto endereça e quem o tem. -->
<!-- §2: A solução proposta e o que a distingue do que já existe. -->
<!-- §3: O resultado esperado e como se verifica que foi atingido. -->
<!-- A sinopse deve ser legível por alguém sem formação técnica. -->

Em contextos de intervenção na área da saúde, a gestão da atividade das equipas técnicas é frequentemente suportada por ferramentas dispersas, como agendas individuais, folhas de cálculo e aplicações não integradas. Esta fragmentação dificulta a coordenação da equipa, aumenta a probabilidade de erro e limita o acesso estruturado à informação relevante sobre utentes, sessões e atividade dos colaboradores.

O projeto propõe o desenvolvimento de um sistema de informação web responsivo e multiutilizador, com controlo de acessos baseado em perfis (RBAC), que centraliza num único sistema a gestão de utentes e colaboradores, agenda, sessões/intervenções e registo de presença. A solução distingue-se por integrar mecanismos de rastreabilidade de operações (audit log), garantindo maior controlo e consistência da informação.

Espera-se obter um protótipo funcional que permita executar cenários completos de utilização do sistema, incluindo autenticação, gestão de utentes e colaboradores, planeamento de compromissos, registo de sessões e controlo de presença.

---

## MVP — Definição e critérios de aceitação

<!-- Listar as funcionalidades do núcleo mínimo obrigatório na entrega final. -->
<!-- Para cada funcionalidade, definir um critério de aceitação observável. -->
<!-- Exemplo de critério fraco: "o utilizador consegue autenticar-se" -->
<!-- Exemplo de critério forte: "dado email e password válidos, o sistema autentica e redirige para o dashboard -->
<!--   em menos de 2 segundos; dado email inválido, apresenta mensagem de erro sem expor informação de sistema." -->

### Funcionalidade 1 — Autenticação e controlo de acessos (RBAC)

**Critério de aceitação:**  
Dado um utilizador com credenciais válidas, o sistema autentica e redireciona para a área correspondente ao seu perfil. Utilizadores com permissões insuficientes não conseguem aceder a funcionalidades restritas, sendo apresentada uma mensagem adequada sem exposição de informação interna.

### Funcionalidade 2 — Gestão de utentes

**Critério de aceitação:**  
O sistema permite criar, editar e consultar fichas de utente. Após gravação, os dados ficam persistidos em base de dados e podem ser recuperados posteriormente através de pesquisa.

### Funcionalidade 3 — Gestão de colaboradores

**Critério de aceitação:**  
O sistema permite criar, editar e consultar fichas de colaboradores. Após gravação, os dados ficam persistidos em base de dados e podem ser recuperados posteriormente através de
pesquisa. É possível definir níveis de acesso e responsabilidades associadas a cada colaborador, nomeadamente permissões de consulta, criação, edição e eliminação de dados. Deverá ainda ser possível definir um horário para cada colaborador, sendo apresentado na agenda como disponível em determinado período, impedindo o agendamento em períodos indisponíveis.

### Funcionalidade 4 — Agenda e compromissos

**Critério de aceitação:**  
O sistema permite criar compromissos associados a colaboradores e utentes. Após gravação, os compromissos ficam visíveis na agenda e podem ser consultados, editados ou eliminados por utilizadores autorizados.

### Funcionalidade 5 — Registo de sessões/intervenções

**Critério de aceitação:**  
O sistema permite registar sessões associadas a utentes, incluindo data, colaborador e observações. Após gravação, as sessões ficam disponíveis no histórico do utente, com acesso controlado.

### Funcionalidade 6 — Registo de presença (check-in/check-out)

**Critério de aceitação:**  
Um colaborador autenticado consegue registar entrada e saída, ficando registadas a data e hora. Quando a localização estiver disponível e autorizada, o sistema associa as coordenadas ao registo.

### Funcionalidade 7 — Registo de operações (audit log)

**Critério de aceitação:**  
O sistema regista operações relevantes de criação, alteração e eliminação de dados, associando cada ação ao utilizador responsável e respetivo timestamp, garantindo rastreabilidade e responsabilização das ações efetuadas. O histórico pode ser consultado por utilizadores autorizados.

---

## Stack tecnológica

<!-- Para cada tecnologia principal, uma linha de justificação. -->
<!-- Não é necessário ser exaustivo — as decisões menores entram nos ADRs durante o desenvolvimento. -->


| Componente | Tecnologia escolhida | Justificação |
|-----------|---------------------|-------------|
| Backend | Python + Django | Framework robusto que disponibiliza ORM, autenticação, gestão de utilizadores e formulários, permitindo desenvolvimento rápido de sistemas de informação com controlo de acessos baseado em perfis (RBAC). |
| Base de dados | PostgreSQL | Sistema de gestão de bases de dados relacional robusto, com bom suporte a integridade de dados e relações complexas, adequado ao modelo de dados do projeto e bem integrado com Django, sendo igualmente adequado para suportar futuras funcionalidades de análise de dados e produção de indicadores estatísticos. |
| Frontend base | Django Templates + Bootstrap | Permite a construção de uma interface web responsiva com menor complexidade do que uma arquitetura SPA, favorecendo rapidez de desenvolvimento e manutenção. |
| Agenda / calendário | FullCalendar.js | Biblioteca madura para visualização e gestão de eventos com suporte a vistas diária, semanal e mensal, bem como filtragem dinâmica e interação com eventos. |
| Geolocalização | Browser Geolocation API | Permite a captura de coordenadas diretamente no navegador para suporte ao registo de presença (check-in/check-out), sem necessidade de serviços externos adicionais. |
| Mapas (opcional) | Leaflet.js + OpenStreetMap | Biblioteca leve e de código aberto para visualização cartográfica, adequada para representação de localização associada a eventos ou presenças. |
| Hosting/Deploy | Railway | Plataforma de deploy simples e adequada a aplicações Django com PostgreSQL, permitindo rápida configuração e integração contínua com o repositório de código. A escolha privilegia a estabilidade e disponibilidade do sistema durante o desenvolvimento e demonstração, evitando limitações típicas de planos gratuitos com suspensão automática frequente ou restrições na persistência de dados. |
| Autenticação | Sistema nativo de autenticação do Django (sessões) | Solução integrada no framework, adequada a uma aplicação web server-side baseada em templates, permitindo gestão de utilizadores, grupos e permissões (RBAC). Esta abordagem reduz a complexidade da arquitetura face a soluções baseadas em tokens (como JWT), mantendo um nível de segurança adequado ao contexto do projeto e facilitando a implementação e manutenção do sistema. |

A escolha desta stack tecnológica procura equilibrar simplicidade de desenvolvimento, robustez e adequação ao tempo disponível, concentrando maior complexidade apenas no módulo da agenda, que apresenta requisitos de interface mais exigentes. A solução poderá evoluir em fases posteriores, nomeadamente ao nível da análise estatística da atividade e integração com sistemas externos.

---

## Esboço de arquitectura — C4 Nível 1

<!-- Opcional mas recomendado se já houver clareza sobre a fronteira do sistema. -->
<!-- Pode ser uma imagem, um diagrama em texto, ou uma descrição estruturada. -->
<!-- Vai ser refinado em docs/architecture/c4-context.png durante o desenvolvimento. -->


**Sistema:** SIWAS — Sistema de Informação Web na Área da Saúde

**Utilizadores:**
- Colaborador — regista a sua assiduidade e sessões, consulta agenda;
- Administrativo — gere utentes e marcações, sem acesso a dados clínicos;
- Administrador — gere utilizadores, permissões e dados globais.

**Sistemas externos:**
- Base de dados PostgreSQL — armazenamento persistente dos dados do sistema;
- API de Geolocalização do browser — utilizada para registo de localização no check-in/check-out.

---

## Calendário individual detalhado

<!-- Adaptar o template do Guia de Projecto ao projecto específico. -->
<!-- As datas das três entregas formais são fixas. O restante é do estudante gerir. -->
<!-- Ser realista: prever tempo para testes, revisão do relatório e preparação da defesa. -->

| Semanas | Datas | Conteúdo planeado | Marco |
|---------|-------|------------------|-------|
| Sem. 1–2 | 17–28 mar | Elaboração da proposta + configuração do repositório GitHub | **Proposta (25 mar)** |
| Sem. 3–4 | 31 mar–11 abr | Modelação da base de dados + autenticação (RBAC) | |
| Sem. 5–6 | 14–25 abr | Gestão de utentes e colaboradores + protótipo da agenda + definição de wireframes | |
| Sem. 7 | 28 abr–2 mai | Registo de sessões + presença | **Demo interna** |
| Sem. 8 | 5–6 mai | Ajustes + relatório intercalar | **Intercalar** |
| Sem. 9–10 | 7–16 mai | Integração dos módulos + testes iniciais | |
| Sem. 11–12 | 19–30 mai | Implementação de audit log + testes | |
| Sem. 13 | 2–6 jun | Validação dos critérios de aceitação do MVP | |
| Sem. 14 | 9–13 jun | Refinamento final do sistema | |
| Sem. 15 | 16–20 jun | Preparação da defesa | |
| Sem. 16 | 24 jun | Submissão final | **Final (24 jun)** |


