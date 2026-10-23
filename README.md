# skills-navegador

Skills do plugin `ndados` adaptadas para o Claude no navegador (claude.ai), para quem não tem
Claude Code, como os trainees. Funcionam no plano gratuito.

| Skill | Imita | Para que serve |
|---|---|---|
| `odin-plano` | o orquestrador | Plano antes do código: entender, planejar, pedir o ok, executar, conferir |
| `odin-sessao` | `session-summary` | Resumo da sessão para salvar em `context/sessions/` |
| `odin-ata` | `ata-report` | Ata de reunião para salvar em `context/sessions/` |

A diferença para as originais: o Claude do navegador não escreve no repositório. A skill gera o
arquivo, e o trainee salva, commita e abre o PR.

## Como instalar (uma vez por conta)

1. No claude.ai, ligue **Configurações → Capacidades → Execução de código e criação de arquivos**.
   Sem isso as skills não aparecem.
2. Baixe os ZIPs de `dist/` deste repositório.
3. Vá em **Customize → Skills → + → Create skill → Upload a skill** e suba um ZIP por vez.
4. Ligue as três.

Fonte: [Use Skills in Claude](https://support.claude.com/en/articles/12512180-use-skills-in-claude).

## Como gerar os ZIPs

Cada ZIP tem a pasta da skill na raiz, com o mesmo nome da skill:

```bash
cd skills && for s in odin-plano odin-sessao odin-ata; do zip -r ../dist/$s.zip $s; done
```

## Manutenção

Quando a skill original mudar no `core-plugin`, a versão daqui é revista no mesmo movimento.
