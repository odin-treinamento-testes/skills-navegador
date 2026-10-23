---
name: odin-plano
description: Antes de escrever código ou fazer uma entrega num projeto do ODIN, monta o plano do jeito do orquestrador do núcleo (entender, planejar, pedir o ok, executar, conferir) e só segue depois que o trainee aprovar. Use quando o trainee pedir uma tarefa de projeto ("faz a extração", "monta o pipeline", "cria o chatbot"), disser "planeja", "qual o plano" ou "/odin-plano". Versão para o Claude no navegador do fluxo do orquestrador do plugin ndados.
---

# Plano antes do código (versão para o navegador)

No Claude Code, o orquestrador do plugin `ndados` entende o pedido, monta um plano, pede o ok e só
então delega. No navegador não há orquestrador nem agentes, mas o método é o mesmo: plano
primeiro, código depois, e o trainee decide.

## Como executar

### 1. Entender

Leia o `CLAUDE.md` e o `context/` do repositório da equipe, se estiverem conectados ao Projeto.
Depois confirme com o trainee, em poucas linhas:

- **Objetivo:** o que fica pronto no fim desta tarefa.
- **Contexto:** em que etapa do case ela entra e o que já existe.
- **Critério de aceite:** como o validador vai saber que está certo.
- **O que não mexer:** arquivos, partes do escopo ou decisões já tomadas.

Faltou algum dos quatro? Pergunte antes de planejar.

### 2. Planejar

Devolva um plano numerado e curto (3 a 7 passos). Cada passo diz o que será feito, em que arquivo,
e como conferir que deu certo. Aponte riscos (site que bloqueia scraping, custo de nuvem, dado
sensível) e o que fica fora.

### 3. Pedir o ok

Termine com: "Posso seguir com este plano?" e **pare**. Não escreva código nesta resposta.

### 4. Executar em partes

Com o ok, faça um passo por vez e explique o que cada trecho faz. O trainee é quem roda o
código e o git na máquina dele. Se ele pedir para mudar o plano, ajuste o plano primeiro.

### 5. Conferir

No fim, volte ao critério de aceite e diga o que foi cumprido e o que não foi. Sugira fechar com
a skill `odin-sessao`.

## Regras

- Treinamento é para aprender: explique o porquê das escolhas, não só entregue o código.
- Nunca peça nem aceite senha, token ou chave de API no chat. Credencial fica num `.env`, que não
  vai para o git.
