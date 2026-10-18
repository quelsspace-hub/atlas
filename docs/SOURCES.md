# Origem dos Documentos e Integridade

Todos os arquivos vieram de `/mnt/project/` (somente leitura). Nenhum se declara "original" ou "reconstrução"; a classificação abaixo é **avaliação de integridade** feita pela leitura do conteúdo, não confirmação de autoria (OQ-014).

**Classes**
- **Íntegro**: texto completo e legível.
- **Degradado**: o conteúdo existe, mas o texto entre crases foi perdido (nomes de arquivos, tokens, hex, atalhos, IDs de teste).
- **Corrompido**: contém texto estranho no lugar do conteúdo (saída de shell).

| Arquivo | Bytes | SHA-256 | Classe | Informação não confirmável |
| :--- | ---: | :--- | :--- | :--- |
| `CURSOR_MASTER_GUIDE.md` | 8968 | `76c88b22…00dd8d` | Íntegro (com escapes de exportação) | Escapes `\_` etc. (OQ-009); numeração do fim (OQ-008) |
| `DATA_MODEL.md` | 1061 | `6308666c…d66c46` | **Corrompido** | Todos os campos, enums e caminhos (OQ-001) |
| `DESIGN_SYSTEM.md` | 3510 | `63a1af96…c732f4` | Degradado | Nomes de tokens, hex, nomes de escala tipográfica |
| `UX_SPECIFICATION.md` | 972 | `029ee6bd…f709e4` | Degradado | Atalhos, nomes de tokens |
| `IMPLEMENTATION_ROADMAP.md` | 1084 | `e98e51ff…e365e5` | Degradado | Nomes de arquivos e atalhos (recuperáveis só pelo GUIDE) |
| `ATLAS_DE_INTERESSES_DOCUMENTACAO_OFICIAL.md` | 1718 | `1609e8c6…41d8c3` | Degradado | Fórmula da Regra OR, nomes de documentos citados |
| `REQUIREMENTS_TRACEABILITY.md` | 1019 | `cfb88c78…82073a` | Degradado | Fonte canônica e arquivo de teste de cada REQ |
| `TEST_PLAN.md` | 226 | `03e7e524…3d2241` | Degradado | IDs dos testes (OQ-003) |
| `ARCHITECTURE_DECISIONS.md` | 403 | `7a52ad56…9251cd` | Íntegro, mas incompleto | ADR-003, 006, 007 ausentes (OQ-004) |
| `OPEN_QUESTIONS.md` (original) | 521 | `eacbdef3…f96a0b` | Degradado | Termos técnicos das questões |
| `AGENTS.md` | 330 | `a1beb8dc…a7e733` | Degradado | Nomes dos arquivos da regra 1 e caminho da regra 4 |
| `AI_CONTEXT.md` | 247 | `a6ddb10a…89f5f0` | Degradado | Nome do arquivo do Design System |
| `README.md` (original) | 754 | `2684cb80…5f7072` | Degradado | Nomes das pastas, caminho de abertura no Cursor |
| `WORKFLOW_CHECKLIST_V0_V5.md` | 222 | `0447fd2d…e95342` | Íntegro, mas curto | Detalhes de V0.1–V0.6 |

> Os SHA-256 completos estão nos banners de `reference/*.md`; aqui aparecem os 8 primeiros e os 6 últimos caracteres.

## Fontes citadas e não fornecidas

`poc/vault_core.js`, suíte de testes da PoC, dados fictícios de demonstração, *Design System - Atlas de Interesses.pdf*, pasta `docs/` com hierarquia. Ver OQ-006 e OQ-007.
