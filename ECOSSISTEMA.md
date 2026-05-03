# 🌐 Diagrama do Ecossistema — Maternidade Inteligente

## Visão Geral

O Maternidade Inteligente opera como um ecossistema de frontend inteligente: uma aplicação web estática que integra IA generativa via API, sem necessidade de backend próprio.

---

## Diagrama do Ecossistema

```
┌─────────────────────────────────────────────────────────────────────┐
│                        USUÁRIA (Mãe)                                │
│              Acessa pelo navegador (mobile ou desktop)              │
└───────────────────────────────┬─────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────┐
│                    FRONTEND — index.html                            │
│                                                                     │
│  ┌─────────────┐  ┌──────────────────┐  ┌───────────────────────┐  │
│  │   TÓPICOS   │  │  CHAT ASSISTANT  │  │  CONFIGURAÇÃO API     │  │
│  │  (8 cards)  │  │  (interface)     │  │  (localStorage)       │  │
│  │             │  │                  │  │                       │  │
│  │ - Drawer    │  │ - Input textarea │  │ - Chave salva         │  │
│  │   lateral   │  │ - Histórico      │  │   localmente          │  │
│  │ - Conteúdo  │  │ - Typing dots    │  │ - Validação sk-ant-   │  │
│  │   estático  │  │ - Chips rápidos  │  │                       │  │
│  └─────────────┘  └────────┬─────────┘  └───────────────────────┘  │
│                            │                                        │
│  ┌────────────────────────────────────────────────────────────────┐ │
│  │              SISTEMA DE SEGURANÇA (client-side)                │ │
│  │  • Detector de palavras de emergência (SAMU 192, CVV 188)      │ │
│  │  • Banner de aviso permanente (não substitui médico)           │ │
│  │  • Disclaimer em todo resultado do chat                        │ │
│  └────────────────────────────────────────────────────────────────┘ │
└───────────────────────────┬─────────────────────────────────────────┘
                            │  fetch() via HTTPS
                            │  Com chave API            Sem chave API
                            ▼                                │
┌───────────────────────────────────────┐                   ▼
│       ANTHROPIC API                   │    ┌──────────────────────┐
│   api.anthropic.com/v1/messages       │    │   MODO DEMONSTRAÇÃO  │
│                                       │    │   (respostas locais  │
│  Modelo: claude-3-5-sonnet-20241022   │    │   pré-definidas)     │
│  Max tokens: 800                      │    │                      │
│  System prompt: especialista em       │    │  5 temas cobertas:   │
│    maternidade (SBP/OMS/MS)           │    │  amamentação, choro, │
│                                       │    │  tristeza, sono,     │
│  Conversa multi-turno mantida         │    │  puerpério           │
│  em memória local (array)             │    └──────────────────────┘
└───────────────────────────────────────┘

```

---

## Fluxo de Dados — Chat com IA

```
Usuária digita mensagem
         │
         ▼
[Detector de emergência]
   Contém palavra-chave?
     /            \
   SIM            NÃO
    │               │
    ▼               ▼
Resposta de     Há chave API?
emergência        /     \
imediata        SIM      NÃO
(local)          │         │
                 ▼         ▼
           fetch() →    Demo reply
           Anthropic   (local, ~800ms)
           API
                 │
                 ▼
           Resposta Claude
           (max 800 tokens)
                 │
                 ▼
         Renderizado no chat
         + scroll automático
```

---

## Fluxo de Dados — Tópicos de Apoio

```
Usuária clica no cartão
         │
         ▼
JavaScript renderiza conteúdo
do objeto TOPICS[] em memória
         │
         ▼
Drawer lateral abre (CSS transition)
com: seções de texto, alertas ⚠,
notas de fontes (SBP/OMS/MS)
         │
         ▼
Usuária fecha (X, overlay, Esc)
```

---

## Camadas Tecnológicas

| Camada | Tecnologia | Função |
|---|---|---|
| **Estrutura** | HTML5 semântico | Acessibilidade, SEO |
| **Estilo** | CSS3 + variáveis customizadas | Design system coeso |
| **Tipografia** | Google Fonts (DM Serif + DM Sans) | Identidade visual |
| **Lógica** | JavaScript vanilla (ES6+) | Interações, chat, drawer |
| **Persistência** | localStorage | Chave API do usuário |
| **IA** | Claude 3.5 Sonnet (Anthropic) | Respostas personalizadas |
| **Segurança** | Lógica client-side | Detecção de emergência |
| **Hospedagem** | Qualquer servidor estático | GitHub Pages, Netlify etc. |

---

## Integrações Externas

| Serviço | Tipo | Para quê |
|---|---|---|
| **Anthropic API** | REST/HTTPS | Respostas do chat com IA |
| **Google Fonts** | CDN CSS | Tipografia (DM Serif + DM Sans) |
| **SAMU 192** | Link tel: | Emergências médicas |
| **CVV 188** | Link tel: | Apoio emocional/suicídio |

---

## Estimativa de Funcionamento do Ecossistema

- **Carregamento inicial:** ~300ms (HTML local + fonts CDN)
- **Abertura de tópico:** instantânea (dados em memória)
- **Resposta em modo demo:** ~800–1400ms (simulação de delay)
- **Resposta via API Claude:** ~2–5s (dependendo do tráfego da Anthropic)
- **Custo estimado por conversa:** ~US$ 0,002–0,005 (modelo Sonnet, 800 tokens)
- **Infraestrutura necessária:** zero (arquivo estático + API key do usuário)

