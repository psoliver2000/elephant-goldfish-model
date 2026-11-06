# Fork: perguntas sempre em formulário

Este repositório é um fork de
[google/elephant-goldfish-model](https://github.com/google/elephant-goldfish-model),
licenciado sob Apache 2.0. Ele não é um produto oficial do Google.

## O que muda

No Claude Code, toda pergunta que uma skill do EGM faz ao usuário vai em um
formulário (`AskUserQuestion`), não em texto livre no chat. A regra fica na
seção "Question delivery" de `docs/claude.md`, que toda skill lê antes de
começar.

Arquivos alterados em 2026-11-02 (Paulo Sousa):

- `docs/claude.md`: nova seção "Question delivery: every question is a form".
- `skills/egm-brainstorm/SKILL.md`: na descoberta, as perguntas abertas passam
  a ser formulários com opções neutras, sem opção recomendada nem ordem que
  favoreça uma. O "Other" do formulário continua aberto para texto livre.
- `skills/egm-review/SKILL.md`: os pedidos de caminho de arquivo e de contexto
  extra viram formulário com os arquivos candidatos encontrados.
- `skills/egm-resolve/SKILL.md`: o gate de resolução e a decisão de cada
  achado viram formulário.
- `skills/egm-brainstorm/test_scenarios.yaml` e `skills/egm-brainstorm/TEST.md`:
  textos dos testes ajustados à regra nova.
- `distributions/claude/`: as cópias desses arquivos, mantidas iguais às
  originais.

Onde o `AskUserQuestion` não existe (por exemplo, uma execução com `-p`), as
skills seguem as instruções originais em texto.

A proteção original do EGM continua: na descoberta, nada de opções que puxem
a resposta para o que o agente já pensa.

## Rótulos de evidência no design

Vêm do método LLM CODE da Netpartners (GUIA §3 e §5). Toda afirmação do
design sobre o sistema atual leva um rótulo: **Confirmed** (com `arquivo:linha`),
**Likely** (com o indício) ou **Not verified** (com o motivo). O que ainda não
existe leva **(proposed)**. O design ganha a tabela **Sources Used**.

Arquivos alterados em 2026-11-06 (Paulo Sousa):

- `skills/egm-draft/SKILL.md`: restrição 14, "Evidence Labels".
- `skills/egm-draft/references/design_doc.md`: legenda dos rótulos e a seção
  "Sources Used".
- `resources/document_standards/feature-spec-standard.md`: "The Evidence
  Rule"; a spec reprova sem rótulos ou sem a tabela de fontes.
- `agents/codebase_details.md`: vetor "Unlabeled or Unsupported Evidence".
  O revisor abre cada `arquivo:linha` citado; citação errada em **Confirmed**
  é blocker.
- `distributions/claude/`: as cópias desses arquivos.

## Instalar no Claude Code

```sh
claude plugin marketplace add <seu-usuario>/elephant-goldfish-model
claude plugin install egm@egm
```

Os comandos continuam `/egm:egm-brainstorm`, `/egm:egm-draft` e
`/egm:egm-review`. Abra uma sessão nova depois de instalar.

## Receber atualizações do Google

Use "Sync fork" no GitHub, ou `git fetch upstream && git merge upstream/main`.
Conflitos só podem aparecer nos arquivos listados acima. Depois de atualizar,
rode `claude plugin marketplace update` e `claude plugin update egm@egm`.
