---
name: odin-ata
description: Transforma a transcrição ou as anotações de uma reunião (planning, weekly, review, alinhamento com validador, reunião com o cliente do case) numa ata no padrão do núcleo, pronta para o trainee salvar em context/sessions/ e commitar. Use quando o usuário disser "gerar ata", "ata da reunião", "registrar reunião", "processar transcrição" ou "/odin-ata". Versão para o Claude no navegador da skill ata-report do plugin ndados.
---

# Ata de reunião (versão para o navegador)

Adaptação da skill `ata-report` do plugin `ndados` (`core-plugin`). Aqui o Claude não escreve no
repositório: ele gera a ata e quem salva e commita é o trainee.

## Como executar

### 1. Receber a transcrição

O trainee cola a transcrição ou as anotações no chat, ou anexa um arquivo. Se não vier nada,
pergunte: "Pode colar a transcrição ou as suas anotações da reunião?"

### 2. Identificar o tipo de reunião

| Tipo | Foco |
|---|---|
| Reunião com o cliente | Escopo, expectativas, entregáveis, prazo |
| Planning | Tarefas da sprint, responsáveis, prioridades |
| Weekly | Progresso, impedimentos, próximos passos |
| Review | O que foi entregue e o que o cliente achou |
| Alinhamento com validador | Status, bloqueios, direcionamento |
| Interna da equipe | Decisões e divisão de tarefas |

### 3. Extrair

Participantes (com papel), objetivo, pontos discutidos em ordem, decisões (com quem decidiu),
ações (com responsável e prazo; sem responsável, `[A DEFINIR]`), informações úteis e dúvidas
abertas. Transcrição automática erra nomes: corrija o óbvio e marque a incerteza com `[?]`.

### 4. Gerar o arquivo

Arquivo para download `AAAA-MM-DD-ata-<tipo>.md`:

```markdown
# Ata — <Tipo> — DD/MM/AAAA

**Participantes:**
- <Nome> — <papel>

**Objetivo:** <uma frase>

## Pontos discutidos
1. <tópico>

## Decisões
| Decisão | Quem decidiu | Contexto |
|---|---|---|

## Ações
| Ação | Responsável | Prazo |
|---|---|---|

## Informações relevantes
- <fato ou restrição>

## Pendências e dúvidas
- [ ] <item a confirmar>
```

### 5. Fechar

Diga quantas decisões e quantas ações saíram, e destaque as ações `[A DEFINIR]`: ação sem dono
costuma não acontecer. Depois, mostre os passos para salvar em `context/sessions/` e commitar,
como na skill `odin-sessao`.

## Regras

- Fiel ao que foi dito; na dúvida, registre a dúvida.
- Nunca ponha na ata senha, token ou dado pessoal de cliente.
