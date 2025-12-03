## ESCOMBROS.LOG

> Repositório *front-end* oficial do [Escombros Lab](https://github.com/escombros-lab).
> Atua como o agregador estático e ponto de acesso público para as investigações sociotécnicas do laboratório.

## :: ARQUITETURA DO SISTEMA

O portal foi construído sob uma filosofia de **minimalismo digital e independência**. Não utilizamos frameworks pesados (React, Vue, Bootstrap) para garantir performance, longevidade do código e facilidade de auditoria.

### Tech Stack
*   **Core:** HTML5 Semântico.
*   **Styling:** CSS3 nativo (CSS Variables, Flexbox/Grid). Design system proprietário focado em estética "Terminal/Forensics".
*   **Logic:** Vanilla JavaScript (ES6+).
*   **Data Source:** JSON (`fetch` API).

---

## :: ESTRUTURA DE DADOS

O site opera como uma *Single Page Application* (SPA) simplificada. O conteúdo das seções de auditoria não é *hardcoded* no HTML, mas renderizado dinamicamente.

### `data/projects.json`
Este arquivo atua como o "banco de dados" do site. Ele controla o que é exibido nas seções:

1.  **01_AUDITS/**: Lista de investigações ativas/arquivadas.
2.  **02_EVIDENCE_LOCKER/**: Arquivos e logs exibidos no terminal simulado.

**Exemplo de estrutura:**
```json
{
  "investigations": [
    {
      "id": "CASE_001",
      "title": "TITLE_HERE",
      "status": { "text": "PUBLISHED", "class": "status-finished" },
      "links": [{ "text": "READ_REPORT", "url": "..." }]
    }
  ]
}
```

---

## :: PROTOCOLOS DE DESENVOLVIMENTO (Local Dev)

Como o sistema utiliza requisições assíncronas (`fetch`) para ler o arquivo JSON, **o site não funcionará corretamente se aberto diretamente pelo sistema de arquivos** (`file://index.html`) devido a políticas de segurança de navegadores (CORS).

Para rodar localmente:

1.  **Clone o repositório:**
    ```bash
    git clone https://github.com/escombros-lab/escombros-lab.github.io.git
    cd escombros-lab.github.io
    ```

2.  **Inicie um servidor local:**
    *   Com Python 3 (Recomendado):
        ```bash
        python3 -m http.server 8000
        ```
    *   Com Node.js:
        ```bash
        npx serve
        ```

3.  **Acesse:** `http://localhost:8000`

---

## :: DEPLOY & HOSPEDAGEM

*   **Infraestrutura:** GitHub Pages.
*   **Branch:** `main` (Raiz).
*   **DNS:** https://escombros-lab.github.io

Qualquer *push* na branch `main` dispara automaticamente a build do GitHub Pages. O cache pode levar até 60 segundos para atualizar.

---

## :: LICENÇA

Este repositório segue a política de duplo licenciamento do Escombros Lab:

*   **CÓDIGO (HTML/CSS/JS):** [MIT License](LICENSE).
*   **CONTEÚDO/TEXTOS:** [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

---
*2025 © Escombros Lab. Independent Research Unit.*
