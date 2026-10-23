---
name: odin-sessao
description: Fecha uma sessão de trabalho num projeto do ODIN e gera o resumo no padrão do núcleo, pronto para o trainee salvar em context/sessions/ e commitar. Use quando o usuário disser "resumo da sessão", "fechar sessão", "registrar sessão", "o que fizemos hoje" ou "/odin-sessao". Versão para o Claude no navegador da skill session-summary do plugin ndados.
---

# Resumo de sessão (versão para o navegador)

Adaptação da skill `session-summary` do plugin `ndados` (`core-plugin`). A original grava direto
em `context/` porque o Claude Code enxerga a pasta do projeto. Aqui o Claude não escreve no
repositório: ele gera o arquivo e quem salva e commita é o trainee.

## Como executar

### 1. Ler o contexto do projeto

Se o repositório da equipe estiver conectado ao Projeto, leia o `CLAUDE.md` e o
`context/README.md`, e o último arquivo de `context/sessions/`, se houver. Isso evita repetir
pendência que já foi registrada. Se não houver repositório conectado, siga só com a conversa.

### 2. Sintetizar a sessão

A partir da conversa, identifique:

- **Feito:** entregas concretas. Não "trabalhamos na extração", e sim "extração da página de
  produtos da Farmácia X, 1.240 itens, salvos em `data/raw/`".
- **Decisões:** escolhas que fecham uma opção e seriam caras de desfazer, com o porquê.
- **Pendências:** o que começou e não terminou, com contexto para retomar sem reler a conversa.
- **Bloqueios:** o que depende de outra pessoa. Omita a seção se não houver.
- **Próxima sessão:** em ordem de prioridade; a primeira linha tem que ser algo que dá para
  começar na hora.

Se algo não ficou claro na conversa, pergunte ao trainee em vez de inventar.

### 3. Gerar o arquivo

Crie um arquivo para download chamado `AAAA-MM-DD.md` (data de hoje; se já houver sessão no dia,
`AAAA-MM-DD-2.md`), com este modelo:

```markdown
# Sessão — AAAA-MM-DD

**Duração:** ~Xh
**Quem:** <nome do trainee>

## Feito
- <item concreto>

## Decisões
| Decisão | Por quê |
|---|---|
| <decisão> | <motivo> |

## Pendências
- [ ] <item com contexto para retomar>

## Bloqueios
- <se houver>

## Próxima sessão
1. <primeira ação, começa na hora>
2. <segunda>
```

Até 30 linhas. Se passar disso, está detalhado demais.

### 4. Dizer ao trainee o que fazer com ele

Termine com estes passos, no Windows:

```powershell
# na pasta do repositório da equipe
mkdir context\sessions -Force
# mova o arquivo baixado para context\sessions\
git switch -c sessao/AAAA-MM-DD
git add context/sessions/AAAA-MM-DD.md
git commit -m "sessão AAAA-MM-DD"
git push -u origin sessao/AAAA-MM-DD
```

E lembre: o PR vai para o validador da equipe, e a sessão nova no Claude começa pelo item 1 da
"Próxima sessão".

## Regras

- Nunca ponha no resumo senha, token, chave de API ou dado pessoal.
- Fiel ao que aconteceu: na dúvida, registre a dúvida, não a suposição.
