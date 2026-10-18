# ATLAS DE INTERESSES — DOCUMENTAÇÃO OFICIAL DO PRODUTO
**Versão do Documento:** 8.0 (Baseline do Produto com Design System Integrado)  
**Data:** 17 de outubro de 2026  
**Status:** Baseline oficial consolidada. Núcleo de dados e algoritmos da PoC V0.4 formalmente aprovados com escopo delimitado. Handoff V0.6 e Design System integrados.

---

### 1. DECISÃO OFICIAL DA PROPRIETÁRIA DO PROJETO (GATE V0.4 e V0.6)
* **Aprovação do Núcleo de Dados**: Aprovado o núcleo de dados e persistência da PoC V0.4 com base nos testes em disco (operações Markdown/YAML, UUID v4 imutável, associação dinâmica por tags via Regra OR, resolução de aliases pós-restart, preservação byte a byte no round-trip D-006, backup ZIP com SHA-256 e recuperação da Inbox).
* **Consolidação do Handoff e Design System (V0.6)**: Repositório organizado para o Cursor, integrando o  e o . Proibida a implementação da V1 sem autorização prévia explícita.
* **Stack Principal**: **Tauri 2 + React + TypeScript** mantida como candidata principal.

---

### 2. PRINCÍPIOS E INVARIANTES DO PRODUTO
1. **Markdown é a Fonte de Verdade**: Registros em arquivos  e  no vault local.
2. **Identificador Estável UUID v4**: Imutável perante renomeações ou movimentações.
3. **Regra OR de Grupos**: Pertinência calculada por .
4. **Navegação Hub Centralizada**: A caixa "ATLAS DE INTERESSES" permanece centralizada na Tela 1 (). Proibida barra lateral fixa à esquerda.
5. **Design System Oficial**: Interface implementada segundo  (Tipografia Inter, paleta semântica Light/Dark e grade base 8px).
6. **Preservação Byte a Byte (D-006)**: Alterar metadados no Frontmatter mantém o corpo Markdown 100% idêntico.
