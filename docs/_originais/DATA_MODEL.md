# ESPECIFICAÇÃO DE MODELO DE DADOS E SCHEMAS — ATLAS DE INTERESSES (V1)
**Versão:** 2.0 (Consolidada V0.2 / V0.6)  
**Padrão de ID:** UUID v4 (36 caracteres)  
**Formato do Arquivo:** YAML Frontmatter + Markdown Body  

---

## 1. Regras Gerais de Armazenamento
1. **Chaves Primárias**: UUID v4 único e imutável.
2. **Caminhos no Vault**:
   - 
   - 
   - 
   - 
   - 
   - 
   - 
   - 
   -  (Manifesto de Transação Temporário)

---

## 2. Entidades
* **Group**: uid=1000(sandbox) gid=1000(sandbox) groups=1000(sandbox), , ,  (Hex), ,  (UUIDs).
* **Tag**: uid=1000(sandbox) gid=1000(sandbox) groups=1000(sandbox), , ,  (Hex),  (Array de strings).
* **Item**: uid=1000(sandbox) gid=1000(sandbox) groups=1000(sandbox),  (|||||), , , , , , .
* **Task**: uid=1000(sandbox) gid=1000(sandbox) groups=1000(sandbox), ,  (|||), , , , .
* **Note**: uid=1000(sandbox) gid=1000(sandbox) groups=1000(sandbox), ,  (||),  (: obrigatório, : opcional, : estritamente ), , .
* **InboxCapture**: uid=1000(sandbox) gid=1000(sandbox) groups=1000(sandbox), ,  (|), , .
