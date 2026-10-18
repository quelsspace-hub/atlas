# Questões em Aberto, Conflitos e Lacunas

> Nenhum item abaixo foi resolvido. Cada um indica o que as fontes dizem e o que precisa ser decidido ou fornecido pela responsável pelo projeto.

## A. Questões originais preservadas

Fonte: `OPEN_QUESTIONS.md` original (v2.0) e `DESIGN_SYSTEM.md` §5. Os termos técnicos entre crases foram perdidos na origem.

**Nativas GUI / Rust (validar na V1)**
1. Interceptação do evento nativo de fechamento (o GUIDE indica `tauri://close-requested`).
2. Permissões de escopo de arquivo do plugin de FS (o GUIDE indica `@tauri-apps/plugin-fs`).
3. Medições reais de tamanho do executável compilado e de RAM.

**Visuais (aprovação formal)**
4. Mapeamento hexadecimal primitivo CSS/Tailwind.
5. Adoção da biblioteca Lucide React para ícones.
6. Alternância de tema via configuração do SO (termo técnico exato perdido).

## B. Conflitos e inconsistências encontrados

| ID | Gravidade | Descrição | O que precisa ser decidido |
| :--- | :--- | :--- | :--- |
| OQ-001 | **Alta** | `DATA_MODEL.md` original está corrompido: campos, caminhos e enums foram substituídos por vazio e por saída do comando `id` (`uid=1000(sandbox)...`), repetida em todas as seis entidades. Causa provável (hipótese, não confirmada): crases interpretadas pelo shell ao gerar o arquivo via heredoc sem aspas. | Fornecer o `DATA_MODEL.md` íntegro ou a versão anterior (v1/V0.2). Sem isso, o schema YAML não pode ser implementado. |
| OQ-002 | **Alta** | Os demais arquivos (exceto o GUIDE) perderam todo texto entre crases: nomes de arquivos referenciados em AGENTS/README, tokens de cor e valores hex em DS, atalhos e nomes de tela em UX, IDs de teste em TEST_PLAN, fontes canônicas em REQUIREMENTS_TRACEABILITY. Exemplo: AGENTS §1 diz "Ler  e  antes de começar" sem nomear os arquivos. | Fornecer versões íntegras. Enquanto isso, só o GUIDE serve de fonte para nomes de tokens e arquivos. |
| OQ-003 | **Alta** | Resultado da PoC: README original diz "13/13 testes aprovados" e o GUIDE repete "PoC 13/13 PASS"; já o TEST_PLAN diz 11 testes de núcleo aprovados (Node/disco) e **2 com "Lógica Aprovada / IPC Nativa Pendente"**. | Esclarecer se os 2 testes nativos contam como aprovados. Até lá, tratar como 11 aprovados em disco + 2 parciais, e nenhum reexecutado. |
| OQ-004 | Média | Numeração: o cabeçalho de ADR diz "ADR-001 a ADR-008", mas faltam ADR-003, 006 e 007. Na série D-xxx falta D-002. A relação entre D-xxx e ADR-xxx só é explícita para ADR-004 = D-006. | Fornecer os registros ausentes ou confirmar que não existem; confirmar o mapeamento D ↔ ADR. |
| OQ-005 | Média | O GUIDE §5 lista valores hex (ex.: `#2563EB`, `#0F172A`), mas "mapeamento hexadecimal primitivo CSS/Tailwind" consta como pendente de aprovação formal (item A.4). Os hex do `DESIGN_SYSTEM.md` foram perdidos. | Confirmar se os hex do GUIDE são os aprovados ou provisórios. Não usá-los como definitivos até lá. |
| OQ-006 | **Alta** | Fontes referenciadas e **não fornecidas**: código da PoC (`poc/vault_core.js`), a suíte de testes, os dados fictícios de demonstração e o PDF *Design System - Atlas de Interesses.pdf* (fonte oficial do DS). | Fornecer os artefatos, ou confirmar que estão em outro local. Sem eles, nada da PoC pode ser reverificado. |
| OQ-007 | Média | Conflito de caminho: o GUIDE manda manter `docs/IMPLEMENTATION_STATUS.md`, mas esta tarefa determina `docs/recovered/`. Além disso, as fontes citam `docs/...`, enquanto os arquivos fornecidos estão sem hierarquia. | Decidir onde ficará o registro de status oficial e como promover `docs/recovered/` a `docs/`. Os originais não foram movidos. |
| OQ-008 | Baixa | Estrutura do GUIDE: a seção "Registro contínuo de implementação" está sem numeração entre §8 e "# 9. Regras de atualização", com nível de título diferente. | Confirmar se §9 pertence àquela seção. Tratado aqui como seção única. |
| OQ-009 | Baixa | O GUIDE contém escapes de exportação (`\_`, `\*`, `\[`, `\---`), inclusive dentro de crases (ex.: `.txn\_{capture\_id}.json`). | Confirmar que os nomes reais não têm barra invertida (assumidos sem, mas não confirmado). |
| OQ-010 | Média | Regra de validação da nota `reading` não confirmada. O GUIDE só define `work` (exige item) e `permanent` (força `null`). A linha de Note em DM tem "obrigatório, opcional, estritamente ..." com rótulos perdidos. | Confirmar a regra de `context_item_id` para `reading`. Não foi deduzida. |
| OQ-011 | Baixa | Ordem das telas ≠ ordem dos atalhos: Tela 2 = `Alt+3`, Tela 4 = `Alt+2`. Tela 3 não tem atalho (navegação direta). Atalhos em UX e DS foram perdidos; só o GUIDE os lista. | Confirmar se o mapeamento é intencional. |
| OQ-012 | Baixa | DS §3 usa "painéis laterais" para `Surface raised` e `Radius/M`, enquanto a barra lateral fixa à esquerda é proibida. Interpretado como painéis contextuais, mas não está explícito. | Esclarecer o que são "painéis laterais" permitidos. |
| OQ-013 | Média | "Gate V0.4 Aprovado com Escopo Delimitado": o escopo exato não está detalhado. REQ-010 e REQ-011 estão como PASS por "Gate V0.2" e "Handoff V0.6", isto é, aprovação documental, não teste. | Definir o que está dentro e fora do escopo aprovado. |
| OQ-014 | Média | Nenhum arquivo se declara original ou reconstrução. Pelas evidências, a corrupção parece ter origem em geração automática por shell, mas isso é hipótese. | Informar quais arquivos são os originais autoritativos. |

## C. Informações que não puderam ser confirmadas

- Nomes completos dos campos de Group, Tag, Item, Task, Note e InboxCapture (além dos citados no GUIDE).
- Valores de enum: status de Task (4 valores, só `canceled` legível) e enum de InboxCapture (2 valores).
- Caminhos do vault (oito dos nove itens vazios).
- Definição exata de tarefa elegível para o progresso.
- IDs e nomes dos 13 testes da PoC; TC-008 e TC-013 são citados na matriz, mas sem descrição.
- Tokens de cor e valores hex dos modos Light/Dark, além dos citados no GUIDE.
