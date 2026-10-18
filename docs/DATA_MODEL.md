# Modelo de Dados — Atlas de Interesses (versão recuperada)

> **Status: PARCIAL.** O `DATA_MODEL.md` original (v2.0) está corrompido: os nomes de campo, caminhos e valores de enum entre crases foram substituídos por texto vazio e por saída de shell (`uid=1000(sandbox) gid=1000(sandbox) groups=1000(sandbox)`). Este arquivo reúne **somente** o que pôde ser confirmado em fontes legíveis. O que não pôde ser confirmado está marcado como **[PERDIDO]** e registrado em `OPEN_QUESTIONS.md`. Nada foi inferido ou inventado.
>
> Cópia literal do original: `reference/DATA_MODEL.md`.

**Fontes citadas:** `GUIDE` = `CURSOR_MASTER_GUIDE.md` (legível); `DM` = `DATA_MODEL.md` (corrompido); `OFC` = `ATLAS_DE_INTERESSES_DOCUMENTACAO_OFICIAL.md`; `DS` = `DESIGN_SYSTEM.md`.

---

## 1. Regras gerais de armazenamento

| Item | Valor | Fonte |
| :--- | :--- | :--- |
| Formato do arquivo | YAML Frontmatter + corpo Markdown | DM (cabeçalho), GUIDE §1 |
| Fonte de verdade | Arquivos Markdown no vault local | OFC §2.1, GUIDE §1 |
| Padrão de ID | UUID v4, 36 caracteres, único e imutável | DM, GUIDE §4 (D-005) |
| Caminhos no vault | **[PERDIDO]** — a fonte tem nove itens de lista; oito estão vazios | DM §1 |
| Manifesto de transação temporário | `.txn_{capture_id}.json` | GUIDE §4 |
| Arquivos temporários | `.tmp_*` (renomeação atômica) | GUIDE §4 |

---

## 2. Entidades

Seis entidades centrais (GUIDE §2).

### 2.1 Group

| Campo / regra | Situação | Fonte |
| :--- | :--- | :--- |
| `tag_ids` (lista de UUIDs) | Confirmado | GUIDE §2, §4 |
| Pertinência de itens | Derivada pela Regra OR; **nunca** salvar `group_id` no item | GUIDE §4 (D-004) |
| Campo de cor em hexadecimal | Indício em DM ("(Hex)"); **nome do campo [PERDIDO]** | DM §2, DS §1.2 |
| Demais campos (id, título etc.) | **[PERDIDO]** | DM §2 |

### 2.2 Tag

| Campo / regra | Situação | Fonte |
| :--- | :--- | :--- |
| `title`, `color`, `description`, `aliases` | Confirmado (nomes listados) | GUIDE §1 e §2 |
| `color` em hexadecimal no YAML | Confirmado em DS (exemplo [PERDIDO]) | DS §1.2 |
| `aliases` como array de strings | Consistente entre DM ("Array de strings") e GUIDE | DM §2 |
| Campo de identificador | **[PERDIDO]** (UUID v4 por regra geral) | DM §2 |

### 2.3 Item

| Campo / regra | Situação | Fonte |
| :--- | :--- | :--- |
| Tipos (6): `project`, `course`, `interest`, `idea`, `learning_path`, `goal` | Confirmado | GUIDE §2 |
| `tag_ids` | Confirmado (usado na Regra OR) | GUIDE §4 |
| Demais campos | **[PERDIDO]** | DM §2 |

### 2.4 Task

| Campo / regra | Situação | Fonte |
| :--- | :--- | :--- |
| `project_id` — no máximo um projeto, ou `null` (avulsa) | Confirmado | GUIDE §2 |
| `is_next_action` | Confirmado | GUIDE §2 |
| Status canceled | `canceled` confirmado; ignorado no cálculo de progresso | GUIDE §4 (D-003) |
| Enum de status | DM mostra **quatro** valores separados por `\|`; só `canceled` é legível. **Demais [PERDIDOS]** | DM §2 |
| Demais campos | **[PERDIDO]** | DM §2 |

### 2.5 Note

| Campo / regra | Situação | Fonte |
| :--- | :--- | :--- |
| Tipos (3): `work` (contextual de item), `reading` (leitura), `permanent` (global) | Confirmado | GUIDE §2 |
| `context_item_id` | Confirmado | GUIDE §2, §4 |
| `work` exige item | Confirmado | GUIDE §4 (D-001) |
| `permanent` força `context_item_id: null` | Confirmado | GUIDE §4 (D-001) |
| Regra para `reading` | **Não confirmada** (ver OQ-010) | DM §2 corrompido |
| Links `[[...]]` e resolução de aliases | Mencionados | GUIDE §7 (Step 6), REQ-009 |

### 2.6 InboxCapture

| Campo / regra | Situação | Fonte |
| :--- | :--- | :--- |
| Existência e finalidade (captura rápida para processamento posterior) | Confirmado | GUIDE §2 |
| Enum com dois valores | DM mostra `(\|)`; **valores [PERDIDOS]** | DM §2 |
| Demais campos | **[PERDIDO]** | DM §2 |

---

## 3. Algoritmos e invariantes documentados

Reproduzidos como estão em `GUIDE` §4. Constam como documentados; **não foram executados nesta sessão**.

| Ref. | Regra |
| :--- | :--- |
| D-004 | Regra OR: `intersection(Group.tag_ids, Item.tag_ids).length > 0` |
| D-001 | Validação de notas (ver §2.5) |
| D-003 | `eligible_tasks == 0` → `progress = null` ("Sem tarefas"); tarefas `canceled` ignoradas |
| D-005 | UUID v4 imutável, 36 caracteres |
| D-006 | Alterar YAML mantém o corpo Markdown 100% idêntico (SHA-256 antes === depois) |
| D-007 | Backup `.zip` com `manifest.json` e validação SHA-256 em pasta limpa |
| — | Recuperação de Inbox idempotente via `.txn_{capture_id}.json` e renomeação atômica de `.tmp_*` |

A definição de "tarefa elegível" (`eligible_tasks`) além da exclusão de `canceled` **não está legível** nas fontes.
