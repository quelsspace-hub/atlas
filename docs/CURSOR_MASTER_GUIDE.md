# CURSOR MASTER GUIDE — ATLAS DE INTERESSES (HANDOFF V0.6)

**Versão:** 1.0 (Consolidada V0.6)  
**Data:** 17 de outubro de 2026  
**Status:** Fase V0 Concluída (Gate V0.4 Aprovado com Escopo Delimitado / V0.5 Governança Concluída / V0.6 Handoff Pronto). **A Aplicação V1 ainda NÃO foi implementada.**

---

## 1. IDENTIDADE E OBJETIVO DO PRODUTO

* **O que é**: O Atlas de Interesses é um sistema pessoal de organização de interesses, projetos, tarefas e conhecimento.
* **Problema que resolve**: Conecta curiosidade e estudo à execução prática sem categorizações rígidas antecipadas.
* **Diferenciais**: Local-first em Markdown com YAML Frontmatter; IDs UUID v4 imutáveis; Grupos derivados por tags (Regra OR); Base de conhecimento permanente interconectada sem duplicação de dados.

---

## 2. VISÃO FUNCIONAL E ESTRUTURA DO SISTEMA

* **Entidades Centrais**:

  1. `Group`: Área temática abrangente (exibe itens via interseção de tags em `Group.tag_ids`).
  2. `Tag`: Classificador reutilizável com `title`, `color`, `description` e `aliases`.
  3. `Item`: Registro-base. 6 tipos na V1: `project`, `course`, `interest`, `idea`, `learning_path`, `goal`.
  4. `Task`: Ação executável associada a no máximo um projeto (`Task.project_id`) ou avulsa (`null`). Marcação `is_next_action`.
  5. `Note`: Conhecimento Markdown. 3 tipos: `work` (contextual de item), `reading` (leitura), `permanent` (global, `context_item_id: null`).
  6. `InboxCapture`: Captura rápida na Caixa de Entrada para processamento posterior.

---

## 3. ARQUITETURA E STACK APROVADA

* **Stack Candidata Principal**: **Tauri 2 + React + TypeScript**.
* **Armazenamento**: Arquivos locais Markdown (`.md`) e YAML Frontmatter no *vault*.
* **Comprovado em Disco (PoC V0.4)**: CRUD, UUIDs, Regra OR, backup ZIP com SHA-256, aliases e recuperação da Inbox (`.txn_*.json`).
* **A Validar na V1 (Nativo GUI)**: Evento `tauri://close-requested`, escopos Rust do `@tauri-apps/plugin-fs` e medições reais de executável/RAM.

---

## 4. REGRAS DE NEGÓCIO INEGOCIÁVEIS

* **IDs UUID v4 (D-005)**: Imutáveis de 36 caracteres.
* **Regra OR de Grupos (D-004)**: `intersection(Group.tag_ids, Item.tag_ids).length > 0`. Nunca salvar `group_id` no item.
* **Validação de Notas (D-001)**: `work` exige item; `permanent` força `context_item_id: null`.
* **Preservação Byte a Byte (D-006)**: Alterar metadados YAML mantém o corpo Markdown 100% idêntico (SHA-256 antes === depois).
* **Recuperação Inbox Idempotente**: Uso de manifesto `.txn_{capture_id}.json` e renomeação atômica de `.tmp_*`.
* **Progresso com Nullability (D-003)**: `eligible_tasks == 0` -> `progress = null` ("Sem tarefas"). Tarefas `canceled` ignoradas.
* **Backup ZIP (D-007)**: Exportação `.zip` com `manifest.json` e validação SHA-256 em pasta limpa.

---

## 5. DESIGN SYSTEM E DIRETRIZES VISUAIS

* **Fonte Canônica**: `docs/DESIGN_SYSTEM.md` (baseado em *Design System - Atlas de Interesses.pdf*).
* **Tokens de Cores Semânticas**:

  * `Surface`: Fundo principal (`#FFFFFF` / `#0F172A`).
  * `Surface raised`: Cards, modais e painéis (`#F8FAFC` / `#1E293B`).
  * `Text` & `Text muted`: Texto primário e secundário/metadados.
  * `Primary` & `Primary hover`: Ações principais e destaques (`#2563EB` / `#3B82F6`).
  * `Danger`: Alertas críticos de disco e ações destrutivas (`#DC2626` / `#EF4444`).
* **Escala Tipográfica (Família Inter)**:

  * `Display` (48px), `Heading/L` (30px), `Heading/M` (22px), `Heading/S` (17px), `Body/L` (18px), `Body/M` (15px - Editor), `Body/S` (13px), `Label/M` (14px), `Label/S` (12px).
* **Geometria & Espaçamento**:

  * `Radius/S` (6px - Badges/Tags/Inputs), `Radius/M` (12px - Cards/Modais), `Radius/L` (24px - **Hub Centralizado**).
  * Base 8px Spacing: `Space/S` (8px), `Space/M` (16px), `Space/L` (24px), `Space/XL` (40px).
* **Regra de Interface**: O nó **'ATLAS DE INTERESSES' na Tela 1 é a caixa central da navegação** (`Radius/L`). **É PROIBIDA a criação de barra lateral fixa à esquerda**.

---

## 6. MAPA DAS 7 TELAS OFICIAIS

