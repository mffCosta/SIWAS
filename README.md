# Sistema de Informação Web para Gestão Integrada de Agenda, Assiduidade e Informação Operacional em Contextos de Intervenção na Área da Saúde

> SIWAS - Sistema de Informação Web na Área da Saúde

**Estudante:** Maria Costa · 2304361  
**Orientador:** Pedro Pestana  
**UC:** Projecto de Engenharia Informática · Universidade Aberta · 2025/26  
**Repositório:** https://github.com/mffCosta/SIWAS

---

## Estado actual

🟡 **Amarelo** - Proposta inicial concluída; implementação ainda não iniciada.

---

## O que está implementado

- [x] Proposta inicial do projeto
- [x] Definição do MVP e critérios de aceitação
- [x] Stack tecnológica definida e justificada
- [x] Estrutura do repositório criada com base no template da UC
- [x] Calendarização individual detalhada

---

## O que está pendente

- [ ] Implementação da estrutura inicial do backend em Django
- [ ] Modelação da base de dados
- [ ] Criação dos diagramas de arquitetura (C4 e modelo de dados)
- [ ] Definição dos wireframes principais
- [ ] Implementação do núcleo funcional do MVP (autenticação, utentes, colaboradores, agenda, sessões, presenças e audit log)


---

## Como instalar e correr

### Pré-requisitos

- Python 3.11+
- Django
- PostgreSQL

### Instalação

```bash
# 1. Clonar o repositório
git clone https://github.com/mffCosta/SIWAS
cd SIWAS

# 2. Instalar dependências
# (a definir após criação do projeto Django)

# 3. Configurar variáveis de ambiente
# (a definir)

# 4. Correr
# (a definir)
```


### Acesso

Informação a disponibilizar após a primeira versão funcional do sistema.


---


## Decisões de arquitectura principais

| Decisão | Alternativa considerada | Razão da escolha |
|---------|-------------------------|------------------|
| Python + Django | Laravel / Blazor / Node.js + Express | Framework robusto que disponibiliza ORM, autenticação, gestão de utilizadores e formulários, permitindo desenvolvimento rápido de sistemas de informação com controlo de acessos baseado em perfis (RBAC). |
| PostgreSQL | MySQL | Sistema de gestão de bases de dados relacional robusto, com bom suporte a integridade de dados e relações complexas, adequado ao modelo de dados do projeto e bem integrado com Django, sendo igualmente adequado para suportar futuras funcionalidades de análise de dados e produção de indicadores estatísticos. |
| Django Templates + Bootstrap | SPA com React | Abordagem mais simples e adequada ao tempo disponível, permitindo interface responsiva sem complexidade adicional de uma arquitetura SPA. |
| FullCalendar.js | Implementação manual da agenda | Biblioteca madura para gestão e visualização de eventos, adequada ao módulo mais exigente do sistema (agenda). |


---

## Referências e IA utilizada

### Referências técnicas

- Documentação oficial do Django
- Documentação oficial do PostgreSQL
- Documentação oficial do FullCalendar
- Documentação oficial do Leaflet

### Ferramentas de IA utilizadas

<!-- Obrigatório declarar. Não é penalizado. -->

| Ferramenta | Para que foi usada |
|-----------|-------------------|
| ChatGPT | Apoio à clarificação do âmbito do projeto, definição do MVP, análise da stack tecnológica e estruturação da documentação |
| ProjAIde | Discussão de alternativas tecnológicas e apoio na organização inicial da proposta |

---

*Última actualização: 09/04/2026 · Sem. 4*
