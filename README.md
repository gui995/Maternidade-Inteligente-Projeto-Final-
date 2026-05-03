# Maternidade-Inteligente-Projeto-Final-

# 🤱 Maternidade Inteligente

> Apoio informativo com IA para mães na fase do puerpério e primeiros meses do bebê.

**Trabalho acadêmico** | Protótipo funcional com integração à API Claude (Anthropic)

---

## 📁 Estrutura do Repositório

```
maternidade-inteligente/
├── index.html              # Protótipo principal — abra direto no navegador
├── README.md               # Este guia de navegação
└── docs/
    ├── MEMORIAL.md         # Memorial de construção (como foi feito)
    ├── ECOSSISTEMA.md      # Diagrama e descrição do ecossistema
    ├── PROMPTS.md          # Prompts utilizados na construção com IA
    ├── EVIDENCIAS.md       # Evidências da solução proposta
    └── APRESENTACAO.md     # Roteiro das 9 partes da apresentação
```

---

## 🚀 Como Usar o Protótipo

### Opção 1 — Modo Demonstração (sem chave de API)
1. Baixe ou clone o repositório
2. Abra o arquivo `index.html` diretamente no navegador (Chrome, Firefox, Edge)
3. O assistente responderá com respostas pré-definidas sobre os principais tópicos

### Opção 2 — Modo Completo (com chave Anthropic)
1. Obtenha uma chave em [console.anthropic.com](https://console.anthropic.com)
2. Abra o `index.html` no navegador
3. Clique em **"Configurar chave de API"** no chat
4. Insira sua chave (`sk-ant-...`) e salve
5. O assistente passará a usar o modelo Claude em tempo real

> A chave é salva apenas no `localStorage` do seu navegador e nunca é enviada a servidores externos.

---

## 🗂️ O que Cada Seção do Site Faz

| Seção | Descrição |
|---|---|
| **Banner de aviso** | Lembrete permanente: conteúdo educativo, não substitui médico |
| **Tópicos de apoio** | 8 cartões clicáveis com conteúdo expandido em drawer lateral |
| **Assistente de Maternidade** | Chat com IA (Claude) ou modo demo com respostas pré-definidas |
| **Sobre o projeto** | Contexto acadêmico, fontes utilizadas e responsabilidade |
| **Rodapé** | Links de emergência (SAMU 192, CVV 188) |

---

## 📚 Tópicos Cobertos

- 🤱 Amamentação
- 😴 Sono do bebê
- 💛 Puerpério
- 💙 Saúde emocional e depressão pós-parto
- 💉 Vacinação (calendário PNI)
- 🥣 Introdução alimentar e BLW
- 👶 Cólicas e choro
- 🧸 Desenvolvimento 0–12 meses

---

## ⚠️ Fontes e Segurança

O conteúdo é baseado exclusivamente em:
- **SBP** — Sociedade Brasileira de Pediatria
- **OMS** — Organização Mundial da Saúde
- **Ministério da Saúde** — Brasil

O assistente detecta automaticamente palavras de emergência e redireciona para SAMU (192) e CVV (188).

---

## 📄 Documentação Complementar

Consulte a pasta `docs/` para:
- Memorial completo de como o projeto foi construído
- Diagrama do ecossistema tecnológico
- Prompts utilizados
- Evidências da proposta
- Roteiro da apresentação em 9 partes