1. **Tela 1 — Visão Geral (Home / Hub Operacional)** `[Alt + 1]` (Caixa Central `Radius/L`)
2. **Tela 2 — Atlas / Grupos e Lista Geral de Itens** `[Alt + 3]`
3. **Tela 3 — Detalhe do Item / Projeto** `[Navegação direta]`
4. **Tela 4 — Caixa de Entrada (Inbox) & Processamento** `[Alt + 2]`
5. **Tela 5 — Central de Tarefas** `[Alt + 4]`
6. **Tela 6 — Editor e Gestor de Notas** `[Alt + 5]` (Modais anti-perda de dados)
7. **Tela 7 — Organização (Gerenciador de Grupos e Tags)** `[Alt + 6]`

---

## 7. ESTRATÉGIA INCREMENTAL DE IMPLEMENTAÇÃO (ROADMAP V1)

1. **Step 1**: Setup Tauri 2 + React + TS e integração das funções de `poc/vault_core.js`.
2. **Step 2**: Configuração dos tokens CSS/Tailwind do `docs/DESIGN_SYSTEM.md` e Vault Engine.
3. **Step 3**: Módulo de Tags e Grupos com Regra OR.
4. **Step 4**: Módulo de Itens e Lista Geral.
5. **Step 5**: Módulo de Projetos e Tarefas com progresso dinâmico e nullability.
6. **Step 6**: Editor de Notas, links `[[...]]`, aliases e promoção byte a byte (D-006).
7. **Step 7**: Inbox e Motor de Reconciliação `.txn_*.json`.
8. **Step 8**: UI das 7 Telas com Hub Centralizado (sem sidebar) e atalhos `Alt+1..6`.
9. **Step 9**: Módulo de Backup ZIP com `manifest.json` (D-007).
10. **Step 10**: Suíte de Testes Nativos GUI (`tauri://close-requested`, escopos Rust).

---

## 8. MAPA DE FONTES DE VERDADE

* `docs/ATLAS_DE_INTERESSES_DOCUMENTACAO_OFICIAL.md` — Baseline do Produto v8.0
* `docs/DESIGN_SYSTEM.md` — Paleta, Tipografia e Tokens Visuais
* `docs/DATA_MODEL.md` — Schemas YAML e Algoritmos v2.0
* `docs/UX_SPECIFICATION.md` — Especificação de UX e Wireframes ASCII
* `docs/IMPLEMENTATION_ROADMAP.md` — Guia Incremental em 10 Passos para Cursor
* `docs/TEST_PLAN.md` — Plano de Testes Auditado (PoC 13/13 PASS)
* `docs/ARCHITECTURE_DECISIONS.md` — Registros de Decisão (ADR-001 a ADR-008)
* `docs/REQUIREMENTS_TRACEABILITY.md` — Matriz de Rastreabilidade (REQ-001 a REQ-011)
* `docs/OPEN_QUESTIONS.md` — Questões Técnicas e Visuais Pendentes
* `docs/WORKFLOW_CHECKLIST_V0_V5.md` — Checklist Operacional de Roadmap



## Registro contínuo de implementação — obrigatório



Mantenha o arquivo `docs/IMPLEMENTATION_STATUS.md` como registro central e atualizado do estado real da implementação do Atlas de Interesses.



**Após cada etapa de trabalho**, atualize esse documento de forma breve, factual e direta, incluindo:



1. **Estado atual:** etapa do roadmap em andamento e situação geral.

2. **Implementado:** funcionalidades, módulos e arquivos efetivamente criados ou concluídos.

3. **Alterações recentes:** arquivos modificados e resumo do que mudou.

4. **Pendente:** funcionalidades e etapas ainda não implementadas.

5. **Problemas e riscos:** erros conhecidos, limitações técnicas, decisões pendentes e testes que falharam.

6. **Validação:** testes, builds e verificações realmente executados, com seus resultados.

7. **Próximo passo:** próxima tarefa prevista no roadmap aprovado.

---

# 9. Regras de atualização

* Baseie o relatório no estado real do repositório, nos diffs, nos resultados dos comandos e nos testes executados.
* Não declare uma funcionalidade como concluída apenas porque o código foi escrito. Diferencie implementação realizada de implementação validada.
* Não marque testes como aprovados se não tiverem sido executados com sucesso.
* Preserve o histórico de etapas anteriores por meio de um registro resumido de alterações relevantes, sem duplicar relatórios extensos.
* Atualize o documento ao final de cada etapa autorizada, inclusive quando houver falhas ou implementação parcial.
* Se uma etapa não puder ser concluída, registre o que foi feito, o que bloqueou o avanço e o que ainda precisa ser resolvido.
* Não altere requisitos, decisões arquiteturais ou o roadmap aprovado apenas para fazer o relatório parecer consistente.
* Mantenha o documento conciso, operacional e fácil de consultar no início de uma nova conversa.



Ao iniciar uma nova etapa, consulte `docs/IMPLEMENTATION_STATUS.md` junto com `AGENTS.md`, `CURSOR_MASTER_GUIDE.md` e os documentos pertinentes à tarefa. Compare o status registrado com o estado real do código antes de continuar e corrija eventuais divergências.



O documento é um registro de acompanhamento, não uma fonte de verdade superior ao código, aos testes ou à documentação oficial de requisitos. Em caso de divergência, identifique o conflito e não presuma que o registro está correto.



**Objetivo:** permitir que a pessoa responsável pelo projeto compreenda rapidamente o que existe, o que mudou, o que funciona, o que falta e qual é o próximo passo, mesmo após muitas etapas ou novas conversas.

