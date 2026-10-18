# Decisões Técnicas — Atlas de Interesses

> Registra **apenas** decisões que constam nas fontes, com a fonte de cada uma. A coluna "Evidência" indica o que a fonte afirma; **nenhum resultado foi reverificado nesta sessão** (não há código, testes ou PoC disponíveis; ver `IMPLEMENTATION_STATUS.md`).
>
> Lacunas e conflitos de numeração estão em `OPEN_QUESTIONS.md` (OQ-004).

## 1. Decisões de regra de negócio (série D-xxx)

Fonte única da lista: `CURSOR_MASTER_GUIDE.md` §4. **D-002 não aparece em nenhuma fonte legível.**

| ID | Decisão | Evidência declarada na fonte |
| :--- | :--- | :--- |
| D-001 | Validação de notas: `work` exige item; `permanent` força `context_item_id: null` | REQ-004 marcado PASS (PoC) |
| D-003 | Progresso com nullability: `eligible_tasks == 0` → `progress = null` ("Sem tarefas"); `canceled` ignoradas | REQ-007 "Unitário (PASS)" — só teste unitário |
| D-004 | Regra OR de Grupos; nunca salvar `group_id` no item | REQ-003 PASS |
| D-005 | UUID v4 imutável, 36 caracteres | REQ-002 PASS |
| D-006 | Preservação byte a byte do corpo Markdown ao alterar YAML | REQ-005 PASS (ref. TC-013) |
| D-007 | Backup ZIP com `manifest.json` e validação SHA-256 | REQ-008 PASS (ref. TC-008) |

## 2. Registros de arquitetura (série ADR)

Fonte: `ARCHITECTURE_DECISIONS.md` (v6.0). O cabeçalho diz "ADR-001 a ADR-008", mas só cinco estão listados.

| ADR | Decisão | Situação declarada |
| :--- | :--- | :--- |
| ADR-001 | UUID v4 | Aprovado e Comprovado |
| ADR-002 | Tags por UUID e Regra OR | Aprovado e Comprovado |
| ADR-004 | Promoção byte a byte (D-006) | Aprovado e Comprovado |
| ADR-005 | Recuperação de Inbox | Aprovado no núcleo |
| ADR-008 | Stack V1: Tauri 2 + React + TypeScript | Candidata principal (não definitiva) |
| ADR-003, 006, 007 | — | **Ausentes nas fontes** |

A correspondência D-xxx ↔ ADR só é explícita para ADR-004 = D-006. As demais (ex.: ADR-001 ≈ D-005) **não estão declaradas** e não foram assumidas.

## 3. Princípios e restrições do produto

| Decisão | Fonte |
| :--- | :--- |
| Markdown é a fonte de verdade; abordagem local-first | OFC §2.1, GUIDE §1 |
| Hub centralizado: o nó "ATLAS DE INTERESSES" na Tela 1 é a caixa central (`Radius/L`, 24px, afastamento 40px). **Proibida barra lateral fixa à esquerda** | OFC §2.4, UX §1, DS §3–4, GUIDE §5 |
| Design System oficial: fonte Inter, paleta semântica Light/Dark, grade base 8px; proibido inventar cores ou alterar a escala tipográfica | OFC §2.5, DS §4 |
| Gate V0.4: núcleo de dados e persistência da PoC aprovado **com escopo delimitado** | OFC §1 |
| **Proibida a implementação da V1 sem autorização explícita** | OFC §1, AGENTS §3, WORKFLOW (V1 bloqueada) |
| Preservar a PoC V0.4 e seu histórico | AGENTS §4 |
| Sete telas oficiais, atalhos `Alt+1..6` | GUIDE §6, ROADMAP Step 8 |
| Roadmap incremental em 10 passos | GUIDE §7, ROADMAP |
| Manter `docs/IMPLEMENTATION_STATUS.md` atualizado após cada etapa, sem declarar concluído o que não foi validado | GUIDE (seção "Registro contínuo" e §9) |

## 4. Decisões que NÃO estão fechadas

| Tema | Situação | Fonte |
| :--- | :--- | :--- |
| Stack Tauri 2 + React + TS | Candidata principal | ADR-008 |
| Evento `tauri://close-requested`, escopos Rust do `@tauri-apps/plugin-fs`, tamanho de executável e RAM | A validar na V1 | GUIDE §3, OQ original |
| Mapeamento hexadecimal primitivo CSS/Tailwind | Pendente de aprovação formal | DS §5, OQ original |
| Biblioteca Lucide React para ícones | Pendente de aprovação formal | DS §5, OQ original |
| Alternância de tema pelo sistema operacional | Pendente de aprovação formal | DS §5, OQ original |
