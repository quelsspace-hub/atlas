# Atlas de Interesses — Documentação Recuperada

Cópia organizada da documentação para uso durante a implementação no Cursor. Criada em 17 de outubro de 2026 a partir dos 14 arquivos de `/mnt/project/`, que **não foram alterados**.

> **Leia antes:** parte das fontes está degradada ou corrompida (texto entre crases perdido; `DATA_MODEL.md` original contém saída de shell). Esta pasta **não está validada**: foi apenas organizada. Nenhum teste foi executado e a **V1 não está autorizada**. Veja `OPEN_QUESTIONS.md` e `IMPLEMENTATION_STATUS.md`.

## Arquivos desta pasta

| Arquivo | Conteúdo |
| :--- | :--- |
| `README.md` | Este índice e a ordem de leitura |
| `IMPLEMENTATION_STATUS.md` | Documentado × implementado × testado |
| `DECISIONS.md` | Decisões confirmadas (D-xxx, ADR, princípios) com fontes |
| `OPEN_QUESTIONS.md` | Questões originais, 14 conflitos/lacunas e informações não confirmadas |
| `DATA_MODEL.md` | Modelo de dados parcial, só com o que é confirmável |
| `SOURCES.md` | Origem, tamanho, hash e integridade de cada fonte |
| `reference/` | Cópias literais dos 14 originais, com banner de proveniência |

## Ordem de leitura

1. `reference/AGENTS.md` — limites de autonomia (regras invariáveis).
2. `reference/CURSOR_MASTER_GUIDE.md` — única fonte plenamente legível; base do restante.
3. `IMPLEMENTATION_STATUS.md` — o que existe de fato.
4. `DECISIONS.md` e `OPEN_QUESTIONS.md` — o que está decidido e o que não está.
5. `DATA_MODEL.md` — schemas (parcial).
6. `reference/DESIGN_SYSTEM.md` e `reference/UX_SPECIFICATION.md` — interface (hex e atalhos perdidos; usar o GUIDE §5–6).
7. `reference/IMPLEMENTATION_ROADMAP.md` — os 10 passos da V1.
8. `reference/ATLAS_DE_INTERESSES_DOCUMENTACAO_OFICIAL.md` — baseline do produto.
9. `reference/REQUIREMENTS_TRACEABILITY.md`, `reference/TEST_PLAN.md`, `reference/WORKFLOW_CHECKLIST_V0_V5.md`, `reference/ARCHITECTURE_DECISIONS.md` — rastreabilidade e histórico.
10. `reference/AI_CONTEXT.md`, `reference/README.md`, `reference/OPEN_QUESTIONS.md`, `reference/DATA_MODEL.md` — originais, só para consulta.

## Convenções

- **[PERDIDO]**: informação ausente na origem; não foi inferida.
- Siglas de fonte: `GUIDE` = Cursor Master Guide; `DM` = Data Model original; `OFC` = documentação oficial (§N.M = seção N, item M); `DS` = Design System; `UX` = especificação de UX.
- Resultados "PASS" são **relatos históricos** das fontes, não resultados desta sessão.
