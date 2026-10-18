# Status de Implementação — Atlas de Interesses

**Data do registro:** 17 de outubro de 2026
**Natureza:** registro de acompanhamento. Não é fonte de verdade superior ao código, aos testes ou à documentação oficial. Em caso de divergência, registre o conflito; não presuma que este arquivo está correto.

## 1. Estado atual

- Etapa: **organização da documentação** (pré-V1). O roadmap da V1 **não foi iniciado**.
- A V1 está **bloqueada aguardando autorização explícita** (WORKFLOW_CHECKLIST; AGENTS §3).
- Nenhum código de aplicativo foi criado ou alterado nesta etapa.

## 2. Documentado × Implementado × Testado

Legenda: **Documentado** = consta em texto nas fontes. **Implementado** = existe código verificável. **Testado nesta sessão** = executado agora com resultado observado.

| Item | Documentado | Implementado | Testado nesta sessão |
| :--- | :---: | :---: | :---: |
| Núcleo de dados da PoC V0.4 (CRUD, UUID, Regra OR, aliases) | Sim | Não verificável (código não fornecido) | **Não** |
| Preservação byte a byte (D-006) | Sim | Não verificável | **Não** |
| Backup ZIP com SHA-256 (D-007) | Sim | Não verificável | **Não** |
| Recuperação de Inbox (`.txn_*.json`) | Sim | Não verificável | **Não** |
| Progresso com nullability (D-003) | Sim | Não verificável | **Não** |
| Design System (tokens, tipografia, geometria) | Sim (parcial; hex perdidos) | Não | Não |
| 7 telas, Hub centralizado, atalhos | Sim | **Não** | Não |
| Módulos V1 (Steps 1–10) | Sim (roadmap) | **Não** | Não |
| Validação nativa Tauri (close-requested, escopos FS, RAM/executável) | Sim (como pendência) | **Não** | **Não** |

## 3. Resultados historicamente relatados (não reverificados)

Estes são **relatos das fontes**, não resultados desta sessão:

- PoC V0.4: "13/13 aprovados" (README, GUIDE) × "11 aprovados em disco + 2 com IPC nativa pendente" (TEST_PLAN). Ver OQ-003.
- REQ-001 a REQ-011 marcados PASS na matriz; REQ-007 é apenas teste unitário; REQ-010 e REQ-011 são aprovações de gate/handoff.

## 4. Alterações recentes

Somente documentação, em `docs/recovered/` (pasta nova):

- Criados: `README.md`, `DATA_MODEL.md`, `DECISIONS.md`, `OPEN_QUESTIONS.md`, `IMPLEMENTATION_STATUS.md`, `SOURCES.md`.
- Criado `reference/` com 14 cópias literais dos originais, cada uma com banner de proveniência e SHA-256.
- Nenhum arquivo original foi alterado, movido ou excluído.

## 5. Pendente

- Autorização explícita para iniciar a V1 (Step 1 em diante).
- Resolução das questões de `OPEN_QUESTIONS.md`, em especial OQ-001, OQ-002, OQ-003 e OQ-006.
- Fornecimento do código da PoC, dos testes e do PDF do Design System.

## 6. Problemas e riscos

- `DATA_MODEL.md` original corrompido (OQ-001): o schema não pode ser implementado com segurança.
- Perda de texto entre crases em quase todas as fontes (OQ-002).
- Discrepância no resultado da PoC (OQ-003).
- Todas as afirmações de "PASS" são herdadas e não verificáveis aqui.

## 7. Validação realizada nesta sessão

Apenas verificações de arquivo, sem testes de software:

| Verificação | Resultado |
| :--- | :--- |
| Listagem e tamanho dos 14 arquivos em `/mnt/project` | Executada |
| SHA-256 dos 14 originais antes e depois da cópia | Executada (ver `SOURCES.md` e relatório final) |
| Detecção de corrupção (busca por `uid=1000`) | Encontrada em `DATA_MODEL.md` (6 ocorrências) |
| Comparação (diff) corpo das cópias × originais | Executada (ver relatório final) |
| Testes da PoC, builds, testes nativos | **Não executados** |

Geração bem-sucedida dos arquivos **não** equivale a validação da documentação.

## 8. Próximo passo

Aguardar revisão das lacunas e autorização explícita. Com a autorização, o próximo item do roadmap é o **Step 1** (Setup Tauri 2 + React + TypeScript e integração de `poc/vault_core.js`), cuja pré-condição é obter o código da PoC (OQ-006).
