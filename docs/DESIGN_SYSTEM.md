# DESIGN SYSTEM — ATLAS DE INTERESSES
**Fonte Oficial de Referência:** *Design System - Atlas de Interesses.pdf*  
**Versão:** 1.0 (Consolidada V0.6)  
**Status:** Norma técnica de interface para desenvolvimento no Cursor.

---

## 1. TOKENS DE CORES E PALETA SEMÂNTICA

### 1.1 Mapeamento de Tokens Semânticos (Light & Dark Mode)
* ****: Fundo principal da aplicação ( | ).
* ****: Cards, modais, painéis laterais e contêineres de destaque ( | ).
* ****: Texto primário, títulos principais e corpo do leitor/editor Markdown ( | ).
* ****: Texto secundário, rótulos de metadados, datas ISO-8601, atalhos de teclado ( | ).
* ****: Cor primária de marca, botões de ação principal e destaques ( | ).
* ****: Estado de foco/hover da cor primária ( | ).
* ****: Cor de texto e ícones sobre fundo primário ().
* ****: Divisores estruturais, contornos de cartões e inputs ( | ).
* ****: Erros de I/O em disco, alertas críticos e ações destrutivas ( | ).

### 1.2 Cores Dinâmicas de Entidades
* As propriedades  e  continuam sendo armazenadas em hexadecimal no YAML Frontmatter (ex.: ) e renderizadas dinamente em badges e bordas.

---

## 2. ESCALA TIPOGRÁFICA (FAMÍLIA INTER / SYSTEM SANS-SERIF)

* ****: Bold (700) | **48px / 56px** (Line-height: 1.16) — Boas-vindas e introdução.
* ****: Bold (700) | **30px / 38px** (Line-height: 1.26) — Título do **Hub Centralizado "ATLAS DE INTERESSES"** e cabeçalhos de tela.
* ****: Semi Bold (600) | **22px / 30px** (Line-height: 1.36) — Títulos de seções, nomes de Grupos e Projetos.
* ****: Semi Bold (600) | **17px / 24px** (Line-height: 1.41) — Subseções e cabeçalhos de formulários.
* ****: Regular (400) | **18px / 28px** (Line-height: 1.55) — Resumos de destaque.
* ****: Regular (400) | **15px / 22px** (Line-height: 1.46) — **Corpo do Editor Markdown**, descrições de tarefas e campos de formulário.
* ****: Regular (400) | **13px / 18px** (Line-height: 1.38) — Texto secundário, metadados e timestamps ISO-8601.
* ****: Medium (500) | **14px / 20px** (Line-height: 1.42) — Rótulos de botões, badges de status (, ) e Tags.
* ****: Medium (500) | **12px / 16px** (Line-height: 1.33) — Rótulos pequenos, atalhos de teclado () e badges secundários.
* *Frase de Amostra Oficial:* **"Ridgeline at first light"**

---

## 3. GEOMETRIA, CANTO ARREDONDADO E ESPAÇAMENTO

* **Corner Radius (Arredondamento)**:
  *  (**6px**): Badges, tags, inputs e botões S/M.
  *  (**12px**): Cards de grupos, painéis laterais e modais.
  *  (**24px**): **Caixa do Hub Centralizado "ATLAS DE INTERESSES" (Tela 1)**.
* **Grade de Espaçamento (Base 8px)**:
  *  (**8px**): Gaps internos pequenos.
  *  (**16px**): Padding interno padrão de cards e formulários.
  *  (**24px**): Gaps entre cartões e seções.
  *  (**40px**): Margens externas de tela e afastamento no Hub Centralizado.

---

## 4. INSTRUÇÕES PARA O CURSOR
1. O agente de código deve consultar este documento antes de criar qualquer componente gráfico em React/Tailwind.
2. É proibido inventar cores genéricas ou substituir a escala tipográfica aprovada.
3. O Hub Centralizado "ATLAS DE INTERESSES" na Tela 1 DEVE usar  (24px) e  (40px) de afastamento. Proibido transformar o Hub em barra lateral fixa à esquerda.

---

## 5. QUESTÕES VISUAIS EM ABERTO
1. Confirmação do mapeamento hexadecimal primitivo CSS/Tailwind.
2. Adoção da biblioteca **Lucide React** para os ícones do sistema e .
3. Alternância automática de tema baseada em .
