# ✨ Fundo Mágico — Gerador de Backgrounds com IA

> *"Eu entrei na semana sem saber direito onde ia chegar. Saí com um projeto rodando, integrado com IA, e com a certeza de que programar é, de fato, para mim."*

---

## 🚀 Sobre o Projeto

**Fundo Mágico** é uma aplicação web que transforma descrições em linguagem natural e backgrounds animados gerados por inteligência artificial.
O usuário digita o que imagina — um gradiente, uma cena, um estilo — e a IA interpreta e devolve o código HTML e CSS pronto,
aplicando o background diretamente na tela em tempo real.

O projeto foi desenvolvido durante a **Semana do Zero ao Programador Contratado**, uma imersão intensiva de programação Front End que aconteceu 
entre os dias **23 e 29 de Março de 2026**, conduzida pelos gêmeos **Ricardo Dias** e **Roberto Dias**.

---

## 🖼️ Preview

![Preview do Fundo Mágico](./src/imagens/bg.JPG)

> Interface em ação: o usuário descreve o background, a IA processa e o resultado aparece instantaneamente na tela — junto com o código gerado.

---

## 🛠️ Tecnologias Utilizadas

| Camada | Tecnologia |
|---|---|
| Estrutura | HTML5 semântico |
| Estilização | CSS3 (com responsividade) |
| Lógica | JavaScript puro (Vanilla JS) |
| Automação & IA | n8n (workflow com AI Agent) |
| Modelo de linguagem | Google Gemini (via n8n) |
| Fontes | Google Fonts — Roboto + Roboto Mono |

---

## ⚙️ Como Funciona

O fluxo por baixo dos panos é mais interessante do que parece à primeira vista:

1. O usuário descreve o background desejado no campo de texto
2. O JavaScript captura o evento de submit e faz uma requisição **POST** para um webhook no **n8n**
3. O n8n recebe o texto, passa para um **AI Agent** conectado ao **Google Gemini**
4. O Gemini interpreta a descrição e gera código HTML e CSS correspondente
5. Um nó de **Code in JavaScript** dentro do n8n trata e formata a resposta
6. O front-end recebe o JSON com `{ html, css }`, exibe os códigos na tela e injeta o CSS dinamicamente
   no `<head>` do documento — aplicando o background gerado em tempo real

```
[Usuário] → [Formulário HTML] → [Fetch POST] → [Webhook n8n]
                                                      ↓
                                               [AI Agent + Gemini]
                                                      ↓
                                            [Code in JavaScript]
                                                      ↓
                                          [Respond to Webhook]
                                                      ↓
                               [Front-end aplica HTML + CSS dinamicamente]
```

---

## 📁 Estrutura de Arquivos

```
fundo-magico/
│
├── index.html
└── src/
    ├── css/
    │   ├── reset.css        # Zerando margens e paddings padrão
    │   ├── estilos.css      # Estilos principais da interface
    │   └── responsivo.css   # Media queries para mobile
    ├── js/
    │   └── index.js         # Toda a lógica de interação e comunicação com a API
    └── imagens/
        └── bg.JPG           # Background visual da aplicação
```

---

## 💡 Destaques Técnicos

- **Fetch API com async/await** — comunicação assíncrona com o webhook sem bibliotecas externas
- **Injeção dinâmica de CSS** — o estilo gerado pela IA é inserido diretamente no `<head>` via `document.createElement('style')`,
  substituindo o anterior a cada nova geração
- **Loading state** — feedback visual no botão enquanto a requisição está em andamento
- **CSS responsivo** — layout adaptado para dispositivos móveis via media queries
- **Reset CSS** — base consistente de estilos em todos os navegadores
- **Design com glassmorphism** — cards com bordas translúcidas e fundo desfocado

---

## 🤖 Workflow no n8n

O backend da aplicação é 100% serverless, orquestrado pelo **n8n Cloud**. O workflow é composto por quatro nós:

```
Webhook → AI Agent (Gemini) → Code in JavaScript → Respond to Webhook
```

O AI Agent recebe o texto do usuário e tem como instrução gerar exclusivamente um JSON no formato `{ "html": "...", "css": "..." }`, 
que é depois tratado pelo nó de código antes de ser devolvido ao front-end.

---

## 📅 A Semana

Essa semana foi uma experiência que misturou aprendizado técnico com uma energia que é difícil de descrever. Durante 7 dias, do dia 23 ao dia 29 de março,
os gêmeos **Ricardo** e **Roberto Dias** conduziram cada aula com uma didática direta, prática e sem enrolação — do tipo que você aprende fazendo, não só assistindo.

A comunidade no **Discord do evento** foi outro nível. Toda dúvida que surgiu — e surgiram bastante — foi respondida lá, seja por alguém da galera ou pelo próprio suporte. 
Essa troca faz toda a diferença quando você está tentando depurar um erro às 23h.

O projeto **Fundo Mágico** foi o resultado disso tudo: uma semana de código, erros, ajustes, e aquele momento específico em que você vê a IA gerando um background personalizado
na tela do seu projeto pela primeira vez — e percebe que entendeu o que fez.

---

## 📬 Contato

Se quiser trocar uma ideia sobre o projeto ou sobre desenvolvimento, pode me encontrar aqui no GitHub ou nas minhas redes.

° LinkedIn: https://www.linkedin.com/in/breno-leal-b91a26262/
° Github: https://github.com/breno-2020-17-03-2000
° WhatsApp: (89) 98808-8841
---

*Desenvolvido com curiosidade, caffeine e uma semana inteira de imersão. 🚀*
